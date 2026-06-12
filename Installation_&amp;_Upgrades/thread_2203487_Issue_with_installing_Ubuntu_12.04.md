---
title: "Issue with installing Ubuntu 12.04"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by douglas-shuler91 on 2014-02-03
Hi, new here, almost completely new. I tried ubuntu via the live cd windows installer. I like what I see and I'd love to use it further, but when I try to use the cd as a boot disk, I go through the whole installation, and it tells me to restart the computer, and remove the media, press enter, and restart. The problem is, it goes straight to windows eight. I've tried this now on the same drive as my windows installation (partitioning the drive 500GB for windows 500GB for linux) But it doesnt show up at all. Not even in my bios. When I did it using the windows installer, I could chose which one I wanted to boot into. Now it's like it doesn't even exist. I've tried uninstalling and reinstalling three times now. Both using install alongside windows, I even tried installing it on a completely seperate hard drive, which then lead to my bios boot menu no longer even detecting said hard drive. Hoping I can find some help here :( kind of lost.

---

### Post by LukasLeon on 2014-02-03
Try this:
1. Insert the LiveCD to your drive again, in installation click on Try Ubuntu, which will load it from the LiveCD
2. When it loads, open up terminal and type in following commands one after each other:

sudo add-apt-repository ppa:yannubuntu/boot-repair  
sudo apt-get update  
sudo apt-get install -y boot-repair

This will actually install a program called Boot-repair.

3. Open the Boot-repair by typing sudo boot-repair into the terminal
4. Boot-repair should open, choose the Recommended repair option and wait until it is done
5. Remove CD from the drive and reboot your PC, you should now see the option to choose between Win and Ubuntu..

Hope this helps

---

### Post by oldfred on 2014-02-03
Not sure where you are at now.
Was Windows 8 pre-installed so you have UEFI and gpt partitioning?
Or did you install it yourself in BIOS boot mode with MBR partitioning?

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by westie457 on 2014-02-03
Have you ever checked the Power options in Windows 8 to check if 'Fastboot' is enabled. If it is enabled this is the reason you go straight to windows when you start your computer.

See here for info. [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Also disable all forms of hibernation/sleep. [http://www.techrepublic.com/blog/tr-dojo/delete-hiberfilsys-by-disabling-windows-hibernate-function/](http://www.techrepublic.com/blog/tr-dojo/delete-hiberfilsys-by-disabling-windows-hibernate-function/)

Boot Repair sometimes fails when Windows is hibernated.

---

### Post by douglas-shuler91 on 2014-02-04
Okay, so I started out with what Lukas had posted. also, westie my fastboot is disabled, as well as all hibernations. 

I started with the boot repair, it moved along nicely until I've hit another block. Boot repair did it's stuff until it told me to type some commands into terminal. I do this and let it finish. I then click forward on the box and I get an error saying "GRUB is still present. Please try again". I've gone through this a few times now to no avail. Boot repair will NOT finish what it's trying to do. Any answers to this? Sorry if I'm being a royal pain in the ass.

---

### Post by LukasLeon on 2014-02-04
Well, when you are completly sure that fastboot is disabled and there is no hibernation allowed for Windows 8, i dont know what else could be possibly wrong sorry.. but i am sure someone here will find a solution for this.. However i have one kinda tricky solution, which is not rly the correct one, but you can try it in the meantime while waiting for somebody to answer you.. Once i have installed win, Ubuntu as a dual boot and a Xubuntu via a wubi.exe in windows, that way, when i started PC i get an option to boot to Xubuntu or Win thrue the Windows Boot Screen, when i choosed Xubuntu it loads up grub which gives me an option to load Xubuntu or my Ubuntu.. You can maybe try to install Xubuntu (or any other from the list in wubi) thrue wubi.exe in your win, use the minumum space needed while you dont actually need it , and that way after choosing it in win boot manager you will maybe load yourself a grub and there choose your legit Ubuntu to boot up xD. I told this is really just a temporary solution and it is kind of a stupid, but it should work :D

---

### Post by Bucky Ball on 2014-02-04
Very convoluted. Don't go there unless you actually want Wubi, Ubuntu installed INSIDE Windows. Using Wubi as a bootmanager/loader rather than fixing the actual issue is not advised. Wubi is not supported in recent releases for one. 

Could you please answer oldfred's questions in post three? This is quite possibly an EFI/Legacy problem. Boot Repair may have chosen to turn your Ubuntu install to EFI but can't get rid of the regular grub-pc. It may be on a drive or partition other than sda. We don't know without more info.  

Please attempt to tell exactly how you went about installing Ubuntu. Was the disk set to EFI and did you switch off fastboot, secureboot, etc.? Have you tried rebooting the machine at this point? You might try that and tell us what happens so we can see where you are. Also, please create the bootinfo script in Bootrepair so we can see it. Thanks.

*Thread moved to **Installation & Upgrades**.*

---

