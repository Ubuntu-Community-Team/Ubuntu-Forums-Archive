---
title: "Want Dual boot while keeping Windows MBR"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by BenWilson on 2007-05-25
When I used Gentoo, I had a laptop dual boot WinXP and Linux. The installation used the Windows Bootloader (MBR) that allowed me to chose between the two. When  Linux was chosen, the Windows loader invoked grub and the Linux loaded.

The default Ubuntu installation overwrites the MBR. I would like to control that aspect of the installation so I can us my own approach to booting. (Based on [http://dausha.net/Technical/WindowsDualBoot](http://dausha.net/Technical/WindowsDualBoot)).

Would somebody mind explaining how??

Ben Wilson

---

### Post by ryanVickers on 2007-05-25
Why don't you like the GRUB?  It did recognize windows and list it as an option, didn't it?

---

### Post by zencoder on 2007-05-25
I'm curious as to how this is done also. I've done it, years ago, and I forget how.

As for the "why"?  Not that Ben needs to justify asking a question, but I have a reason...I have already installed Feisty on my laptop and left a large amount of space unused.  Now I would like to put XP on part of that space for other uses.

---

### Post by ryanVickers on 2007-05-25
Here's a part of my grub file:  I've changed some of the names to look cleaner, but the data is the same.

> ## ## End Default Options ##

title		Linux - Ubuntu 7.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fc875855-6709-408e-b1c5-54e431aab68a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu Recovery mode
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fc875855-6709-408e-b1c5-54e431aab68a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Please ignore everything below this line:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Home
root		(hd0,1)
savedefault
makeactive
chainloader	+1


That just makes a boot option for (in this order):
linux
recoverymode linux
memtest
divider
windows xp

usually, I would recommend installing windows then linux so everything is automatic, but when this is not possible, just open /boot/grub/menu.list as root and add the entry for windows.  simply paste mine (the windows part) if you want and change the part that says (hd0,1) to match your situation.  the 0 in this case is the hard drive position (it is likely everyone will use 0) and the second one is partition number, starting at 0 and the left and counting up as it moves right.  I had linux, then windows, then linux swap in that order, so there fore my windows was 2nd, making it "1".  if it's first, it would be 0.  If it's third, then 2, and so on...

yes, I suppose, but I'm just saying "why?" because this one is much easier in my opinion.  I just though I'd say that because I saw no reason, and if he has one, fine, but if not, consider this.

---

### Post by BenWilson on 2007-05-25
> **ryanVickers said:**
> Why don't you like the GRUB?  It did recognize windows and list it as an option, didn't it?

I should say, this is for a brand new computer, and I've already bifurcated the drive for the Ubuntu install.

The reason why I did this last time was because the laptop was Compaq. To shorten the story of how, I was forced to use the system restore disk to recover after a laptop crash. The trouble was that the non-Windoze MBR prevended the system restore disk from doing anything other than a complete restoration of the factory install. This destroyed both Windows and Linux partitions.

Beyond that, I like having some say in the process. I prefer letting the Windows bootloader control initially. If you're familiar with Gentoo Linux, then I hope you'll understand that I am very comfortable mucking around with Linux internals (including GRUB). I prefer Ubuntu over Gentoo because, well, everything works and is painless. I don't have the time I used to have for fixing Gentoo.

It would be great if I could do all of the Ubuntu install _but for_ the GRUB. From there, I would be content to configure it manually.

Although, as an aside (not exactly related). I currently have a computer that I've not had time to fix because when I upgraded to Fiesty it completely mis-identified which drive was which (it is a eMachine where the first partition is the restore partition, second partition is C:\ and Linux follows. GRUB keeps assigning hda(0,1) to WinXP, which should be hda(0,2). Of course, I can fix that, but now that it uses UUID, I am in a bit of a bind. Again, this is an unrelated gripe that I can fix _when I have time_.

---

### Post by BenWilson on 2007-05-25
> **ryanVickers said:**
> Here's a part of my grub file:  I've changed some of the names to look cleaner, but the data is the same....

I appreciate that, but this does not address my core issue at all. I want to use the Windows bootloader at MBR, then feed the Linux choice into GRUB. I need to short-circuit the Ubuntu installation process as it automatically overwrites MBR.

---

### Post by merlinus on 2007-05-25
You should be able to easily restore the MBR from your windows cd after installing Ubuntu.

-merlin

---

### Post by ryanVickers on 2007-05-25
> I need to short-circuit the Ubuntu installation process as it automatically overwrites MBR.

Funny, that actually happened by acedent the first time I installed.  Of course I fixed it, but it's what you need. hm :)

I don't know how, the boot.ini windows uses looks alot more complicated, but I'm sure it's as easy as finding someone who's done it and just putting that entry at the end.

---

### Post by confused57 on 2007-05-25
I use the alternate install cd and you can definitely opt to install grub to the Ubuntu root partition...I don't use the live cd, but I believe you can specify to install grub to the root partition(from Dapper 6.06.1 live cd & later versions)...I think what you do is type in where you want to install grub in a menu "box" option that defaults to (hd0)...you could probably type in something like /dev/sda3, or whatever your root partition is.

---

