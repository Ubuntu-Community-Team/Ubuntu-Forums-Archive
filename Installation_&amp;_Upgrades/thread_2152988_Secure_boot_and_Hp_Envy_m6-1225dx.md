---
title: "Secure boot and Hp Envy m6-1225dx"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2013-06-09
New laptop with secure boot and windows factory oem.  Have been trying to dual boot windows 8 with either ubuntu 13.04 or fedora 18...this is what I have learned thus far.

I can disable secure boot in order to install either ubuntu or fedora, however upon reboot, system goes straight to windows 8.  Rebooted system and went int bios again, and yep you guessed it, secure boot was enabled again, and not by me.

I have been able to disable secure boot and install ubuntu and fedora over windows, but not side by side.

When I had them side by side, it required me to go into f9 boot options and from there I could should choose ubuntu or fedora, but bith give me kernel panics.

What gives, why is it so hard to dual boot fedora or ubuntu with windows 8 and secure boot.  I was under the impression that both fedora and cannonical had purchased the right and or keys to do this?

Henry

---

### Post by oldfred on 2013-06-09
Does Windows boot with secure boot off or only with it on? 

Ubuntu does have secure boot grub & kernels which you will need if your system only boots with secure boot on.

Often Boot_Repair can do the work arounds required to get most systems working.  Also see link in my signature.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Hewjr100 on 2013-06-09
I suppose windows 8 could boot with secure boot off, but like I said in first post, when rebooting, for some reason secure boot is re-enabled.  Probably something hp did with it's oem image.  Anyway not to be funny or anything, but I liked linux when you could more or less install it and forget it, sorta like mint.  But this secure boot efi thing, which I believe much ado about nothing, has been blown out of proportion.  Pay the fee for the key and move on, nothing in life is 100% free.  Even living in a cave will cost you blood sweat and tears.

Henry

---

### Post by sparks40 on 2013-07-17
I'm in the same boat. Any progress since your last try at this problem.
TNX
K2OSP

---

### Post by fantab on 2013-07-18
'Secure boot' is NOT a doing of Linux, its Microsoft which is responsible for it. Both Ubuntu and Fedora can boot with 'Secure-Boot' enabled. Which means you can install Ubuntu with 'Secure Boot' enabled.
Windows 8 comes with a 'fast-startup' feature which in effect keeps the PC in 'Hibernation' when you actually Shut it down. To install Ubuntu Windows8 MUST be Shutdown properly, [Disable 'Fast Startup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
Also there is 'fast boot' which should be disabled, in UEFI. If you laptop came with a pre-installed SSD and HDD and is based on Intel then look for 'Intel SRT' and disable it too.

Use only Windows Disk Management tool to manage your Windows partitions. [Shrinking Windows partitions]("http://www.liberiangeek.net/2012/11/shrink-resize-partitions-in-windows-8/") to make space for Ubuntu.

Then install Ubuntu. To install Ubuntu in UEFI mode it needs to be booting in UEFI mode. When you boot in UEFI mode you will see a Black Screen with options. The regualr Ubuntu color scree will indicate that its is NOT booted in UEFI mode.
There is bug in Grub or OS-Prober (not sure which) which creates a wrong entry for Windows8 and can cause Windows not to boot. This can be fixed easily with [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") utility.

Good Luck...

---

### Post by oldfred on 2013-07-18
Another HP Envy. Not sure if same model.

 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by distortedecho on 2014-06-26
You have to go into the BIOS (on boot press ESC and F10)

Then ENABLE Legacy Support.
TheLegacy Support Boot Options then become active, change the boot order there.
F10 to save and exit.

Boot and press F9 - choose your boot option.

---

