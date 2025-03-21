# RT95interface
Interfaces to use the Retevis RT-95 with digital modes (e.g. APRS) 

***Critical (it cost me a radio): the GPIOs on the radio side of the system can only tolerate +- 12ma. Additionally, Retevis is extremely clear in their manual: Do not connect the external speaker or the audio line from the handset to ground or other components directly. Both the TX and RX sides NEED an 8 Ohms audio transformer. Failure to do so WILL result in damages to your radio that cannot be fixed outside of the factory. The Retevis people are very nice and helpful but there's only so much they can do. ***

There is an inherent risk of damaging your radio or computer in this project. I will try to guide you step by step but you are responsible for your own work.
Whatever you do, MAKE SURE that you always have a constant electrical link betweeen your radio GROUND line and that of your PC/Raspberry Pi so that both are at the same potential. 

The first version of this interface uses a DRA-54 "sound card" from Masters Communications (https://www.masterscommunications.com/products/radio-adapter/dra/dra54.html).

This is done to isolate the radio from the driving computer by an additional layer and the DRA-54 also allows you to control the PTT signal from the same USB connection for neatness purposes

Alternatively, it could be bypassed and a USB soundcard such as (https://www.amazon.ca/UGREEN-Universal-Headphone-Microphone-Raspberry/dp/B01N905VOY/ref=sr_1_1_sspa?dib=eyJ2IjoiMSJ9.qknjKnIYm0U-3Xi3oJu1qKmUNisgbQESEJECEBrktkKbnM3dxTu0Jyb0OHCMotfU2SixzOxbG5Qlg4n-4E-q_plg7D3BBlNf4lgepr9LmDc-NauvrPa4AeTgLLQ5tr7aV4VLevqCCHywXhBKCPJzaPc4VQh5V692qGWtspeDas8XWAfQP6-QG8uJL4uy6UJFe6tMGb_s-TddkyrxfMj7NmGPVcjoTV8rc3AJsqxzGFkDb0gd2S4uE2t1eS4F5eX0h4Q9eqziyTx5DNuoDsJow-clAawXJmCkcuUZ5JVgO4g.8QuevpvKqUcIn8JXpePtfcXX2ata7ClIxgrniRU1XCc&dib_tag=se&hvadid=671287084767&hvdev=c&hvlocphy=9000662&hvnetw=g&hvqmt=e&hvrand=8937630120474496837&hvtargid=kwd-296167516060&hydadcr=1500_13637778&keywords=usb+sound+card&mcid=1ff72d0b73cc318eaa13d1abf55de88e&qid=1742566663&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1) could be used with a Raspberry Pi.

If using a Raspbery pi and soundcard, you will have to build a transistor setup for the PTT signal where the collector is held at 5v and connected to the PTT line, the base is triggered by the Pi's PTT signal and the emitter goes to ground. Limit the current going to the RT-95 with a 16k Ohms resistor as in the included KiCad file. 
This should result in a 5v/0.5ma signal when PTT is off and of a connecction to ground or 0v when PTT is being clicked in.

Sample Direwolf configuration files are also included for Raspberry.pi (ensure that you choose the one for the DRA-54 adapter or direct to the rt-95 from the pi).

The Serial signal line is currently left unconnected but future work will explore the possibility of managing the radio (volume adjustments, channel selection, etc.) from the software using that line. 
