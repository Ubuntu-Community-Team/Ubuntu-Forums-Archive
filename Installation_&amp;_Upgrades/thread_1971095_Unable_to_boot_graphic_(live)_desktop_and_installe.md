---
title: "Unable to boot graphic (live) desktop and installer, freeze (SiS M760)"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by Smetsers on 2012-05-02
I have a Fujitsu Siemens Amilo A1645 notebook working perfect with Ubuntu 11.04 (32 bit) and 11.10 (32 & 64 bit). Installation was a piece of cake and except for the wireless driver that had to be installed manually (Broadcom 4318; b43-fwcutter, firmware-b43-installer) everything worked out of the box.

I decided to do a clean install of 12.04 Precise Pangolin so I erased my HDD (shred) just like I did before all previous installs and tried to boot the 12.04 (64 bit) desktop-CD. After getting to the language select screen I selected the "install" option. Some moments of a screen with "Ubuntu 12.04" and the dots beneath are then followed by a screen with all kind of notifications (see picture below) and a some kind of freeze of the system, no response on keys and the only option is to shutdown.

[IMG]http://forum.ubuntu-nl.org/installatie/grafische-desktop-niet-op-te-starten-zowel-live-cd-als-alternate/?action=dlattach;attach=16091;image[/IMG]

I then tried to install Precise Pangolin by the text-based alternate-CD which worked quite well but after the necessary reboot the system freezes again with a blinking underscore or a screen with notifications as shown above. I then tried to boot the desktop-CD by the Live-option with options nomodeset, acpi=off and vga=771/???. All results in a freeze of the system. I also tried to boot with "xforcevesa" when pushing escape at the language select menu but this gave "Could not find kernel image: xforcevesa". Furthermore I tried to boot a live Xubuntu-CD but this also gave a freeze with "Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic x86_64) * Documentation [https://help.ubuntu.com/](https://help.ubuntu.com/)) on the screen. So I assume it has nothing to do with Unity.

Meanwhile I cannot find a solution in all the threads on the internet so I wonder if anyone has a clue what's going wrong? I think it's very strange Ubuntu 12.04 isn't working while 11.04 and 11.10 were working perfect on exact the same notebook. The notebook has a AMD Turion 64 MT-28 CPU and 1GB RAM (870.4 MiB after subtraction for video chip?). The video chip is if I'm right a SiS M760.

I wonder if anyone has a solution how to get the Live-CD option working while I reinstalled 11.10 to maintain productive.

---

### Post by aaazman on 2012-05-02
I am no expert. Try Ctrl-Alt-F7.

---

### Post by Smetsers on 2012-05-03
At which moment should I hit Ctrl-Alt-F7 aaazman?

I haven't been able yet to start up any desktop at my laptop. I guess it has something to do with the new kernel. Does anyone have a clue what changed in the kernel? Until now I was only able to boot in a text-mode.

---

### Post by aaazman on 2012-05-07
When you boot your Ubuntu PC (in my case my USB flash drive,) you will get your boot messages, Ctrl-Alt-F1, Ctrl-Alt-F2, Ctrl-Alt-F3, or Ctrl-Alt-F4 should get you a terminal. However, Ctrl-Alt-F7 should get your X Desktop. By the way, precede this keystroke with a choice of a terminal: the previous keystroke combination (i.e., Ctrl-Alt-F1.)

---

### Post by jadtech on 2012-05-07
from all I am reading  its very possible that 12.4 ubuntu is to much for it to really handle well even if you manage to install it maybe try the lite version ...

---

### Post by westie457 on 2012-05-07
Try this work around.

[http://ubuntuforums.org/showpost.php?p=11883375&postcount=6](http://ubuntuforums.org/showpost.php?p=11883375&postcount=6)

---

### Post by Smetsers on 2012-05-08
> **westie457 said:**
> Try this work around.

[http://ubuntuforums.org/showpost.php?p=11883375&postcount=6](http://ubuntuforums.org/showpost.php?p=11883375&postcount=6)
Hooray, this worked! I was able to start the live-CD function by adding "b43.blacklist=yes" as well when using the graphic installation. I saw the message "b43/ucode5.fw not found" but I assumed this wasn't the problem while I also saw this when installing Ubuntu 11.10, which caused no problems.

So actually solved for me! I experience 12.04 being even faster than 11.10 on my notebook!

---

