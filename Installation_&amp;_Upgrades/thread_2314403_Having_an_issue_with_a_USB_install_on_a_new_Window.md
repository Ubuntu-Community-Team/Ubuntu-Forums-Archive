---
title: "Having an issue with a USB install on a new Windows computer"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by Speedwagon on 2016-02-20
I recently purchased a new HP laptop, running Windows 10. I have a USB drive of Ubuntu 15.10 64 bit. I am having some issues with this though.

I set the computer to boot from USB first. Once it gets to the GRUB menu, if I tell it to try without installing, it will often go to a blank screen and just sit there. If I hit C first, then ESC, then try without installing, it seems to work. I am able to use the computer from that point, on the live USB. But once I tell it to install Ubuntu (I intend to dual boot), I proceed to the window with the "download updates, third party software" and hit continue, I then get a blank screen.

I'm a bit baffled as to why it is doing this. The USB drive was a good working unit before I tried it in this computer. I have since used Pendrivelinux a few times to verify the install, and I ran an MD5 comparison to check the ISO file.

What is the next step to resolve this?

Computer is a new HP Pavilion 17 touchscreen.

---

### Post by yancek on 2016-02-20
Do you have any unallocated space on the drive on which to install Ubuntu?  Windows generally will take up the entire disk.  If you boot the Ubuntu usb, open a terminal and run the following command:  sudo gparted  You can post the image here which will give some info on your system.

---

### Post by Speedwagon on 2016-02-21
I intended to resize the partition, and give Ubuntu ~100Gb of the 1Tb drive.

However, I can't seem to get past the GRUB screen now into the live USB part.

---

### Post by oldfred on 2016-02-21
Use Windows to resize the NTFS partition. And reboot immediately so it can run chkdsk.
And with Windows 10 make sure fast startup or the always on hibernation is off.
Often better to have UEFI Secure Boot off, but leave UEFI on, not CSM/Legacy/BIOS boot.
Flash drive should show two ways to boot UEFI:flashdrive and flashdrive (which then is the BIOS boot).

What chip and what video card/chip?
Often boot parameters required.

 With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel

 dual AMD
[http://ubuntuforums.org/showthread.php?t=2288314&p=13329042#post13329042](http://ubuntuforums.org/showthread.php?t=2288314&p=13329042#post13329042)
With the upcoming Linux 4.2 kernel will be the premiere of the new "AMDGPU" 
kernel driver to succeed the "Radeon" DRM kernel driver
[http://tech.slashdot.org/story/15/07/25/2014228/amd-starts-rolling-out-new-linux-driver-model-but-many-issues-remain](http://tech.slashdot.org/story/15/07/25/2014228/amd-starts-rolling-out-new-linux-driver-model-but-many-issues-remain)

   AMD drivers alternatives
[http://ubuntuforums.org/showthread.php?t=2256824](http://ubuntuforums.org/showthread.php?t=2256824)

   open (Gallium3D) and closed-source (Catalyst) driver

   The Slides Announcing The New "AMDGPU" Kernel Driver
[http://www.phoronix.com/scan.php?page=news_item&px=MTgwODA](http://www.phoronix.com/scan.php?page=news_item&px=MTgwODA)

---

### Post by Speedwagon on 2016-02-22
AMD A10-8780P, Radeon R8 M360.

It looks like the kernel in 15.10 iso is 4.1 then? 4.2 appears to be released though, which would mean a pre-release of 16.04 might well do just fine on this computer?

If 16.04 would work out of the box, I may just hold off on dual booting this computer for another month, and get myself a hybrid drive to install in the mean time(this only came with a standard 5400 drive).

---

### Post by oldfred on 2016-02-22
While not released you can still install 16.04 to see if it works better.

I keep my desktop with 14.04 as main working install as hardware has no issues with it, but then have installed 16.04 in another 25GB / (root) partition just to see if it works ok. It may break as they update things more, so I do not depend on it. And with all the changes & updates I will reinstall to houseclean out logs and many updates when it finally is released.

---

### Post by Speedwagon on 2016-04-09
I cannot figure this thing out. I've tried following some instructions on booting with UEFI, but I am not having any luck.

I get to the menu for the live USB drive, but when I try to run without installing, it will go to the Ubuntu name with the status dots, then the screen goes black and nothing after that. 14.04, 15.10, 16.04 beta 2 all fail.

---

### Post by oldfred on 2016-04-09
At grub menu have you tried nomodeset?
But some systems also need added boot parameters in addition to nomodeset.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710) 

Other HP, often UEFI (and issues) is similar across models.

 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)

---

