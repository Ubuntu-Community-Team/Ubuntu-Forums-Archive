---
title: "[HALFLY-SOLVED]Uninstall Ubuntu on UEFI computer"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by thederpyworld on 2014-01-03
Hi, I am new here, but I need help.

Recently my HDD was corrupted, so I bought a new one with GPT disk.
I installed there Windows 8.1 64bit. (of course with UEFI) I am considering about installing Ubuntu, but I want to know, how to safely uninstall it without losing Windows partition. I tried to google it, but I couldn't find it.

I just don't want to risk command "fixmbr". On some pages is writed, that it will corrupt the disk, if it is GPT. On some page it'll work perfectly.
Please help me.

Thank for help.
-Derpy Hooves

---

### Post by fantab on 2014-01-03
If you have installed Windows in UEFI then you needn't worry about 'fixmbr'. UEFI does not work from 'MBR' but from 'EFI partition'.
It is safe to install Ubuntu.. search this forum there are numerous threads to help you.

If you still have any doubts, just ask.
This page should get you started: [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by thederpyworld on 2014-01-03
> **fantab said:**
> If you have installed Windows in UEFI then you needn't worry about 'fixmbr'. UEFI does not work from 'MBR' but from 'EFI partition'.
It is safe to install Ubuntu.. search this forum there are numerous threads to help you.

If you still have any doubts, just ask.
This page should get you started: [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

So, the thing you want to say is, than even if I have disk in GPT table, I can still use 'fixmbr'?
(Just for safe)

---

### Post by thederpyworld on 2014-01-05
I really need this information. Please reply as fast as you could.

---

### Post by varunendra on 2014-01-05
> **thederpyworld said:**
> So, the thing you want to say is, than even if I have disk in GPT table, I can still use 'fixmbr'?
(Just for safe)

No, he meant exactly opposite of that. Don't use the "fixmbr" command !

[LIST]
[*]Shrink one of the partitions from 'inside' windows (that is, while Windows is running) using Windows' own disk manager program - to create empty space for installing Ubuntu.
[*]Make sure "Fastboot" is turned off in Windows.
[*]Then boot with Ubuntu 64 bit (32 bit can't be installed in EFI mode) live CD in "Test" mode > run "GParted" program on the live session > Create an EXT4 partition (+ a 2 GB swap is recommended but not necessary) > Save the changes and close the program.
[*]Now run the Ubuntu installer and choose "Something Else" option at partition selection stage of installation.
[*]Choose the EXT4 partition (that you just created) as mount point for '/' > Proceed with installation.
[/LIST]


Regarding your original question -
> but I want to know, how to safely uninstall it without losing Windows partition.
Although I'm not sure if this is the recommended method, but **in an EFI setup**, you can simply delete the Ubuntu partition later to remove it. It won't affect Windows booting.

**PS:**
By the way, it is HIGHLY RECOMMENDED to read the post in full that fantab linked to. It contains probably everything you need to know about UEFI setups. Don't follow the links that don't seem interesting, but at least read the post thoroughly.
Hope you have already read this wiki page : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for general guidelines.

---

### Post by varunendra on 2014-01-05
Interesting prefix - "[HALFLY-SOLVED]" :P

Mind letting us know what have you achieved so far and what is left to achieve to make it '[Fully-Solved]'?? :)

---

