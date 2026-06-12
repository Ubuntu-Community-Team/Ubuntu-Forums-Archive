---
title: "Why ubuntu/mint won't install on my system?"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by Argo_Nunya on 2014-03-17
This is fifth week this problem has been tormenting me, three of which the computer was in a shop being checked for hardware problems (no hardware problems. All parts work fine and correctly.) and they tried this there too but couldnt figure out what is the problem.  All began five weeks ago when I decided to install linux mint over my windows 7 install because I wanted to go back to linux world and mint is stable, easy to use and I have past expirience with. Also, according to my last expirience with it, it is simple to install. Not so this time. I boot linux mint 16 64-bit cinnamon and it crashes to this: [http://feb.imghost.us/FSxM.jpg](http://feb.imghost.us/FSxM.jpg)  

At this point cd stopped spinning, pressing the reset button on computer did nothing, only by shutting it manually down worked. I googled to see what might be a problem and then rebooted linux mint in compatibilty mode which promptly began to vomit lines of text which I didnt understand and crashed at this point [http://feb.imghost.us/FT0H.jpg](http://feb.imghost.us/FT0H.jpg)  

This time google was no help so I asked in linux mint forums and were told to take safeboot off and make my hard drive into legacy mode via bios. Same problem, crashes at same point. Then I was told to remove win7 because some clash of some sorts. I was stupid and did it. And it still crashes at the same point when trying to install mint, only this time I couldnt even boot to win7. Well, time to try install win7 then cause I had it installed so it should work, right? Nope, the win7 install crashes at 0% everytime. Well, then I try to install newest ubuntu because this is strange. Saddly, it crashes at same point.  After this several people agreed with me that it seems like hardware problem based on the error screen and how the cd stops spinning etc so I sent the computer to shop. It comes back and they told me that cd drive was broken and they installed another one. They had managed to install win7 to it somehow. When I powered the machine up, it tried loading win7 up, then crashed and restarted. I tried everything I could to no avail. 

Back to shop.  This time they say that they checked every piece of hardware and everything is in working order and none of them is broken. What. They tell me also that they got ubuntu installed on it. What what. When I take it home I notice its old version of ubuntu because it has gnome 2 and in update menu it asks to update to newest version 12.04, the one I tried installing but it crashed.  Well, of course I try to update to it to newest version so it has full support. Everything seems to be going fine, packages are downloaded, installing is going fine but when it has 1 minute left (of hour long operation) and says: Setting up udisks (1.0.4-5ubuntu2.2)...  It crashed. Reset wont work. I hard shutdown it and restart. Ubuntu wont start. Why?!?!?! Why the hell this has to be this difficult?!  Google hasnt help me at all with this so I hope someone at some forum has any idea what the heck is going on with this. Heres my specs:  RAM 8.00GB Dual-Channel DDR3 @ 798MHz (11-11-11-28)  Motherboard ASRock B75 Pro3-M (CPUSocket)  Graphics VE247 (1920x1080@60Hz) 3072MB ATI AMD Radeon HD 7900 Series (Gigabyte)  Storage 931GB Seagate ST1000DM003-1CH162 ATA Device (SATA)  Optical Drives ASUS DRW-24B5ST ATA Device HUAWEI Mass Storage USB Device  . . .Why this totally destroyed my formatting?! Okay, I cant figure out how to restore the formatting.

---

### Post by slooksterpsv on 2014-03-17
Specs - 
RAM 8.00GB Dual-Channel DDR3 @ 798MHz (11-11-11-28) 
Motherboard ASRock B75 Pro3-M (CPUSocket) 
Graphics VE247 (1920x1080@60Hz) 3072MB ATI AMD Radeon HD 7900 Series (Gigabyte) 
Storage 931GB Seagate ST1000DM003-1CH162 ATA Device (SATA) 
Optical Drives ASUS DRW-24B5ST ATA Device HUAWEI Mass Storage USB Device

Phew, yeah the formatting is terrible. So you've taken the PC to a shop numerous times to see if it was a hardware issue it wasn't.

When you say it "crashed" what do you mean? How does it crash, what does it do or say? - Even with Windows 7 crashing, if being installed from a DVD,  if it's an issue with the CDROM drive, the CDROM drive could be junk.

The second picture you posted is an issue with the CDROM or Drive itself. Can you use Unetbootin to make a bootable USB drive of Ubuntu?

Do you know how your disk drive is setup in BIOS if it's set to IDE or AHCI?

---

### Post by Argo_Nunya on 2014-03-17
The cd rom drive has been replaced with brand new one. When it crashes it gets stuck to the screen, mouse wont work, keyboard wont work, cd drive stops spinning, the computer is basically dead aside from screen showing either that error message, that white little square or in todays updates case the update message.    I cannot do usb drive now.    I have and it has been tried by at the shop in both ide and achi and either safeboot on or off. No difference.

---

