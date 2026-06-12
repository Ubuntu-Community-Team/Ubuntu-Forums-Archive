---
title: "Can't boot new Toshiba laptop after Ubuntu install - boot-manager won't run also"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by bsnider on 2014-10-19
Hi all, 

I got a brand new Toshiba Satellite C55-B laptop as a gift.  I thought,"I don't want Windows 8, I want Ubuntu 14.04 only."     I learned that the hardware setup program found on the laptop is UEFI.  I got into this using Windows 8.  I changed it to 1) Secure Boot Off, and 2)  Change boot sequence; I made first choice is boot from USB.  Then I made a live USB to install Ubuntu 14.04.    I inserted this in to the Toshiba laptop and installed Ubuntu, not trying to do a dual boot, but I was going for 100% Ubuntu.  Afterward, the computer won't boot at all from the hard disk.  Continues to boot from the Ubuntu thumb drive though.  

Well, now with Windows 8 gone for good, there is no way to access the UEFI setup, isn't that right?  

I read here that the program boot-repair is a best bet to resolve problems such as this.    I tried starting it by entering the commands at the terminal as others have shown, but this did not work.  So I made a live USB for boot-manager and tried to run.  It only started running, but it did not get to the part that fixes my computer.   

Starting the boot-manager live USB, it says at Gnu Grub screen "Boot-repair disk session.  I click on this, then a blue screen saying "Boot-Repair Disk" in center of screen appears. 

Next boot-repair brings up a screen saying:  

* Stopping enable remaining boot-time encrypted block devices
* Starting crash report submission daemon
*Stopping System V runlevel compatibility
*Starting
*Starting
*Stopping
*Starting LightDM Display Manager

Then the screen goes blank with a faint dark blue color.  
The computer hits a blue screen of death.  Good thing, I can turn the laptop off using by holding down the start button for several seconds.  


I want to get my laptop working.   With Windows gone,  I cant get into the UEFI setup program at all can I?   boot-repair might fix my problem, but it won't run.   I don't think I can get Windows back for free!  

Oh dear, what can I do now?   

Thank you very much for your help!!!

---

### Post by ajgreeny on 2014-10-19
You may well be able to access the UEFI setup from Win 8, but I would be very surprised if there is no way to get to it from the point of power-on. I admit I have no idea about Win 8 at all, having only ever seen it in  the shops; I don't know anyone who has it on their machine.

Look carefully as the screen comes to life when you switch on and you'll probably see a message flash up saying "Press F2 or Del to access setup" or something similar.  It is also likely that there is a key-press you can use at power-on to get to a small menu offering the choice of boot devices; on my desktop it's F8.  Look in your laptop manual or download one from Toshiba direct if possible for much more info.

---

### Post by ubfan1 on 2014-10-19
Try typing F2 right after the vendor splash screen at poweron. That should get you into the UEFI settings.  F12 should give you the boot device choices, choose HDD, and you should get another screen offering ubuntu and maybe Windows (which of course won't work).  Try the ubuntu.  If you can run this way, change the default boot to ubuntu with efibootmgr (install the package and read the man pages).

---

### Post by bsnider on 2014-10-19
Thanks friends,  

Well, you saved me.   Silly me,  Of course  you can still access the BIOS setup program without Windows.  With my Toshiba laptop, you need to hold down the F2 button for several seconds while the computer starts to access BIOS.  

The boot-repair program started working after I went to the BIOS setup program, changing Secure Boot to Disabled, and changing the Advanced &#8211; System Configuration &#8211; Boot Mode to CSM.  

When I ran the boot repair program, it suggested I go to the terminal and paste in some instructions.   I was going to do that, but first I will try to reinstall Ubuntu with the Secure Boot Disabled, and Boot Mode as CSM.   Seems like Linux likes CSM.

---

### Post by jonathan57 on 2014-10-20
hey bsnider, i picked up possibly the same laptop today. toshiba satellite c55-b5299 and I'm having issues getting it to boot as well. I had the same goal of getting rid of win8 and having only ubuntu.

I didn't change any boot options before installing. It wouldn't boot from HDD despite fixing boot order at what I think was BIOS menu, I pressed F12 during startup.

I successfully installed and ran boot-repair recommended but there was an issue at the end. Here's the boot-info URL I got:   paste.ubuntu.com/8597540/

I'm gonna go try turning off Secure Boot and if that fails tomorrow I'll try reinstalling after switching boot mode to CSM like you. Best of luck.


EDIT: turning off secure boot and switching to CSM didn't work (with current install.) Maybe I'll try running boot-repair one more time or maybe I'll just try a new install after turning off secure boot and switching to CSM before install.

---

### Post by ubfan1 on 2014-10-20
Bug 1091464 still keeps grub from booting Windows (at least on my Toshiba and probably yours), so turn off secure boot, and the grub boot of windows should work.  No need to avoid UEFI, CSM is not necessary unless no live media boots with UEFI turned on (some few machines).

---

### Post by jonathan57 on 2014-10-20
Success! I turned off secure boot and switched to CSM (IDK if this was necessary) ran a LiveUSB and then ran boot-repair again. Didn't work with CSM so I switched back to UEFI and now everything boots perfectly and ubuntu ran software update without issue. I think the key is simply having secure boot disabled when you installubuntu or run boot-repair.

edit: correct way to do it is turn off secure boot in BIOS, install ubuntu, boot from liveCD/USB, and then run boot repair. I don't think you can get away with not using boot-repair, can you?

---

