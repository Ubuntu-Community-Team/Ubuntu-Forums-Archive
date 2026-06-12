---
title: "Uninstalling Ubuntu 18.04.4 to Install Ubuntu 20"
date: 2020-05-07
forum: Installation &amp; Upgrades
---

### Post by digital-junkie on 2020-05-07
I want to uninstall my current Ubuntu 18.04.4 and install the version 20. But I have an issue... 

Due to the issues my Ubuntu 18.04.4 is having I will not be able to upgrade it from the terminal.


My issue was discussed in this thread:
[https://ubuntuforums.org/showthread.php?t=2442291](https://ubuntuforums.org/showthread.php?t=2442291)

.. and I was advised to install a new version of Ubuntu.



I have downloaded Ubuntu 20 on my bootable flash drive. 


Please how can I run the new installation? I want to completely install the new version to override the previous version.

I have inserted the flash, restart my system while pressing F10, I can't locate my flash to load the Ubuntu from. Where do I need to enter to load the OS that is on my flash?

Or is there any way I can achieve this?

---

### Post by DuckHook on 2020-05-07
[LIST=1]
[*]Let it boot from your flash drive and choose "Try Ubuntu".
[*]Then, when the desktop shows up, there is an icon that will allow you to install with graphical dialogue boxes and prompts.
[*]Follow along with the appropriate choices until it gets to the part where it asks where you would like to install the OS.
[*]Choose "Erase Disk and install Ubuntu" or "Erase Previous Installation and install New Ubuntu". Do **NOT** choose "Install side-by-side". Do **NOT** choose "Upgrade Existing Ubuntu" (or however it is phrased).
[/LIST]
Graphical instructions here: [https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview)

Read through them first to make sure you can follow along exactly.

By choosing "Erase Disk&#8230;" it will automatically purge your old Ubuntu. There will be nothing left of 18.04. Be sure that you have all of your important personal data backed up first. After you install 20.04, you will not be able to get any data back.

---

### Post by DuckHook on 2020-05-07
I'm sure you've learned from your previous experience. This time, do not change anything on your base OS. Instead, install a VM, install a virtual Ubuntu in the VM, take a snapshot immediately after installing, and experiment on that.

---

### Post by DuckHook on 2020-05-07
> **digital-junkie said:**
> &#8230;I have inserted the flash, restart my system while pressing F10, I can't locate my flash to load the Ubuntu from. Where do I need to enter to load the OS that is on my flash?

Or is there any way I can achieve this?
Apologies. I did not read your initial post completely.

[LIST=1]
[*]How did you install 18.04 the first time? You had to have been able to boot from the USB that time.
[*]Is your flash drive a good one?
[*]How did you burn the ISO image? What burner software did you use?
[*]Did you do a MD5 checksum?
[/LIST]

---

### Post by digital-junkie on 2020-05-08
1. The first time I installed Ubuntu 18.04.4, I was using windows then, so I inserted the flash and while booting I pressed F10... But it seem not to be giving me the same option now on Ubuntu. F10 takes me to Ubuntu bios and I can't find my flash to select and boot from.

2. Yes, my flash is a good one. 
3. I used Rufus on windows. I couldn't make the flash bootable on Ubuntu.
4. I don't know why MD5 checksum mean. 








Again, let me explain how I made the flash bootable: 


After making it bootable with Rufus [on windows] , I sent the ISO file to the root directory of the flash drive. 


I hope it works that way?


Please which function key should I press to give me the boot option?

---

### Post by yancek on 2020-05-08
What hardware manufacturer?  HP, Dell, ??  Did you use the instructions at the rufus site at the link below?

  [https://rufus.ie/](https://rufus.ie/)

>  F10 takes me to Ubuntu bios

There is no "Ubuntu BIOS", that is part of the hardware before you even have anything installed so you are probably seeing the Grub/syslinux bootloader.
Md5 checksum is explained at the Ubuntu documentation site at the link below.

 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

> After making it bootable with Rufus [on windows] , I sent the ISO file to the root directory of the flash drive. 

I don't know what that means.  See the rufus link above, did you follow that process?

---

