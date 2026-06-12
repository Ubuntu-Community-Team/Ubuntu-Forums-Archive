---
title: "GRUB don't see Windows."
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Ussop on 2008-06-08
When I boot there is no option to boot my WinXP. I have 3 partitions. On 
first Ubuntu, 2nd - swap and on 3rd WinXP.

Can anyone help me?

---

### Post by abhiroopb on 2008-06-08
in a terminal (applications>accessories>terminal):

sudo gedit /boot/grub/menu.lst

scroll the the bottom and add this: 
title   Windows XP
root   (hd0,2)
makeactive
chainloader   +1

Save and exit, it should be in grub now.

---

### Post by Ussop on 2008-06-08
Now there is windows option but when selected i get:
Error 12: Invalid device requested.

Before installing Ubuntu i had:
c:\   - now Ubuntu
d:\   - now swap
e:\ DVD
f:\ win

Can it be that 0,2 go to DVD?

---

### Post by abhiroopb on 2008-06-08
ok start up ubuntu, and in a terminal:

sudo fdisk -l

post output here.

The problem is I think I got the partition wrong.

---

### Post by the8thstar on 2008-06-08
Please type in a terminal:

> sudo fdisk -l

to get a list of all the partitions (and therefore OS) recognized by your system, then copy and paste the output into your next answer. This way we can figure out what's going on.

---

### Post by Ussop on 2008-06-08
```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4dc98ad6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6847    54998496   83  Linux
/dev/sda2            6848        6971      996030   82  Linux swap / Solaris
/dev/sda3            6972        9963    24033240    f  W95 Ext'd (LBA)
/dev/sda5            6972        9963    24033208+   7  HPFS/NTFS

```

---

### Post by abhiroopb on 2008-06-08
again in the menu.lst file:
input the followin:

title Windows XP
**root (hd0,3)**
makeactive
chainloader +1

---

### Post by the8thstar on 2008-06-08
Okay, then Grub should be modified as follows:

First, type in the terminal:

> sudo gedit /boot/grub/menu.lst

then scroll to the end and replace the previous Windows entries with this:

> title Windows
root **(hd0,3)**
makeactive
chainloader +1

Tell us how it went.

---

### Post by the8thstar on 2008-06-08
lol, **abhiroopb**. You beat me to it again. At least, two good advices are better than none.

---

### Post by abhiroopb on 2008-06-08
yea as long as its the same thing!!!!

---

### Post by Ussop on 2008-06-08
No love :(

Error 22: No such partition.

---

### Post by the8thstar on 2008-06-08
Is your XP partition (what you called F: )the one where you had the windows directory installed (i.e. f:\windows), or was it the recovery partition?

---

### Post by abhiroopb on 2008-06-08
Ok type this in the terminal:

gksudo gparted

Right click on wherever it says NTFS and click on manage flags, and select wherever it says "boot".

Then in menu.lst change back to:

title Windows XP
**root (hd0,2)**
makeactive
chainloader +1

---

### Post by the8thstar on 2008-06-08
Might be a flag issue, but I'm concerned about the whole windows partition on c: having been wiped during ubuntu install.

---

### Post by Ussop on 2008-06-08
It's install partition with windows files and such.

---

### Post by abhiroopb on 2008-06-08
Try doing what I suggested should work.

---

### Post by the8thstar on 2008-06-08
> **Ussop said:**
> It's install partition with windows files and such.

Okay then, try what **abhiroopb** suggested and let's see how it rolls.

---

### Post by Ussop on 2008-06-08
Error 12

But noticed something interesting in Gparted.
```

/dev/sda3       Extended
  /dev/sda5     ntfs
```

Can it be that i need (0,4)?

---

### Post by the8thstar on 2008-06-08
> **Ussop said:**
> Error 12

But noticed something interesting in Gparted.
```

/dev/sda3       Extended
  /dev/sda5     ntfs
```

Can it be that i need (0,4)?

Typically, yes.

---

### Post by Ussop on 2008-06-08
Changed (hd02) to (hd0,4) and got same error 12.

---

### Post by abhiroopb on 2008-06-08
No no, NTFS is only your third partition, it looks like its the fifth because of the extended partition. Usually the swap should be in the extended partition. I think the extended partition is what is causing the mess. Ok can you delete the windows partition? And re-install? would that be an option for you?

---

### Post by the8thstar on 2008-06-08
At the command prompt type:

> cd /dev/sda5

then 

> dir

and paste the results in here. I want to make sure there IS a living Windows directory there.

---

### Post by Ussop on 2008-06-08
Yes but no. For some reason i can't install windows with Linux present on PC. After pressing any key to boot from CD (install disc) it shows message: Inspecting your hardware configuration... or something like that.
And then go blank.

cd /dev/sda5 gives me communicate that it's not directory.

---

### Post by abhiroopb on 2008-06-08
Why can't you install windows with linux present? All you have to do is put in an XP disc and during setup just select the ntfs partition and it will install there.

---

### Post by Ussop on 2008-06-08
You mean now from Ubuntu?

---

### Post by abhiroopb on 2008-06-08
Ok if you are sure you can re-install windows without losing any data then all you have to do:

First go into gparted (sudo gparted), and erase extended partition. Then create a new partition called NTFS.

Put in the windows CD, restart the computer and install windows to the NTFS partition (the partition which has the "bad" copy of windows).

Then put in the ubuntu livecd and do the following in a terminal:
    sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit
that will reset grub.

Then restart and you should load into ubuntu.

Then tell us what it shows on gparted.

---

### Post by Ussop on 2008-06-08
It works now. Thank you.

Still, drive letter bothers me, is there a way to change f: to c: ?

---

### Post by abhiroopb on 2008-06-08
managed to do all of that in under an hour? impressive :P! 

The drive letters only appear in Windows right? Not much of an expert on windows, I'm sure its possible but it MIGHT cause problems in ubuntu.

---

