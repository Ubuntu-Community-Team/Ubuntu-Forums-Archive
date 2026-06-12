---
title: "3 different Ubuntu installs. 2 drives."
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by R3linquish3r on 2006-04-22
Well Ive looked around for about an hour but really havent found anything to answer my questions...

My plan is to setup as follows:

80GB IDE Drive:

512MB Will be Swap
40GB Will be for Movies and such
40GB Will be for Dapper

120GB SATA Drive

60GB Will be for x32 Breezy
60GB Will be for x64 Breezy
512MB Will be Boot


My question is: I'll start by installing the x32 which will be my stable version. x64 and dapper are for messing around. Ill start by making the Swap Boot and Root for x32 partitions and I'll install x32. After that I will install x64 and Dapper. When I install x64 and Dapper do I skip the phase were I install GRUB completely and then when I boot into x32 just do "sudo update-grub" and I should be good to go? Also, when I go to setup the partitions for the other isntalls. I have to reselect the partition for Boot and set it for Boot when I install the other version of Ubuntu? I ran into some trouble when I went to install x64 and GRUB for that didn't install properly and I had to start all over. It also seemed that I had to re-partition the Boot area in some way. When I went to isntall the x64 it just labeled Boot as /dev/sda2 so I selected it and changed it to boot. It still had the black face isntead of the white face so I'm guessing it wouldn't change that. :( I hope this can be answered as quick as possible.

---

### Post by Sutekh on 2006-04-22
[QUOTE=R3linquish3r]
My question is: I'll start by installing the x32 which will be my stable version. x64 and dapper are for messing around. Ill start by making the Swap Boot and Root for x32 partitions and I'll install x32. After that I will install x64 and Dapper. When I install x64 and Dapper do I skip the phase were I install GRUB completely and then when I boot into x32 just do "sudo update-grub" and I should be good to go? [/quote]
What I do is install GRUB on the MBR for my 'main' install of Ubuntu, and then with subsequent installs (I like mucking around with dapper/server installs) I install GRUB onto the partition that the installation is on.

So if I install Dapper to mess around with on /dev/hda2 say, then I install GRUB (from the Dapper install) on /dev/hda2.  Once it's all done, all you have to do is copy the Dapper GRUB menu entry from /dev/hda2 to the main GRUB menu.  Then do the same for any other installations.

I hope you understand what I mean, I'm sure update-grub will work, I just wanted to relate my preferred method.

[quote=R3linquish3r]
Also, when I go to setup the partitions for the other isntalls. I have to reselect the partition for Boot and set it for Boot when I install the other version of Ubuntu? I ran into some trouble when I went to install x64 and GRUB for that didn't install properly and I had to start all over. It also seemed that I had to re-partition the Boot area in some way. When I went to isntall the x64 it just labeled Boot as /dev/sda2 so I selected it and changed it to boot. It still had the black face isntead of the white face so I'm guessing it wouldn't change that. :( I hope this can be answered as quick as possible.[/QUOTE]
That sounds about right, change the mount point from /dev/sda2 to /boot but don't format.   I have never used a common /boot partition though. I think the black face is what you want to see.  Skull and crossbones means that it will format IIRC.

Good Luck!

---

### Post by R3linquish3r on 2006-04-23
Thanks for the input. I had a brainstorm last night of wiping both drives clean and installing the main with GRUB in the boot partition and then isntall the other two withou GRUB, then just go back into the main and do sudo update-grub. Ill attempt your way if it doesnt work :)

---

### Post by R3linquish3r on 2006-04-23
If anyone can answer another question I have....

How big does my Boot partition need to be? And do I need to set the bootable flag to on?

---

### Post by Sutekh on 2006-04-23
[QUOTE=R3linquish3r]Thanks for the input. I had a brainstorm last night of wiping both drives clean and installing the main with GRUB in the boot partition and then isntall the other two withou GRUB, then just go back into the main and do sudo update-grub. Ill attempt your way if it doesnt work :)[/QUOTE]
With a fresh install why not give that a try, it sounds quite feasible.

[QUOTE=R3linquish3r]If anyone can answer another question I have....

How big does my Boot partition need to be? And do I need to set the bootable flag to on?[/QUOTE]
The boot partition needs to be big enough to fit all the default kernel images of each OS, plus any others you might install afterwards.  I think each kernel image is around 16-20 MB from memory.  Maybe someone can confirm how much space their kernel images (and other stuff in /boot) takes up.  512 MB will be plenty I'm sure.

The bootable flag should be on.  I would hope that the installer would do this automatically, when you set the mount point to be /boot, but just check.

---

