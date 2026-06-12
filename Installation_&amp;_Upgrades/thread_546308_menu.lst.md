---
title: "menu.lst"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by hackxxcrack on 2007-09-08
I am trying to configure menu.lst to run a Diferent Linux Os, here is what i have:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Famelix .:Hasta La Vista:.
root		(hd0,4)
savedefault
makeactive
chainloader	+1[/B]--->this is the one i want to put

Where is my mistake? 

Thank you

---

### Post by Pumalite on 2007-09-08
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst (complete)

---

### Post by hackxxcrack on 2007-09-08
But when i do that it stays the same way and when i trie to boot the OS it cant...

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title Famelix .:Hasta La Vista:.
root (hd0,4)
savedefault
makeactive
chainloader +1

[B]i think my problem is this part_
# on /dev/sda5

and this one 

root (hd0,4)

i dont know if exactly what do i have to put there could you help me?[/B]

---

### Post by llamakc on 2007-09-08
I've never seen the chainloader line on a Linux distro, and never used it for anything other than Windows.

---

### Post by Pumalite on 2007-09-08
Sorry, but you have to explain better what's going on. I have trouble understanding your problem and therefore is hard for me to help you.

---

### Post by llamakc on 2007-09-08
I agree with Pumalite.

OP: Do you know how to view the Grub menu at boot? Hit the escape key. Use the arrow keys to arrow down and choose the O/S you want to load.

---

### Post by rsambuca on 2007-09-08
I use chainloading for all of my distros, so I don't have to keep messing with grub after kernel updates.  The menu.lst you have will work, PROVIDED that you had the new distro on sda5 install the grub to the /boot folder on that partition.

EDIT:  I don't put the savedefault and makeactive lines in mine, though.

---

### Post by hackxxcrack on 2007-09-08
> **rsambuca said:**
> I use chainloading for all of my distros, so I don't have to keep messing with grub after kernel updates.  The menu.lst you have will work, PROVIDED that you had the new distro on sda5 install the grub to the /boot folder on that partition.

how can i install the grub to the boot folder?

---

### Post by llamakc on 2007-09-08
> **rsambuca said:**
> I use chainloading for all of my distros, so I don't have to keep messing with grub after kernel updates.  The menu.lst you have will work, PROVIDED that you had the new distro on sda5 install the grub to the /boot folder on that partition.

EDIT:  I don't put the savedefault and makeactive lines in mine, though.

I wasn't aware of that. I'll go read up on what chainloading does. Since I use the kernel-image packages my menu.lst is always automatically updated. I have recently recompiled a kernel and didn't realize chainloading was helpful.

Thanks for the info.

---

### Post by Pumalite on 2007-09-08
Hey, rsambuca:
If this is a chainloader, don't you think the original grub is already installed somewhere else?

---

### Post by llamakc on 2007-09-08
> **hackxxcrack said:**
> how can i install the grub to the boot folder?

What you really need to do is provide the layout of your disks. Copy/paste the output of 

sudo fdisk -l

---

### Post by merlinus on 2007-09-08
sudo fdisk -l

---

### Post by Pumalite on 2007-09-08
That's what I first asked for

---

### Post by merlinus on 2007-09-08
You expect to get what you ask for???

You must live in L.A. (la-la land).

:popcorn:

-merlin

---

### Post by hackxxcrack on 2007-09-08
> **Pumalite said:**
> That's what I first asked for

I dont understand , when i do that it just gives me my drive info, what i want to do is to start famelix, that is a linux distro  but when i reboot my pc it doesnt starts, or it doesnt shows at the start menu

---

### Post by merlinus on 2007-09-08
You had best give what is asked for.

We need to know your drives and partitions before we can help.

Get with the program!

-merlin

---

### Post by Pumalite on 2007-09-08
Plug in a Live CD then, mount your partition and then do what we asked in the terminal.

---

### Post by Pumalite on 2007-09-08
> **merlinus said:**
> You expect to get what you ask for???

You must live in L.A. (la-la land).

:popcorn:

-merlin

All the time. You are right, I cannot complain.

---

### Post by llamakc on 2007-09-08
> **hackxxcrack said:**
> I dont understand , when i do that it just gives me my drive info, what i want to do is to start famelix, that is a linux distro  but when i reboot my pc it doesnt starts, or it doesnt shows at the start menu

Give us the information. What is the deal with not following suggested directions?

---

### Post by Pumalite on 2007-09-08
We are anxiously awaiting

---

### Post by rsambuca on 2007-09-08
OK guys, just to clarify.  (I don't know if this is the best way, but after trying different methods this is what I prefer)  This is what I do...

1.  Install you first distro, have grub setup to the mbr.

2.  Install your second distro, (to sda2, for example).  Have the grub for this installer setup on sda2.  Then add the chainloader to the first distro's menu.lst

3.  Install distro3 on sda3.  Have its grub setup to sda3.  Then add the chainloader to the first distro's menu.lst.

The benefit to this method is that if distro2 or 3 updates the kernel, you don't have to worry about reconfiguring any grub menu.lst files, as that should all be automatic.

The downside is that you hop from grub to grub.  This hasn't been a big deal for me.  For example, the last part of my menu.lst looks like this:```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
#savedefault
makeactive
chainloader     +1

title           Ubuntu 32-bit
root            (hd2,5)
chainloader     +1


title           Gentoo
root            (hd2,6)
chainloader     +1


title           Debian
root            (hd2,7)
chainloader     +1

title           Sabayon Linux
root            (hd2,8)
chainloader    +1

```

---

### Post by hackxxcrack on 2007-09-08
> **Pumalite said:**
> We are anxiously awaiting

My disk info is:

Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1        1424    11438248+   7  HPFS/NTFS

/dev/sda2            1425        6713    42483891+  83  Linux

/dev/sda3            6714        8414    13663282+   5  Extended

/dev/sda4   *        8415        9729    10562737+  83  Linux

/dev/sda5            6714        8414    13663251   83  Linux

i want to select to start from the sda1 to the sda5

thank you all

---

### Post by Pumalite on 2007-09-08
So, you have to change (hd0,4) to (hd0,3), and sda5 to sda4

---

### Post by Pumalite on 2007-09-08
> **rsambuca said:**
> OK guys, just to clarify.  (I don't know if this is the best way, but after trying different methods this is what I prefer)  This is what I do...

1.  Install you first distro, have grub setup to the mbr.

2.  Install your second distro, (to sda2, for example).  Have the grub for this installer setup on sda2.  Then add the chainloader to the first distro's menu.lst

3.  Install distro3 on sda3.  Have its grub setup to sda3.  Then add the chainloader to the first distro's menu.lst.

The benefit to this method is that if distro2 or 3 updates the kernel, you don't have to worry about reconfiguring any grub menu.lst files, as that should all be automatic.

The downside is that you hop from grub to grub.  This hasn't been a big deal for me.  For example, the last part of my menu.lst looks like this:```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
#savedefault
makeactive
chainloader     +1

title           Ubuntu 32-bit
root            (hd2,5)
chainloader     +1


title           Gentoo
root            (hd2,6)
chainloader     +1


title           Debian
root            (hd2,7)
chainloader     +1

title           Sabayon Linux
root            (hd2,8)
chainloader    +1

```

Very nifty.

---

### Post by merlinus on 2007-09-08
You also may need to set a boot flag on sda1 for windows, and lose the one on sda4.

-merlin

---

### Post by Pumalite on 2007-09-08
You are a cop!

---

### Post by merlinus on 2007-09-08
Truth be told, I was one of those flower-power youth.  And still mostly a hippie and dharma bum after all these years, grey beard and all!

-merlin

---

### Post by Pumalite on 2007-09-08
You now something Merlin?. No wonder we are kind of friendly: we are kindred spirits. I read you are interested in piano and photography. I'm a professional photographer and painter and always a hippie (and grey beard too)(Zen-Buhddist to boot[pardon the pun])

---

### Post by merlinus on 2007-09-08
I play classical and improvisational acoustic piano (have for many years), and create abstract expressionist paintings.

Take a look at my website, if you care to:

[http://evening-sun.com](http://evening-sun.com)

-merlin

Sorry to have hijacked this thread.....

---

### Post by Pumalite on 2007-09-08
This is a riot! I'm gonna have to have my own Web page. Very nice.

---

### Post by hackxxcrack on 2007-09-08
> **Pumalite said:**
> So, you have to change (hd0,4) to (hd0,3), and sda5 to sda4

it doesnt work! :confused:

---

### Post by Pumalite on 2007-09-08
That's because you TYPED your fdisk. Post the real output ( copy and paste )

---

### Post by hackxxcrack on 2007-09-08
I cant boot an operating system that's not ubuntu or Windows!! i want to boot another distro but i cant , could anyone help me please?!!?!?!?!?!:confused:

---

### Post by Pumalite on 2007-09-08
Do you have a Live CD or not? If not; get Knoppix:[http://www.knoppix.org/](http://www.knoppix.org/), download the iso, burn it as an 'Image' to a CD and boot from it. Then mount your system and give us fdisk -lu so we can help you. As it is we hardly know what's going on.

---

### Post by hackxxcrack on 2007-09-08
> **Pumalite said:**
> Do you have a Live CD or not? If not; get Knoppix:[http://www.knoppix.org/](http://www.knoppix.org/), download the iso, burn it as an 'Image' to a CD and boot from it. Then mount your system and give us fdisk -lu so we can help you. As it is we hardly know what's going on.


here it is:
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    22876559    11438248+   7  HPFS/NTFS
/dev/hda2        22876562   107844344    42483891+  83  Linux---**this is ubuntu**
/dev/hda4       135170910   156296384    10562737+  83  Linux----[B]this is other distro
[/B]
Disk /dev/sda: 512 MB, 512753664 bytes
56 heads, 32 sectors/track, 558 cylinders, total 1001472 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32     1001215      500592    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(838, 55, 32) logical=(558, 39, 32)

---

### Post by Pumalite on 2007-09-08
You have a partition problem in your sda drive. Another thing: do you have two windows or Fat32 is storage. Otherwise your menu.lst as outlined before (with my corrections) should have worked. If Fat32 is storage; remove the bootflag from it. Another thing: in your 'other distro' try changing 'root' for 'rootnoverify'.

---

### Post by meierfra on 2007-09-08
Use the following entree  for Famelix in your  menu.lst in  ubuntu: 


title Famelix .:Hasta La Vista:.
root (hd0,3)
configfile /boot/grub/menu.lst


Reboot and your should be able  to choose Famelix from the grub boot menu.

This should work as long as the file /boot/grub/menu.lst exists in Famelix.


(You might also try root (hd0,4) . According to your most recent "fdisk -l"  it should be (hd0,3). But your earlier information suggest (hd0,4))

---

### Post by hackxxcrack on 2007-09-09
> **meierfra said:**
> Use the following entree  for Famelix in your  menu.lst in  ubuntu: 


title Famelix .:Hasta La Vista:.
root (hd0,3)
configfile /boot/grub/menu.lst


Reboot and your should be able  to choose Famelix from the grub boot menu.

This should work as long as the file /boot/grub/menu.lst exists in Famelix.


(You might also try root (hd0,4) . According to your most recent "fdisk -l"  it should be (hd0,3). But your earlier information suggest (hd0,4))

how can i install the grub on famelix partition?

---

### Post by meierfra on 2007-09-09
Did you try my suggestion? Did it fail? Did you get any error messages?

Grub  should  have been installed then you installed Famelix.  If not my method will not work. Do you know what boot loader Famelix uses?

Are you able to mount Famelix in Ubuntu? If yes, you can navigate to the folder /boot in  Famelix and see whether /boot/grub exists.

---

### Post by hackxxcrack on 2007-09-09
i have the machine i want to boot this way:

title           Famelix 2.0
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.17 root=/dev/sda4 root
savedefault

and when i select it it says:

Vfs: cannot open root device sda4 or unknown block (0,0)
Please append a correct "root=" boot option
Dernel panic - nost syncing:Vfs:unable to mount root fs on unknown block (0,0)

what do i have to do?

---

### Post by hackxxcrack on 2007-09-09
> **meierfra said:**
> Did you try my suggestion? Did it fail? Did you get any error messages?

Grub  should  have been installed then you installed Famelix.  If not my method will not work. Do you know what boot loader Famelix uses?

Are you able to mount Famelix in Ubuntu? If yes, you can navigate to the folder /boot in  Famelix and see whether /boot/grub exists.

i tried what you told me, but the grub/menu.lst isnt in the famelix boot folder, and when i tryed to put it there i couldnt...

---

### Post by meierfra on 2007-09-09
According to you  latest "fdisk" output you should be using "/dev/hda4"  instead of "/dev/sda4"

---

### Post by hackxxcrack on 2007-09-09
> **meierfra said:**
> According to you  latest "fdisk" output you should be using "/dev/hda4"  instead of "/dev/sda4"

okay! maybe thats my error thank you

---

### Post by meierfra on 2007-09-09
> tried what you told me, but the grub/menu.lst isn"t in the famelix boot folder, and when i tryed to put it there i couldnt...

Don't put your ubuntu menu.lst into famelix. That would be useless. 

How did you mount Famelix?  Did you use "/dev/sda4" ?

---

### Post by hackxxcrack on 2007-09-09
> **meierfra said:**
> According to you  latest "fdisk" output you should be using "/dev/hda4"  instead of "/dev/sda4"

You were right!!! thank you im using famelix right now! thank you 

nice one man! :)
[B]
PROMBLEM SOLVED THANK YOU ALL![/B]

---

