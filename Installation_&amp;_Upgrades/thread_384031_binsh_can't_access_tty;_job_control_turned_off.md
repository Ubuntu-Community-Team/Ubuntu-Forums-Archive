---
title: "/bin/sh: can't access tty; job control turned off"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by smokabul on 2007-03-14
when i installed ubuntu i had disconnected my windows HDD (SATA) and installed ubuntu on my second HDD (also SATA). after my install was complete i went to boot ubuntu it booted fine, so i pluged my windows HDD back into the sata port i unplugged it from and ubuntu get to the loading splash screen then goes to a command prompt and says this :

```
BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) built-in (ash)
Enter 'help' for a built-in list of commands.

/bin/sh : can't access tty; job control turned off
_
```

at this point my pc locks up and i can only power it off or reset it with the reset switch, the keyboard wont respond

---

### Post by wonk-o-matic on 2007-03-14
You have confused grub, I think.  If you had left the Windows drive in place, everything would have worked, probably.  It might be easier to reinstall with the drives in their natural configuration.  

If you can't or won't reinstall, there's some grub magic to renumber the drives.

---

### Post by smokabul on 2007-03-14
thats what i was thinking but it didnt seem like grub since it already boots into ubuntu a little.

but do you know of any kinda of reference i can look at to fix it myself without reinstalling, ive sone some configuring to my ubuntu already that i dont want to have to redo

---

### Post by scxtt on 2007-03-14
as far as grub is concerned, when you installed ubuntu - you put it on hd(0,0) - if you only had one HDD plugged in ... then you plugged in a 2nd drive, most likely 'in front of' the one ubuntu was on - pushing ubuntu from hd(0,0) to hd(1,0) - so if you don't update that for grub, it's unaware ...

do you get to the point where you can edit the grub entry that boots ubuntu?

---

### Post by smokabul on 2007-03-14
i can get to that place i believe

its when grub says press a button to look at the config, correct

---

### Post by scxtt on 2007-03-14
you should be able to press 'e' when you're hovering over an entry ... you probably have to hit 'escape' 1st to get to the grub menu ... in the menu, if you hit 'e' on the menu entry for ubuntu, you'd have something like:

root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

you should only have to edit 'root' ... mine is (hd1,0) because i have 3 drives in my PC:

1. 40G ide drive (hd0,0) [ storage for VMs ]
2. 80G sata drive (hd1,0) [ OS, kubuntu edgy in this case ]
3 160G sata drive (hd2,0) [ storage for files i want to keep, mainly ISOs ]

---

### Post by smokabul on 2007-03-14
ok, so if i edit the boot area in grub it hsould be hd1,0 if my windows drive is ahead of my linux drive on the sata bus?

---

### Post by scxtt on 2007-03-15
yeah, that sounds about right ... i think the grub menu also has an equivalent of "tab-completion", so that can give you some ideas too ...

---

### Post by pradeepadapa on 2007-03-15
even i hav the same problem that says that  /bin/sh:cant access tty'job control turned off

(initramfs)

but i hav only 1 hdd (hd0)

i hav installed it on (hdo,5) but when i press 'e' to edit then it shows like root (hd0,8 ) when i edit that line to root (hd0,5) and boot the above error occurs, 

plse giv an solution...........................

---

### Post by scxtt on 2007-03-15
the generic "solution" would be to try:

(hd0,0)
(hd0,1)
(hd0,2)
...
(hd0,8)

and see if any of them work ... booting a LiveCD and running "sudo fdisk -l" would take the guess work out of it i suppose ...

---

### Post by pradeepadapa on 2007-03-15
my fdisk -l output is 



Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 1275 10241406 7 HPFS/NTFS
/dev/hdc2 1276 9728 67898722+ f W95 Ext'd (LBA)
/dev/hdc5 2551 5100 20482843+ 7 HPFS/NTFS
/dev/hdc6 1276 2366 8763394+ 83 Linux
/dev/hdc7 2367 2550 1477948+ 82 Linux swap / Solaris
/dev/hdc8 5101 7650 20482843+ 7 HPFS/NTFS
/dev/hdc9 7651 9728 16691503+ 7 HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sda: 128 MB, 128974848 bytes
16 heads, 32 sectors/track, 492 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

now what to do nd how to mount the partition frm the live cd, when i try to edit the menu.lst from the live cd its showing an empty menu.lst file .......

---

### Post by scxtt on 2007-03-15
well, it looks as tho you should have a **/dev/hda** and **/dev/hdb** if you've got a **/dev/hdc** ... at any rate, it looks like you should be using (hd2,*) taking into account that:

(hd0,*) = /dev/hda
(hd1,*) = /dev/hdb
(hd2,*) = /dev/hdc
(hd3,*) = /dev/sda

and i'm not sure how your whole "NTFS" and extended partitions will affect the * aspect above ...

but basically you should be able to come up w/ some combination that will boot **/dev/hdc6 1276 2366 8763394+ 83 Linux** ... i've give (hd2,5) a shot 1st then try a few in that range ...

as far as menu.lst goes from the LiveCD - it won't do you any good since you want to edit the menu.lst that is stored on your hard drive (not the space on your RAM the LiveCD uses) ... since you can edit the grub menu when you boot your PC, you don't need to worry about editing that file until you can BOOT your install ...

---

### Post by pradeepadapa on 2007-03-15
no man, ur suggestion didnt work, (hd0,5) is the correct sequence bec atleast it tried to get into
the UBUNTU system but in half of the way an error has occurred stating

**[B][B]/bin/sh: can't access tty; job control turned off**[/B][/B]

---

### Post by pradeepadapa on 2007-03-15
[size=+4] can anyone plse tell me how to sort this problem or i am thinking to reinstall the UBUNTU system [/size]

---

### Post by pradeepadapa on 2007-03-16
hello smokabul , i hav got the same problem as u nd i hav solved the problem by editing the grub boot nd kernel lines, just see the boot line and the kernel line present on ur grub by pressing 'e' to edit those lines......  hav any doubt post it

---

### Post by wpshooter on 2007-03-17
> **pradeepadapa said:**
> [size=+4] can anyone plse tell me how to sort this problem or i am thinking to reinstall the UBUNTU system [/size]

Yes, try using the F4 key to select a specific video mode (one compatible with your graphics card and your monitor).

This worked for me.

Don't ask me why.

I don't think this error has any thing to do with drive but with video modes.

---

### Post by smokabul on 2007-03-18
i still havent worked out my problem, BUT i havent had time to mess with it, im going to do the fdisk thing when i get the time and try and work out my problems

---

### Post by pradeepadapa on 2007-03-18
hello smokabul, just post the output of grub>find /boot/grub/stage1 and also see whether the root at the grub prompt is pointing to the correct drive, even if it doesnt point t the correct drive this error occurs, it has occurred t me nd nw i hav solved it, now my sys is working fine....

---

### Post by smokabul on 2007-03-19
i understand that my grub is pointing to the wrong drive, but im working on getting it to point to my linux partition and my windows partition.

im not using IDE, im using 2 sata HDDs so im thinking i need ot use sda instead of hd0,0 nad such

anyway here is my fdisk output
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19080   153260068+  83  Linux
/dev/sdb2           19081       19457     3028252+   5  Extended
/dev/sdb5           19081       19457     3028221   82  Linux swap / Solaris

```

so im thinking if i point grub to sda1 for my windows partition instead of hd0,0 it should boot fine, as well as poinitng linux to sdb1 instead of hd1,0

if im not correct please let me know

if you cant tell im new to linux. i think im good at problem solving

---

### Post by smokabul on 2007-03-19
i figured out my problem, all i had to do was to make sure my Linux drive was in hd0, it wasn't liking to boot on hd1.

i just changed my sata plugs so that my linux drive was ahead of my windows drive on the bus

---

