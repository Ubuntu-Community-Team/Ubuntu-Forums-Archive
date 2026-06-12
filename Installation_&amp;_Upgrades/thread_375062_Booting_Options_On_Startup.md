---
title: "Booting Options On Startup"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by ComputerGuy56 on 2007-03-03
On startup I get about 6 choices, I'm confused about half of them. The options are:
Ubuntu, kernal 2.6.17-11-generic
Ubuntu, kernal 2.6.17-11-generic (recovery mode)
Ubuntu, kernal 2.6.17-10-generic
Ubuntu, kernal 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems: (Not a choice)
Microsoft Windows XP Home Edition

I just installed Ubuntu on a second hard drive, so I have WinXP on one hard drive and Ubuntu on the other. Also, I updated Ubuntu with about 136 updates(I think that what it said).
My questions are:
What's recovery mode?
Why do I have two Ubuntu versions(Yes, I updated, I think that's why)
What's the memtest86+ thing?

System Specifications:
1.7 GHz Intel Celeron Processor
256 MB RAM
40 GB Hard Drive(WinXP)
30 GB Hard Drive(Ubuntu)

By the way, I just somehow got Ubuntu to install and I LOVE it.:lolflag:

---

### Post by wavesound on 2007-03-03
Ubuntu, kernal 2.6.17-11-generic
Ubuntu, kernal 2.6.17-11-generic (recovery mode)
Ubuntu, kernal 2.6.17-10-generic
Ubuntu, kernal 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems: (Not a choice)
Microsoft Windows XP Home Edition


************************************


Hi
The top one is the deafult to boot,  Ubuntu, kernal 2.6.17-11-generic,
( normally after 20 sec, or hit enter)

If you want your XP
just scroll ( arrow down) and hit enter.

You've got two kernals on here and two recovery modes

Hope this helps
Bob
:)

---

### Post by ComputerGuy56 on 2007-03-04
Do I need 2 kernels?

---

### Post by wavesound on 2007-03-04
No.

Although a lot of people on here would suggest you keep them.

If you just comment out the last few they wont show up at boot up.

Always there for later if you run into problems ( you can sometimes boot an older kernel when your new one stops, If it stops!)


I tend to use the last two and then delete the older ones.  :) 

Cheers
Bob

---

### Post by steveyos666 on 2007-03-04
Might as well ask this here... Is there any way to make XP the one that starts up if you don't go to it and hit enter after five or so seconds? I hate accidentally starting up Ubuntu because I mainly use XP since I can't get Ubuntu's wireless working.

---

### Post by wavesound on 2007-03-04
Yeah Dead easy
open up the menu.lst
copy the XP bit and put it at the top obove your first LInux kernel thing.
Then when you boot XP will be default.
I've just got both working on this box and find XP seems to hang around doing things!!

Cheers
Bob

---

### Post by ComputerGuy56 on 2007-03-04
I'm a huge noob on Ubuntu. Where do I find Menu.lst if Ubuntu is installed... Do I just go into file system and look for it?

---

### Post by steveyos666 on 2007-03-04
Yeah man can you inform us where this menu.list is? heh :p

---

### Post by Herman on 2007-03-05
Hello,> I'm a huge noob on Ubuntu. Where do I find Menu.lst if Ubuntu is installed... Do I just go into file system and look for it?> Yeah man can you inform us where this menu.list is? hehIf you fellows click on my 'GRUB Boot Loader Page' sig link right under this post, you will get a web page that will introduce you to the grub boot loader in Ubuntu. It has lots of illustrations and I think it is explained in very simple terms that anyone can understand. If you have any difficulties with it or queries, please ask me and I will do my best to explain and possibly update the page to make it clearer. (Just add another post below this thread and I will see it and answer your question).

It is okay to copy your Windows entry and paste it above the top of the debian automagic kernels list. 

Please don't paste your Windows entry immediately above the kernel entries for Ubuntu, which are inside the automagic kernels list. If you do then they will be automagically deleted each time you receive a kernel update for Ubuntu.

Enjoy your grub bootloader and have fun with Ubuntu,
Regards, Herman :)

---

### Post by steveyos666 on 2007-03-05
I'm not sure if I count the other operating systems as a line or not, but I'm gonna try it now and see what happens...


Hey it worked beautifully :) Thanks man

---

### Post by brightscreamer on 2007-10-20
I still don't get it...why so many kernels? Upon upgrading, do the old ones stay there? Should they be deleted? How much space do they take up? Geeze..this has me so confused!

---

### Post by Herman on 2007-10-20
> I still don't get it...why so many kernels? Upon upgrading, do the old ones stay there? Yes.
 > Should they be deleted? No.
 > How much space do they take up? Hardly any.  
I do know the ones we use in Ubuntu are a bit too big to fit on a floppy disk.  I have read old how-tos about copying other kernels to floppy disks, so some kernels must be small enough. Anyway, that amount of hard drive space is negligible these days when most of us have such nice big hard drives. 
> Geeze..this has me so confused!Just relax and don't worry about it. 
It's nothing to get worked up about, really. It's just that things keep improving, new hardware is invented, programmers have new ideas, there are better ways to do things than in the past, and so on. New kernels are often necessary for things to go ahead. You know, it's called "Progress!" :)

Sometimes (it's rare but it could happen), an new kernel might not suit a particular computer's hardware, or there might be some other problem with a new kernel, so it's a good idea to keep your older kernels just in case.
Usually the newest kernel will be the best though.

If you don't like seeing them listed in your GRUB menu, you can alsways just 'comment them out' in your /boot/grub/menu.lst file, like this, 
```
#title        Ubuntu, kernel 2.6.15-23-386
 #root        (hd0,1)
 #kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
 #initrd        /boot/initrd.img-2.6.15-23-386
 #savedefault
#boot
                                                                                  
 #title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
 #root        (hd0,1)
 #kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
 #initrd        /boot/initrd.img-2.6.15-23-386
 #boot
```See? You place a 'hash' mark in front of the lines you want to make invisible, and they won't appear in your GRUB menu. They'll still be there and you can uncomment them and use them again if you ever need them.

Regards, Herman :)

---

### Post by brightscreamer on 2007-10-20
Thanks, Herman! Those are exactly the kind of answers I was looking for!

---

### Post by Herman on 2007-10-20
:) Okay, good, I'm pleased to have been able to help you. :)

---

