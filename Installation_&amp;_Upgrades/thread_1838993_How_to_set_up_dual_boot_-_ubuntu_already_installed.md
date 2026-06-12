---
title: "How to set up dual boot - ubuntu already installed"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by brightlights on 2011-09-04
Hello,

I'm sure that this has been asked before but I couldn't find any instructions for this.

I have 2 hard disks: I already have Windows 7 installed on one hard disk, and ubuntu natty on the other hard disk.

How do I install GRUB without overwriting the MS Windows MBR?

Also, doesn't grub ask you to create partitions? I don't want to mess with partitions - just want separate OS's on separate hard disks.

Thanks

---

### Post by oldfred on 2011-09-04
Are you installing another copy of Ubuntu or other system that uses grub2 on the Ubuntu drive? If so just unplug the Windows drive as the most sure way. 

But if you partition in advance and then use manual install you get the choice of which drive to install Ubuntu to. If a second install you may want to just throw away the second install of grub2. Ubuntu does not give a choice to not install, so you just install to the partition with Ubuntu that you just installed. It will not be used as you use the grub2 boot loader from the first install.

Lots of detail in Herman's site:
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by brightlights on 2011-09-04
Sorry if I'm being obtuse. 

Do I need to re-install ubuntu to set up dual booting? I would rather not re-install ubuntu to my second hard disk, because it is already installed. Is this the only way?

Upon bootup I just want the option of whether to boot in Windows (on hard disk 1) or Ubuntu (on hard disk 2).

---

### Post by YesWeCan on 2011-09-04
If Ubuntu boots then grub is already installed. In Ubuntu [COLOR="Navy"]run sudo update-grub[/COLOR] to give you a menu with choice of Ubunt or Windows.

If you cannot boot Ubuntu by booting the Ubuntu disk, then boot live CD
[COLOR="navy"]sudo fdisk -l[/COLOR]
to verify the name and partitions of your Ubuntu drive

[COLOR="Navy"]sudo mount /dev/sdxy /mnt[/COLOR]
where x is Ubuntu drive letter and y is Ubuntu root partition

[COLOR="navy"]sudo grub-install --root-directory=/mnt /dev/sdx[/COLOR]

---

### Post by brightlights on 2011-09-05
YesWeCan - thank you!

I feel like a noob (and I am). All I had to do was run the 'sudo update-grub' command, and now I have an option of which OS to boot upon startup!

Ubuntu is amazing! :D

---

