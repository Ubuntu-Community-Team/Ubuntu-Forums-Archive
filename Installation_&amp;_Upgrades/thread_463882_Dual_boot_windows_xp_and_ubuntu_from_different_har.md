---
title: "Dual boot windows xp and ubuntu from different hard drives"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by joy83 on 2007-06-04
OK, so my 160 GB hard drive in my desktop is completely devoted to ubuntu 7.04, now i am a great fan of some of the windows games like civ4, company of heroes even though in general i hate windoze. As the expansion packs are coming up for these games I was planning to install windows xp, now I dont want to reinstall ubuntu again and install all the codecs and stuff (tired of backing up). So I was planning to buy another internal hard drive and dedicate that drive to windows for playing games. Is this possible?

I mean without doing anything to the exisiting ubuntu, I buy another internal hard drive and install windows xp in it and dual boot the computer.

---

### Post by NilsE on 2007-06-04
If your BIOS has the option to select an alternate boot device at startup I would suggest removing the current drive from the system, install the new drive and then install Windows on it.  Then put the other drive back in and use the BIOS boot selection to run the OS of choice. You can then set the BIOS to boot off of whichever one you want by default and then select the other when you want to boot from it by using the BIOS F12 option (or whatever it is) for alternate boot device.

This way no need to worry about what GRUB does to MBR etc. I did it that way (actually had XP on the drive first) and it works well.

---

### Post by zvacet on 2007-06-04
[http://ubuntuforums.org/showthread.php?t=275728&highlight=two+drives]("http://ubuntuforums.org/showthread.php?t=275728&highlight=two+drives")

---

### Post by joy83 on 2007-06-04
> **NilsE said:**
> If your BIOS has the option to select an alternate boot device at startup I would suggest removing the current drive from the system, install the new drive and then install Windows on it.  Then put the other drive back in and use the BIOS boot selection to run the OS of choice. You can then set the BIOS to boot off of whichever one you want by default and then select the other when you want to boot from it by using the BIOS F12 option (or whatever it is) for alternate boot device.

This way no need to worry about what GRUB does to MBR etc. I did it that way (actually had XP on the drive first) and it works well.

Thanks, but do I have to go to BIOS everytime i want to boot to a different operating system? I mean cant i have that option during boot time which asks  me which OS to boot. I know I probably have to do something in the GRUB, but i also heard that ubuntu 7.04 has an "advanced" GRUB button but I dont know much about it.

---

### Post by NilsE on 2007-06-04
> **joy83 said:**
> Thanks, but do I have to go to BIOS everytime i want to boot to a different operating system? I mean cant i have that option during boot time which asks  me which OS to boot. I know I probably have to do something in the GRUB, but i also heard that ubuntu 7.04 has an "advanced" GRUB button but I dont know much about it.
Yes, you can use GRUB to set it up so you select the OS you want at boot time.

I was suggesting that if you had an option when the system is booting to hit for example F12 to select the device to temporarily boot from you could avoid managing GRUB. I was not suggesting you go into the BIOS every time but based on your question I guess you don't have the option to select a temporary boot device. 

For example on my system if I want to go into BIOS setup I hit F2 when it is booting and it takes me into setup.  If I hit F12 it give me a menu of all my bootable devices and I select the one I want. That is similar to GRUB except if I don't hit anything it automatically goes to Ubuntu because that is my primary boot device. And yes, GRUB can do all that for you I just find this easier and faster.

---

