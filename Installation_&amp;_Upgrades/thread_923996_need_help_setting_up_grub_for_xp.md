---
title: "need help setting up grub for xp"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by crosmanrond on 2008-09-19
ok, i've been playing with this all day.
i had win xp installed, i installed ubuntu.

my hard drive config is(from linux's view):

hd0 80gb sata(ubuntu + swap + share)
hd1 320gb sata(windows xp)

and from xp(last i used it)
C:/ sata 320gb
D:/ sata 80gb(empty because this was before install of linux)

now at first i didn't have xp on the grub menu, so i added this(in various forms) to my /boot/grub/menu.lst:

title Windows
root (hd1,0)
save default
make active
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

i know the root is correct but everything else i just put on cause i was told to...

so now when i try to boot to windows from grub i get(aprox):
starting up...

ntldr is missing...

press ctrl+alt+del to restart

i've tried things on other threads here on the forums but nothing seems to work..

thanks in advance

---

### Post by Herman on 2008-09-19
```
title Windows
root (hd1,0)
save default
make active
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
``````
title Windows
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```That basically looks okay, but you have a couple of syntax errors there, it's important to type these commands in exactly. 
There is no space between 'save' and 'default' in 'savedefault. 
There is no space between 'make' and 'active' in 'makeactive'.
Would that be the trouble or is there something else wrong? 

I can't 'see' anything else wrong, from the information you have given. 
The pair of 'map' commands mean you don't need to edit boot.ini to tell it you have Windows on a non-first hard disk. 
The error 'NTLDR is Missing', is often an indication that boot.ini needs editing with the correct hard disk and partition number.
If seems that your GRUB is chainloading Windows's boot sector okay.
What does the output from 'sudo fdisk -lu' loook like?
```
sudo fdisk -lu
```

---

### Post by crosmanrond on 2008-09-19
nope, still the same error

here's the output of fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   136713149    68356543+  83  Linux
/dev/sda2       136713150   148424534     5855692+  82  Linux swap / Solaris
/dev/sda3       148424535   156232124     3903795    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2b346dfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625121279   312560608+   7  HPFS/NTFS

---

### Post by Herman on 2008-09-19
:) Thank you for the fdisk -lu output.
Now I'm sure there's nothing wrong with your GRUB settings. GRUB is finding your XP boot sector okay, but there seems to be some kind of a problem in your Windows XP booting arrangement.
The problem is, due to security settings, we can't easily edit your /boot.ini file from Ubuntu in order to fix it. First you would need to boot XP and relax the security settings, so you're in a catch22 situation.

You can do one of two things.

1. If you have a Windows XP Installation CD, you can boot into the [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and run the '*bootcfg /rebuild* ' command. That command is for automatically fixing a corrupted boot.ini file or making a brand new one if one doesn't already exist.

OR

2. []("http://tinyempire.com/notes/ntldrismissing.htm")A website that is extremely helpful when Windows XP is impossible to chainload is this one, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm") by Miles Comer. 
You can download boot discs from this site that contain the the three vital Windows XP boot loader files (ntldr, ntdetect.com and boot.ini).
The boot.ini file in this CD is a generic version which will give you a boot menu so you can try to boot Windows as partition 1, 2 ,3 or 4 in the first hard disk, or partition 1, 2 ,3 or 4 in the second hard disk. In other words it's something like a Windows equivalent of Super Grub Disk.
If that doesn't boot your Windows I don't know what will!

---

### Post by Herman on 2008-09-19
Just in case you don't know how to get to your boot.ini file in Windows XP or how to change the file permissions so you can edit it, here is a link explaining one way to do that, [A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")...showing the important files needed for booting.

Sometimes Windows automatically deletes it's vital boot loader files, such as NTLDR, so you should check to see if they are in fact there or not.
Windows does that when you set up a dual boot with another Windows. Normally, it would give Windows XP's files to Windows 98, if you had Windows 98 installed before Windows XP.
The work-around is to have GRUB or a partition editor mark the existing Windows partition 'hidden' before installing the second Windows OS.
Vista is even worse, it will even give up it's boot loader files to another Windows installation on another hard drive, and does so in spite of a partition being 'hidden', at least that's what I have read.

If you can't find your vital boot loader files, you can copy them from the CD from Miles Comer's site and that will fix your Windows XP. Just edit the boot.ini to make it show only the booting line you need.

---

### Post by crosmanrond on 2008-09-21
ok, i can now boot to windows via disk(the non-windows one(ntldrfix or somthing like that)) but still can't boot to win via grub

---

### Post by Herman on 2008-09-22
Okay then, first, check to see if you have the files NTLDR, NTdetect.com and boot.ini in the root of drive C:.
You can do that easily from Ubuntu. After booting either Ubuntu or your Ubuntu Live CD, mount your Windows partition [like this]("http://users.bigpond.net.au/hermanzone/p10.htm#Click-Icon_Mounting"), and take a look.
It should look something like this, [A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")...you should be able to see those important files needed for booting: NTLDR, NTdetect.com and boot.ini.

Is NTLDR really missing?
If it is in fact there, then your problem is just that Windows can't find it, you just need to tell Windows where it is by editing the boot.ini file.

If NTLDR, NTdetect.com and boot.ini really are missing, then just copy the ones on that CD and paste them into the root of drive C: and you'll be able to boot again.

---

### Post by crosmanrond on 2008-09-22
yay! adding boot.ini, ntdetect.com, and ntldr to C:\ again(though i never saw them before(which is odd)) worked, though now i see a OS select screen from windows after grub...if anyone knows how to fix that let me know(though i can probably get it on my own)

thanks!

---

### Post by Herman on 2008-09-23
When there is more than one booting choice, listed in boot.ini, you are presented with a menu at boot-up so you can choose either how you want to boot, or what operating system you want to boot, as the case may be.
In this instance, the boot.ini file you copied is a special one, edited to give you the chance to choose Windows in the 1st, 2nd, 3rd, or 4th partition and in the 1st or 2nd hard disk.
You probably don't need all those choices.
Removing all but one operating system entry should mean the menu won't show anymore.

A standard boot.ini file might look something a little more like this one,
```
[boot loader] 
timeout=30 
default=multi(0)disk(0)disk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)disk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
```You should be able to edit the your new boot.ini file to be something similar to the one shown above. You can change the title of the operating ssytem to suit yourself, of course, (for example if yours is Windows XP Professional or something else like that).

---

