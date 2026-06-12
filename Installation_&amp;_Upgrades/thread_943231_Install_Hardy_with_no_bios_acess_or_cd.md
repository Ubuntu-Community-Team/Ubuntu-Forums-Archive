---
title: "Install Hardy with no bios acess or cd"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by fatesjoke03 on 2008-10-10
Okay here is my situation. I have spent the past 8 hours trying to figure out what to do.

I have an Acer Aspire 5630, got it from a friend that found it in a house he was tearing down. It had Vista installed, the bios and Vista were both password locked and of course no default passwords worked.

Took me about a week but I was able to figure out how to bypass the hdd boot. Pulled the hdd and booted from a LiveCD of Hardy. So, I can run the live cd of Hardy no problem. However, the install says it is bad and will not install.

I cannot boot with the hdd in so I slide it in after Hardy launches. I have removed the partitions and formatted it to FAT32 via Hardy.I have downloaded Hardy to the newly formatted hdd and installed Gisomount to try and load from there and install. No good, I was not able to run the virtual cd at all. Of course every time I reboot the laptop I am starting from scratch except for the new iso for Hardy.

Not sure what other info I can offer that might help but let me know if there is. I had never used Ubuntu until tonight but I am totally loving it so far, except for the fact I can;t actually do anything worthwhile because it will all be gone when the computer is shut down.

Please help, lol.

---

### Post by fatesjoke03 on 2008-10-10
I have also tried setting the virtual disc drive to autorun but it does not seem to be working. If I click on it it still shows me the disc contents.

Also, I am out of blank cds so I cannot try burning another one. I did create a usb bootdisc but of course I cannot change the boot order because I cannot get into the bios.

---

### Post by hyper_ch on 2008-10-10
why don't you reset the bios?

---

### Post by fatesjoke03 on 2008-10-10
I have been unable to do so.

I have taken the laptop apart but cannot find a CMOS battery.

I am of course open to suggestions on how to get that done though. It is a Phoenix BIOS, none of the typical default passwords work and of course I cannot run an app to retrieve it. I have ran "lshw" in a terminal but that did not show it.

---

### Post by fatesjoke03 on 2008-10-10
Okay, the laptop is completely taken apart right now. Trying to see how to reset the CMOS battery.

---

### Post by hyper_ch on 2008-10-10
download the manual for the motherboard. It will tell you... mostly it's taking the battery out for a while... maybe also setting a jumper...

---

### Post by fatesjoke03 on 2008-10-10
No luck on a manual for the mobo. Here is the model: HBL51LA-3081P-3690

I tried and checked every part of the mobo but could not find anything the resembled a battery, no cylinder(old school) or even a chip that said anything similar to bios or cmos. I have put the laptop back together and it hung up a bit on loading the bios but when I hit F2 it still asked for a password and none of the backdoor ones worked.

I am trying to flash the bios using the newest flash from Acer but I cannot find out how to run an .exe in Hardy. The hdd is not plugged in right now but I am using a usb flash drive to run from. No good. Also, I have the Hardy build on the usb but cannot find how to install from it.

I have tried about a down times to install following these directions: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux) but I run into problems at this command "sudo mount --bind /dev mingw/dev". I keep going afterwords but still no luck.

I tried using Ultimate Boot CD to see if I could get the bios password but no luck, it actually did not even detect the hdd. The hdd is detectable in Ubuntu though. Well, I can partition it at least.

Now on hour 17 of trying to get this to work. Any help would be appreciated.

---

### Post by fatesjoke03 on 2008-10-11
No help out there on this?

I am still working on it. Stopped keeping track of the hours spent. Went and bought a 8G flashdrive to try to run Ubuntu from but no luck since I cannot change the boot order. Tried using brand new discs (bought new ones) to install from but keep getting an error that the discs are bad. 3 different burns of Hardy and they are all no good? WTF

Come on, there has got to be a solution out there..........

---

### Post by jerome1232 on 2008-10-11
There should be a 3 prong jumper on the mobo that when the jumper is moved, will reset the cmos, if the jumper doesn't say cmos near it then you will need the manual to find it.

---

### Post by jerome1232 on 2008-10-11
[http://www.acerpanam.com/synapse/forms/portal20.cfm?website=AcerPanAm.com&siteid=7117&areaid=2&formid=3425&LINKTEXT=Guides%20%26%20Manuals](http://www.acerpanam.com/synapse/forms/portal20.cfm?website=AcerPanAm.com&siteid=7117&areaid=2&formid=3425&LINKTEXT=Guides%20%26%20Manuals)

That's a link to their manuals/guides support section, I don't know what model of laptop you have so can't pull up the actual manual.

---

### Post by fatesjoke03 on 2008-10-11
Thanks jerome but I have tried the manual. It is not a tech manual so does not cover the mobo or CMOS that I saw.

The model is 5630, as noted on my first post, but the User Manual shows absolutely nothing about the mobo. Of course I have not downloaded every manual listed under this model but none of them look like they are technical manuals.

I appreciate the help though. Hopefully someone figures this out for me. It appears I am able to boot from usb after all. It seems it checks usb after hdd, cd-rom and network.

Could that be the key?

---

### Post by fatesjoke03 on 2008-10-25
Okay, got this taken care of. Just a heads up to anyone doing this in the future. I took the hdd and put it in a desktop, created a liveCD and installed from there. I then put the hdd in my laptop and booted. Still having a problem detecting the monitor right but everything seems fine other than that. 5 reboots and no hangups at all and info is saving to the hdd.

---

