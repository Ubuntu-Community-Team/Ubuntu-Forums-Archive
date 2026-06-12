---
title: "Grub2 problems with windows Seven"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by Aqlor on 2011-02-07
After having problems with grub2 and windows seven and being forced to reinstall both windows and Lubuntu, I got grub to work.

So after some hours of work, everything is working fine.

Today, I was trying to use windows again and windows is no longer listed on grub.

What can I do to keep it permanently on the list?

Thank you,
Manuel Levi

Ps: I've already read lots and lots of threads about problems with grub2, if it works so bad (maybe it's a problem with windows seven only) why is it being more and more used?

Edit: Actually I was an idiot speaking like that before, the problem was mine and mine only :P

---

### Post by Quackers on 2011-02-07
Once a Windows entry has appeared in the grub menu it shouldn't disappear again. This can be caused by a program installed within Windows which writes to the mbr of the hard drive. I believe the most common culprits are Dell's Data Safe, Photoshop and some anti-virus programs (most likely ones with root-kits, as I understand it), but there are others.
Do you have any of these installed in Windows?

---

### Post by Aqlor on 2011-02-07
I don't remember having installed anything on windows but **steam** (that is the only reason I use windows for) however, I have booted windows after this...

I've tried update-grub and no windows partition are recognized so it probably is what you just said, a change on windows' mbr. 

Do you know any way to restore it?

---

### Post by Quackers on 2011-02-07
See if anybody else has anything further to add, but to fix it I would suggest you re-install grub from the live cd.
Look below for details. 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by oldfred on 2011-02-07
I have seen some Lubuntu's without the osprober to find other systems to boot. I guess the assumption is if you have to run Lubuntu your system does not have to power to run other systems anyway.

If you do this, does it update?
```

sudo update-grub
```

---

### Post by Aqlor on 2011-02-07
Hello,

I've tried before to use the update-grub command, nothing changed.

Quackers, I've "completed" the guide you sent, nothing changed either. Even tried to get onto lubuntu again and run update-grub, still the same problem, Windows is not recognized...

---

### Post by Quackers on 2011-02-07
So Lubuntu is booting ok, but Windows doesn't appear in grub menu, but it did at one time?
Please go to System > Admin > Synaptic package manager. In the search box enter os-prober. It will appear in the main window. When it does, is there a green box next to it (in other words, is it installed)?
If not, please install it and then run sudo update-grub in the terminal.

---

### Post by Aqlor on 2011-02-07
That worked perfectly!

```

levi@laptop:~$ sudo apt-get install **os-prober **
[sudo] password for levi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  os-prober
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.0kB of archives.
After this operation, 184kB of additional disk space will be used.
Get:1 http://pt.archive.ubuntu.com/ubuntu/ maverick/main os-prober i386 1.39 [23.0kB]
Fetched 23.0kB in 0s (38.4kB/s)
Selecting previously deselected package os-prober.
(Reading database ... 144293 files and directories currently installed.)
Unpacking os-prober (from .../os-prober_1.39_i386.deb) ...
Setting up os-prober (1.39) ...

```

```
levi@laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
**Found Windows 7** (loader) on /dev/sda1
done
```

I haven't tried to reboot this yet but I am marking it as Solved already! **Thanks a lot Quackers!**

(actually I've read about the os-prober before and I **thought** I had it installed)

---

### Post by Quackers on 2011-02-07
Glad that seems to have gone well :-)
Lubuntu has installed a number of times for people without installing os-prober, as oldfred stated earlier. It has also happened with Ubuntu I believe, but rarely. It is curious though that Windows appeared in the grub menu at some time previously. Maybe an update did something nasty to os-prober - just guessing.

---

### Post by Aqlor on 2011-02-07
Maybe that was the problem...

**Thread Unrelated :**

I had some nasty problems when installing lubuntu, but I think it was more a problem about the installer than anything else.

I was trying to see if the installer would let me have my home folder encripted and at the same time enter with my user automatically, well, it did let me do that and as expected lubuntu didn't work correcly :P another problem was with the keyboard layout, if I recall correctly I set the password on the installer using my country's layout and when I tried to login I was using the USA layout or the contrary, I don't know.

Anyway, now everything seems to go smoothly - thanks to you - and I am hoping it continues that way :D

---

### Post by Quackers on 2011-02-07
Have fun :-)

---

