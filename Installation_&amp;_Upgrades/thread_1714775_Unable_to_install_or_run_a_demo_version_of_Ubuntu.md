---
title: "Unable to install or run a demo version of Ubuntu"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by JTallis on 2011-03-25
This is a newly built computer with newly installed Windows 7. It's a 1TB hard drive which I have partitioned into C:\ and L:\ (L for Linux). Linux has 100GB disk space.

Both drives are NTFS. Typically the default.

I downloaded the .iso file from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and it is the 64 bit version and then I burned the iso to a clean disk. It's also the latest, 10.10.

After rebooting, I came up with two options to choose from - Windows or Ubuntu. This would be which to boot. I chose Ubuntu, the obvious.

The default selection is the standard installation, I also tried out the demo.

The error for the Ubuntu Installation is as follows:
BusyBox v1.15.3 (Ubuntu 1:1.15.3=1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
Could not find the installation files /ubuntu/install/custom-installation This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it. To fix this, simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into Windows. After this you should be able to reboot again and resume the installation.

Now for the Ubuntu Demo, the error is as follows:
BusyBox v1.15.3 (Ubuntu 1:1.15.3=1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system.

I redownloaded the .iso (originally it was in /temp), opened it up with Winrar and checked the files. They all seemed to be in order with none missing.

I do not have a USB to try the installation with either. I rarely use any external data devices.

What appears to be the problem?

---

### Post by oldfred on 2011-03-25
Did you verify that it is downloaded correctly and did you burn it to the CD at the slowest speed your drive lets you. You also burn it not copy it, so it extracts a bootable CD not just a copy of the ISO on the CD.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

When you first start CD do you get human icon & keyboard. If so push any key and you can run a verify of disk from that.

---

