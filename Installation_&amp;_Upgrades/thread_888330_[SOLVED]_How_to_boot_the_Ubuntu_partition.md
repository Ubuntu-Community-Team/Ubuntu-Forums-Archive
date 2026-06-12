---
title: "[SOLVED] How to boot the Ubuntu partition?"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by Hark0 on 2008-08-13
Hi all,

Completely new to Linux and Ubuntu. I created the 8.04 live CD and attempted the dual install with XP. Unfortunately, I didn't check that the CD was error-free (it wasn't), and the installation choked after creating the Ubuntu partition.

I created a new live CD, checked it error-free, and thought I was installing it to the new Ubuntu partition, partition 1. Unfortunately, I instead overwrote and erased the Windows installation entirely.

Fortunately, I was at least smart enough to back up Windows right before the installation, so I lost no data, though a bit of time restoring Windows after I used the partitioner on the live CD to create two fat32 partitions, and GPartEd in Ubuntu to resize them. I re-installed XP Professional to partition 3 (the e: drive) successfully, leaving the other fat32 partition as partition 2 (the c: drive). 

The trouble now is that I simply do not know how to mount the Ubuntu partition. Upon starting the computer, I only get XP on the boot menu. I see in a few places like [here]("http://techiegeekuk.blogspot.com/2007/11/dual-boot-xp-and-ubuntu-710-via-bootini.html") that it's possible to edit the Windows boot menu to list GRUB as an option, but it requires me to mount the Ubuntu partition to retrieve the menu.lst file. Again, I am new to Linux and have no idea how to mount it when I start or restart the machine.

Can someone here tell me what I need to do to start Ubuntu when my computer powers up?

Cheers,
Hark0

---

### Post by coffeecat on 2008-08-13
It's a bit difficult to work out what's happening, so a little bit more information please.

First - 

[quote=Hark0]Upon starting the computer, I only get XP on the boot menu[/quote]

If that's a grub menu, that means that something has edited the menu, and nothing you've done could have done that. Which makes me suspect this is not a grub menu, but some Windows thing. Can you describe the appearance of the menu a bit more?

[quote=Hark0]I see in a few places like [here]("http://techiegeekuk.blogspot.com/2007/11/dual-boot-xp-and-ubuntu-710-via-bootini.html") that it's possible to edit the Windows boot menu to list GRUB as an option[/quote]

You probably don't want to go down that road just now. :(

:wink:

Boot up the live CD, and when you get to the desktop, open a terminal (Applications > Accessories) and post the output of:

```
sudo fdisk -l
```(That's a lower-case L, not one). That way we'll see exactly what your partition structure is. If the Ubuntu partition is still there, all you should have to do is to reinstall grub to the MBR. That's easy enough, but we need to know where the Ubuntu partition is. By the way, you can paste and copy from the terminal into the message field of firefox - saves you retyping all that stuff - but be careful: the keyboard shortcuts are different. In the terminal, add shift to ctrl-C or ctrl-V or whatever - or look in the edit menu.

It would also be useful to see the contents of menu.lst. While in the live environment, have a look in Gparted (if you're not comfortable with reading fdisk) to see which is the Ubuntu root partition, and then go to Places > Computer and double-click on the partition icon. Now navigate to /boot/grub. Double-click on menu.lst and it should open in read-only mode in a text editor where you'll be able to copy and paste into firefox.

Assuming, of course, that you have internet connectivity in the live CD. :?

---

### Post by SkonesMickLoud on 2008-08-13
Windows most likely wrote over your MBR, which it tends to do if you install it after installing XP.

All you need to do is follow the instructions here:

[http://ubuntuforums.org/showthread.php?p=5565706#post5565706](http://ubuntuforums.org/showthread.php?p=5565706#post5565706)

You only need to worry about the stuff after "If not, in a terminal".  You can do the other stuff, but it's not necessary.

---

### Post by sandysandy on 2008-08-13
here is a nice thread on how to re-install GRUB

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

when u reinstall XP, it will overwrite the MBR with its own bootloader. re-installing the GRUB from live ubuntu CD (see thread link above) will get GRUB back on the MBR and u should be able to boot both windows and Ubuntu.

regards

---

### Post by Hark0 on 2008-08-13
Thanks to all for the replies!

[QUOTE=coffeecat]If that's a grub menu, that means that something has edited the menu, and nothing you've done could have done that. Which makes me suspect this is not a grub menu, but some Windows thing. Can you describe the appearance of the menu a bit more?[/QUOTE]

It was the Windows boot.ini menu, sorry not to have clarified that. Start Grub appeared in it because before posting in this forum I first tried to install WinGrub to solve this problem as described [here]("http://users.bigpond.net.au/hermanzone/p9.html"), with no luck ("missing or corrupt hal.dll file when selecting Grub").

Below are the results of the fdisk query on the terminal:```


Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1459    11719386   83  Linux
/dev/sda2   *        1460        4023    20595330    b  W95 FAT32
/dev/sda3            4024        9324    42580282+   7  HPFS/NTFS
/dev/sda4            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 130 MB, 130220032 bytes
5 heads, 50 sectors/track, 1017 cylinders
Units = cylinders of 250 * 512 = 128000 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     3112544     7678583   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(3112543, 3, 9)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(7678582, 0, 39)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      674759     8418872   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(674758, 0, 23)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(8418871, 0, 12)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     7479526    15223639   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(7479525, 4, 16)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(15223638, 3, 7)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1    14548906  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(14548905, 4, 46)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a205f0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          26      204819+  ee  EFI GPT
/dev/sdc2              26        9134    73161964   af  Unknown
/dev/sdc3            9134       14593    43851488+   7  HPFS/NTFS
```

[QUOTE=SkonesMickLoud and sandysandy]Reinstall grub to the MBR...[/QUOTE]

I have done so according to the procedures linked to, thank you. I am now able to boot Ubuntu, thank you (in fact, am typing this from there now).

However, the computer now boots directly to Ubuntu without first presenting a grub menu showing Windows. When I hit Esc during Grub loading, these are the operating systems presented on the menu:


```
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, kernel, memtest86+
```

So now I seem to have the opposite problem to the one I started with: the XP partition is not accessible.

Can anyone help with this? :lolflag:

---

### Post by SkonesMickLoud on 2008-08-13
> **Hark0 said:**
> Thanks to all for the replies!

<snip>

So now I seem to have the opposite problem to the one I started with: the XP partition is not accessible.

Can anyone help with this? :lolflag:

Add this to the end of your menu.lst:

```
title		Windows 95/98/NT/2000
root		(hd0,1)
makeactive
chainloader	+1
```

If "root (hd0,1)" for some reason doesn't work for you, try setting it to "root (hd0,2)".

If you want the grub menu to come up be default, find the line that says:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

And comment out the third line by adding a #.  So, it'll look like this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

It'd also be a good idea to change the default timeout value too.  If you go right above the "hiddenmenu" section, you should see "timeout 3".  This is the amount of time, in seconds, that grub waits for input from you before selecting the default entry.  I personally set this to "10", but it's entirely up to you.

---

### Post by sandysandy on 2008-08-13
u would have to edit the menu.lst file and put the windows entry manually there.

take backup of menu.lst file before doing changes.

regards

---

### Post by Hark0 on 2008-08-13
You people rock! I followed all of SkonesMickLoud's instructions and it works like a champ now, the boot menu appears now for ten seconds with Windows at the bottom of the list, no problems booting into it or Ubuntu when choose them.

So, I'm basically now where I wanted to be a day and a half ago when I burned the first faulty live cd. Live and learn!

Thanks again!

:guitar:

---

### Post by coffeecat on 2008-08-13
> **SkonesMickLoud said:**
> Add this to the end of your menu.lst:

```
title        Windows 95/98/NT/2000
root        (hd0,1)
makeactive
chainloader    +1
```If "root (hd0,1)" for some reason doesn't work for you, try setting it to "root (hd0,2)".

No, definitely: "root (hd0,2)"

Your output of fdisk shows your Windows partition to be:

```
/dev/sda3            4024        9324    42580282+   7  HPFS/NTFS
```... and sda3 in grub-speak is (hd0,2).

To edit menu.lst, open a terminal and:

```
gksudo gedit /boot/grub/menu.lst
```[B]

Edit:[/B] We posted simultaneously, but I'll leave this up anyway. I'm glad it's fixed.

---

### Post by Hark0 on 2008-08-13
> **coffeecat said:**
> No, definitely: "root (hd0,2)"

Your output of fdisk shows your Windows partition to be:

```
/dev/sda3            4024        9324    42580282+   7  HPFS/NTFS
```... and sda3 in grub-speak is (hd0,2).

To edit menu.lst, open a terminal and:

```
gksudo gedit /boot/grub/menu.lst
```[B]

Edit:[/B] We posted simultaneously, but I'll leave this up anyway. I'm glad it's fixed.

Thanks coffeecat. At first, I second-guessed like the n00b I am and typed (hd0,3) in the menu.lst file, since, I equated that with sda3. That was a spectacular fail on bootup, so I went back in and typed what Skones advised in the first place, (hd0,1). That does seem to work. :confused: But not complaining by any means, mind. :)

---

### Post by coffeecat on 2008-08-13
> **Hark0 said:**
> (hd0,1). That does seem to work.

On looking at your fdisk output again, yes it would. Sorry for the muddle in my thinking. :|

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1459    11719386   83  Linux
/dev/sda2   *        1460        4023    20595330    b  W95 FAT32
/dev/sda3            4024        9324    42580282+   7  HPFS/NTFS
```I missed the * under the boot flag, which of course makes sda2 (hd0,1) the partition Windows boots from. I simply looked for the NTFS partition, which was wrong. Clearly, you've got an unusual Windows setup there. But as long as it works. :)

---

### Post by Hark0 on 2008-08-13
> **coffeecat said:**
> ...Clearly, you've got an unusual Windows setup there. But as long as it works. :)

I used the livecd partitioner to create two fat32 partitions, one 20 GB (the hd0,1) partition, and one larger (hd0,2). I did this as I'd read elsewhere on the web that Windows and Ubuntu could both access fat32, but Ubuntu could not access NTFS. I installed Windows on the larger partition, which converted it to NTFS, assigned it drive letter E:, and placed the system files there. However, as you see, it assigned the fat32 partition drive letter c: and made it the Windows boot partition.

I have since learned that Ubuntu 8 is quite capable of accessing NTFS files; I just imported my music from the NTFS partition and am now listening to my tunes with Rhythmbox. So there was absolutely no need for the fat32 partition. Oy.

So, from a Windows point of view, I have a 20 GB C: drive which serves no other function than to boot Windows, and a ~40 GB E: drive which contains the system, applications, and data. I do have plenty of unused space  on the E: partition though, so that's not a worry.

It is, as you say, an unusual setup, and I'm not entirely happy with it, but I've stressed enough the past two days and will live with it for now.

:)

---

### Post by SkonesMickLoud on 2008-08-13
> **Hark0 said:**
> I used the livecd partitioner to create two fat32 partitions, one 20 GB (the hd0,1) partition, and one larger (hd0,2). I did this as I'd read elsewhere on the web that Windows and Ubuntu could both access fat32, but Ubuntu could not access NTFS. I installed Windows on the larger partition, which converted it to NTFS, assigned it drive letter E:, and placed the system files there. However, as you see, it assigned the fat32 partition drive letter c: and made it the Windows boot partition.

I have since learned that Ubuntu 8 is quite capable of accessing NTFS files; I just imported my music from the NTFS partition and am now listening to my tunes with Rhythmbox. So there was absolutely no need for the fat32 partition. Oy.

So, from a Windows point of view, I have a 20 GB C: drive which serves no other function than to boot Windows, and a ~40 GB E: drive which contains the system, applications, and data. I do have plenty of unused space  on the E: partition though, so that's not a worry.

It is, as you say, an unusual setup, and I'm not entirely happy with it, but I've stressed enough the past two days and will live with it for now.

:)

Glad you got everything working!  There are ways to resize your partitions, but I know where you're coming from with the just being happy that it works.  Consider it a chore for another day.

If you would, please mark this thread as solved.  Just click on "Thread Tools" and "Mark as solved."  You can always bump the thread later if you need more help.

---

