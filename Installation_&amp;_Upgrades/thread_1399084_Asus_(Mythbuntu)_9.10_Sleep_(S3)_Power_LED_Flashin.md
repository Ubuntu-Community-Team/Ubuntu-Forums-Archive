---
title: "Asus (Mythbuntu) 9.10 Sleep (S3) Power LED Flashing and looking for clarification"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by rodercot on 2010-02-05
Hey All,

 So I have two systems, both ARe Myth FE's, One is in a Zalman HD135 Chassis with an Mplay systems VFD and Asus P5N7A-VM the other is in an Antec Fusion Black Chassis with the IMON VFD 0038 if I recall. 

 Suspend and Resume work just fine on both machines. They both use custom scripting in /etc/pm/sleep.d as I have lirc performing macro's etc for each system. 

 MY confusion is this. Remember each system uses the same main board. The Antec's VFD is plugged into a USB port on the board and the power is chaned from the power header on the mainboard the Zalman as far as I can tell gets data and power from a USB port on the mainboard.

 So I suspend the Antec Chassis machine and I kill Lirc, LCDd and power off the TV and Bell Sat rcvr, The LCD and the power led GO OFF Completely and turn on just fine when resuming from suspend. 

 On the Zalman Chassis when I suspend the system, it powers off the TV, Denon rcvr and stops LCDd BUT The power button starts flashing every 2 seconds and the VFD just stays lit with a good-bye message on it. 

 So How can kill power to the power led AND I guess kill power to that specific USB(ttyUSB0) port/device on suspend. I have googled till my fingers hurt with no luck. 

 Any Ideas at this point are awesome, NOTE - I know I can unplug the power led. That would be too easy, I want the system to have an led when working. 

 Regards,

 Dave

---

