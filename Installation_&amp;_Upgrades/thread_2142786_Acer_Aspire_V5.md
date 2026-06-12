---
title: "Acer Aspire V5"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by cbutu on 2013-05-06
After my desktop crashed I purchased an Acer Aspire V5 laptop with an I7 processor. It has window 8 but I can't get to the bios. Can I create a boot disk for Ubuntu on a separate disk and run/boot to Ubuntu. Need help to get back to running Ubuntu.

---

### Post by oldfred on 2013-05-06
You have to get into UEFI to boot flash drive. Is this an UltraBook. That has added issues.

       You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 
One user posted this:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.


 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

      
 Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by Coinbird on 2013-07-02
(Great info in the post previous to mine, thanks for that (it helped me))

> **cbutu said:**
> After my desktop crashed I purchased an Acer Aspire V5 laptop with an I7 processor. It has window 8 but I can't get to the bios. Can I create a boot disk for Ubuntu on a separate disk and run/boot to Ubuntu. Need help to get back to running Ubuntu.

Hi,
  I just bought an Acer Aspire v5-122p, which I think is a similar machine (Windows 8 preinstalled, UEFI, recovery partition.) 
The instruction sheet that came with the computer tells you there's a PDF user manual, accessible by typing "User" from the Start screen. The manual, among other information, says to access the BIOS via F2. (you might want to enable F12 boot menu for the final step--but leave the default settings for now.)

First in Win8, I created a recovery disk and deleted the recovery partition (windows does this for you after the disk is created, as an option.) Then I shrunk the primary (biggest) partition by 100 GB via the windows disk management utility. This was for the swap partition and the primary ext4 partition.

I created my ubuntu USB stick from Windows via the Universal USB Stick creator (I think I found it linked off the ubuntu page.) I used the Ubuntu Desktop 13.04 64-bit ISO (other versions will probably not work.)

To boot from UEFI to USB stick from Windows 8, you don't need to mess with the BIOS! First, Windows Key + W (shortcut to bring up Settings,) type "boot" and navigate to Advanced Boot Options. Click the Advanced Boot option (at the bottom of the settings page) and you'll get to win8 screen that lets you choose to boot to EFI USB.

Booted into the Install environment fine (I had issues with the "Try Ubuntu" option because of the graphics card failing to work with lightdm. Luckily, the "Install Ubuntu" option works for my specific laptop.
 
In the Installation environment the first thing to do is to connect to wifi, if you want to connect after the installation is over. 
Next, in the partitioning step, I chose "other" (the last option) In the 100 gigs of free space, I created a 16 gig swap partition and then the rest of the partition (~84 gigs) as ext4, mount as /. The installation then proceeded normally and finished.

Now I have 2 options for dual boot:
* Boot into Windows 8, and via the Advanced Boot menu as before, choose EFI ubuntu
* At bootup, hit F2 (or F12 if enabled) and select Ubuntu in the boot order.

Now, when you boot into Ubuntu there is one last problem: no display manager! Lightdm will crap out as the X server failed with "no screens found". Log into the command prompt. Luckily wifi settings persist from the Install step! 

Note *lspci* shows the graphics card for my machine is a Radeon HD 8250. 
So to fix this last problem (X server not loading,) install the AMD Catalyst beta driver from here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

```

wget http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip
unzip amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip
chmod u+x amd-driver-installer-catalyst-13-6-beta-x86.x86_64.run
sudo ./amd-driver-installer-catalyst-13-6-beta-x86.x86_64.run

```

Seems to be running great now! It's nice having a touchscreen for the Unity interface.
 
Would nice to have a more convenient way to select which OS to boot instead of having to scramble to hit F-keys at boot time (or boot into windows 8 first) but was glad to see that I didn't have to disable EFI or Secure Boot, and it was a fairly simple process.

Hope this post helps the next person with an Acer Aspire v5. Any other tips appreciated!

---

### Post by randompie on 2013-08-17
This might be OT - but does the touchscreen work? I have not been able to find details of whether the touchscreens on these Win 8 boxes work under various Linux flavours.

Thanks ...

---

### Post by oldfred on 2013-08-17
I do not know touch screens, but I think at least some do work. Ubuntu is working on a phone so they have drivers for that.

---

### Post by GPK-SIM on 2013-12-17
> **Coinbird said:**
> (Great info in the post previous to mine, thanks for that (it helped me))



Hi,
I just bought an Acer Aspire v5-122p, which I think is a similar machine (Windows 8 preinstalled, UEFI, recovery partition.) 
The instruction sheet that came with the computer tells you there's a PDF user manual, accessible by typing "User" from the Start screen. The manual, among other information, says to access the BIOS via F2. (you might want to enable F12 boot menu for the final step--but leave the default settings for now.)

First in Win8, I created a recovery disk and deleted the recovery partition (windows does this for you after the disk is created, as an option.) Then I shrunk the primary (biggest) partition by 100 GB via the windows disk management utility. This was for the swap partition and the primary ext4 partition.

I created my ubuntu USB stick from Windows via the Universal USB Stick creator (I think I found it linked off the ubuntu page.) I used the Ubuntu Desktop 13.04 64-bit ISO (other versions will probably not work.)

To boot from UEFI to USB stick from Windows 8, you don't need to mess with the BIOS! First, Windows Key + W (shortcut to bring up Settings,) type "boot" and navigate to Advanced Boot Options. Click the Advanced Boot option (at the bottom of the settings page) and you'll get to win8 screen that lets you choose to boot to EFI USB.

Booted into the Install environment fine (I had issues with the "Try Ubuntu" option because of the graphics card failing to work with lightdm. Luckily, the "Install Ubuntu" option works for my specific laptop.

In the Installation environment the first thing to do is to connect to wifi, if you want to connect after the installation is over. 
Next, in the partitioning step, I chose "other" (the last option) In the 100 gigs of free space, I created a 16 gig swap partition and then the rest of the partition (~84 gigs) as ext4, mount as /. The installation then proceeded normally and finished.

Now I have 2 options for dual boot:
* Boot into Windows 8, and via the Advanced Boot menu as before, choose EFI ubuntu
* At bootup, hit F2 (or F12 if enabled) and select Ubuntu in the boot order.

Now, when you boot into Ubuntu there is one last problem: no display manager! Lightdm will crap out as the X server failed with "no screens found". Log into the command prompt. Luckily wifi settings persist from the Install step! 

Note *lspci* shows the graphics card for my machine is a Radeon HD 8250. 
So to fix this last problem (X server not loading,) install the AMD Catalyst beta driver from here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

```

wget http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip
unzip amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip
chmod u+x amd-driver-installer-catalyst-13-6-beta-x86.x86_64.run
sudo ./amd-driver-installer-catalyst-13-6-beta-x86.x86_64.run

```

Seems to be running great now! It's nice having a touchscreen for the Unity interface.

Would nice to have a more convenient way to select which OS to boot instead of having to scramble to hit F-keys at boot time (or boot into windows 8 first) but was glad to see that I didn't have to disable EFI or Secure Boot, and it was a fairly simple process.

Hope this post helps the next person with an Acer Aspire v5. Any other tips appreciated!
What version of Unbutu did you use and is your model the V5-122P-0408?

---

### Post by Anthony_T on 2014-03-21
> **Coinbird said:**
> 
First in Win8, I created a recovery disk and deleted the recovery partition (windows does this for you after the disk is created, as an option.) Then I shrunk the primary (biggest) partition by 100 GB via the windows disk management utility. This was for the swap partition and the primary ext4 partition.


Hi, Thanks for the detailed info, I have the same laptop.  I have tried the USB boot through F2 but half way through I get a white screen and the install process freezes. :( 
Also, I would like to know why you deleted the recovery partition.  Is that necessary?

And is it possible to do this setup with the **Windows installer**?  I would like to preserve my Windows 8 original install and have Ubuntu installed on the side.

Thanks in advance!:)

---

### Post by oldfred on 2014-03-23
@Anthony_T
You do not have to erase Vendor recovery, but if you have your DVD set, then recovery has little use. Also if drive fails recovery on drive then is worthless, but you can still use the DVD set to restore to new drive.

You use Windows tools for Windows and Linux tools for Linux, generally. A few cases you can fix some Windows issues from Linux, but I do not know of anything you fix in Linux from Windows.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

        Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by smokin420papi on 2014-08-12
hello i have a acer aspire v5 122p-0889 i have put a admin password on my bios unintentually and now its locked i cant remember the password is there anyway to reset that or delete it i have windows 8.1 and ubuntu gnome 14.10 alpha 2 somebody please help

---

### Post by oldfred on 2014-08-12
Windows password or Acer UEFI password?
I found these with a little search.

[http://www.tech-faq.com/how-do-i-reset-an-acer-bios-password.html](http://www.tech-faq.com/how-do-i-reset-an-acer-bios-password.html)
[http://www.tech-faq.com/reset-bios-password.html](http://www.tech-faq.com/reset-bios-password.html)

[http://www.top-password.com/blog/forgot-admin-password-for-your-acer-pc-with-windows-8-pre-installed-in-uefi-boot-mode/](http://www.top-password.com/blog/forgot-admin-password-for-your-acer-pc-with-windows-8-pre-installed-in-uefi-boot-mode/)

But you should never forget admin passwords. You just end up with a brick.

---

### Post by justiny99 on 2015-03-07
PS&#65306; If you use UEFI in Windows 8/8.1 this article will show you how to disable UEFI secure boot:
[http://www.windowspasswordsrecovery.com/win8-tips/how-to-disable-uefi-secure-boot-in-windows-8-1-8.html](http://www.windowspasswordsrecovery.com/win8-tips/how-to-disable-uefi-secure-boot-in-windows-8-1-8.html)

---

### Post by alfu2 on 2015-04-27
Would someone with authority to create tags please create a "Aspire V5 122p" tag?

Thank you.

---

### Post by oldfred on 2015-04-27
There are too many brands & models of computers. And just about every country the model is slightly different, but specs may be similar, just power cord/supply may be different or minor changes for a price point.

And many fixes apply across all models and often across brands as UEFI is configured for all systems with just the differences in options or processors.

I do find if you want details you can use google search and specify site:ubuntuforums.org and then details like a computer model and get all posts with that model.

---

