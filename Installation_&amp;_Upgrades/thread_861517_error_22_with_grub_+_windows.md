---
title: "error 22 with grub + windows"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by Azrael90 on 2008-07-16
I had windows installed and linux but linux crashed and I reinstalled linux but I am getting the error 22: No such partition. I already tried fixing the mbr with supergrub but now the NTLDR is missing and Windows is not booting anymore and linux is not bootable.


sudo fdisk -l:
```

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcae6cae6

 Device    Boot      Start    End      Blocks      Id    System 
/dev/hde1   *         1      19457   156288321      7   HPFS/NTFS


Disk /dev/hdg: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd426d426

 Device    Boot      Start    End     Blocks   Id    System
 /dev/hdg1   *         1      11473   92156841  7   HPFS/NTFS
/dev/hdg2            11474   11722   2000092+  82 Linux Swap/Solaris
/dev/hdg3            11723   24321   101201467+ 83   Linux

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3edae12e

 Device    Boot      Start    End      Blocks      Id    System
 /dev/sda1   *         1      36482   293035096+    7   HPFS/NTFS

```

---

### Post by logos34 on 2008-07-16
boot up the ubuntu live cd, mount root partition (hdg3) and post your /boot/grub/menu.lst.

Try [reinstalling grub from the live cd]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by chicken101 on 2008-07-16
What I suggest is that you use a supergrub cd to repair the grub menu.  While it is possible to fix the grub using your ubuntu live cd, I find it much quicker and easier to use the supergrub, which can be found [here]("http://www.supergrubdisk.org/").  Once you burn it to a CD, boot it up (like you would with a live cd) and follow the simple instructions.  This disk will get your grub menu set up again in mere seconds.:guitar:

---

### Post by Azrael90 on 2008-07-16
> **logos34 said:**
> boot up the ubuntu live cd, mount root partition (hdg3) and post your /boot/grub/menu.lst.

Try [reinstalling grub from the live cd]("http://ubuntuforums.org/showthread.php?t=224351").

how to mount it ? sorry but still a newbie ^^

Edit: tried installing grub but im getting Error 22 while grub is loading.

---

### Post by logos34 on 2008-07-16
Are you using the Hardy 8.04 live cd?

Just click on the root volume in nautilus file browser to mount.  Then navigate inside that volume to /boot/grub/menu.lst

If using an older version of ubuntu which does not automount:

(in a terminal):

sudo mkdir /media/hgd3

sudo mount -t ext3 /dev/hdg3 /media/hdg3

gksudo gedit /media/hdg3/boot/grub/menu.lst

---

### Post by Azrael90 on 2008-07-16
I am not seeing sth wrong...but i know nothing so...

This is my menu.lst
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=92bddca6-cb81-4623-bd3a-3cd4fe8fbd91 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=92bddca6-cb81-4623-bd3a-3cd4fe8fbd91 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdg1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by logos34 on 2008-07-16
reboot to the grub menu screen. 

select ubuntu, and press 'e' to edit, 'e' again on the 'root' line and change to (hd**0**,1).  The 'b' to boot.  If it works that means hdg rather than hde is the boot drive.  You can make the change permanent once inside ubuntu:

gksudo gedit /boot/grub/menu.lst

make sure to take out the 'map' lines in windows stanza

---

### Post by Azrael90 on 2008-07-16
So basicly I change the menu.lst to

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=92bddca6-cb81-4623-bd3a-3cd4fe8fbd91 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=92bddca6-cb81-4623-bd3a-3cd4fe8fbd91 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdg1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I change all the root from hd1 to hd0 and what about the map parts ?

---

### Post by Azrael90 on 2008-07-16
okay i changed it from hd1,2 to 0,2 but it did not work so i tried and 3,2 worked.

---

### Post by Azrael90 on 2008-07-16
Okay so I can boot into linux via supergrub but when grub tries to load on normal boot I still get error 22. When I trie to boot windows is says taht the NTLDR is missing. How to fix ? Btw should I change the windows root to 3,0 since it is on the same hd as linux

---

### Post by logos34 on 2008-07-16
> **Azrael90 said:**
>  so i tried and 3,2 worked.

huh?  that's impossible...you only have 3 drives according to fstab, (which would be hd0, hd1, hd2).  How can hd**3**,2 work?  Are you using an PCI IDE host disk controller or something?

---

### Post by Azrael90 on 2008-07-16
> **logos34 said:**
> huh?  that's impossible...you only have 3 drives according to fstab, (which would be hd0, hd1, hd2).  How can hd**3**,2 work?  Are you using an PCI IDE host disk controller or something?

yes my mainboard has sata connections only so I had to use a pci ide adapter to use my old ide drives.

anywho it is working with supergrub but only with supergrub. still getting error 22 on normal boot.

---

### Post by logos34 on 2008-07-16
> **Azrael90 said:**
> Okay so I can boot into linux via supergrub but when grub tries to load on normal boot I still get error 22. When I trie to boot windows is says taht the NTLDR is missing. How to fix ? Btw should I change the windows root to 3,0 since it is on the same hd as linux

...

> 
anywho it is working with supergrub but only with supergrub. still getting error 22 on normal boot.error 22
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

When you reinstalled grub from the live cd, you did use

grub> setup **(hd0)**

right?

Something odd happened when you reinstalled linux such that the Bios is not detecting the drives in the old order, or not consistently.  And the PCI IDE host controller card is not making things any easier.

Try this from inside linux:

> sudo grub

** find /boot/grub/stage1**
(enter output ('hd3,2'?) in next command)
** root (hd3,2) **
** setup (hd3)** --> this will write grub IPL code to the MBR of /dev/hdg
** quit**Now reboot into the Bios and set the linux drive, hdg, first in the Bios hard disk boot priority.  If it brings up the grub menu screen, press 'e' to edit ubuntu selection, 'e' again on 'root' line and change to (hd0,2).  'b' to boot.  

See if that works

---

### Post by Azrael90 on 2008-07-16
okay that is strange. find /grub/stage1 gives (hd 1,2) back.

---

### Post by logos34 on 2008-07-16
ok, then enter whatever it says.  The point here is to write grub bootloader stage1 (+1.5) to the ubuntu drive, and boot from that.  Because it appears your original boot drive was hde and ubuntu was second.  (which changed to fourth position and now its back to second--hd**1**,2)

so

root (hd1,2)
setup (hd1)

then the rest like above

give that a whirl

---

### Post by Azrael90 on 2008-07-16
same result. linux is only bootable with supergrub and hd3,2 as setting.

btw when I try to go to root (hd3,2) it says Error 21 Selected Disk does not exist. 
So does that mean that supergrub is recognizing the drives in another way than grub installed on the hd ?


this is fdisk -l ( the first partition is windows xp second is swap and 3 linux)
```

  Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *          63   184313744    92156841    7  HPFS/NTFS
/dev/hdg2       184313745   188313929     2000092+  82  Linux swap / Solaris
/dev/hdg3       188313930   390716864   101201467+  83  Linux

```

Just in case we are doing sth basicly wrong

---

### Post by logos34 on 2008-07-16
> **Azrael90 said:**
> So does that mean that supergrub is recognizing the drives in another way than grub installed on the hd ? 

Apparently, and/or the fact that you're booting SGD from a cdrom is throwing off the bios disk order.

we didn't make a mistake in fdisk...linux root is definitely the third partition hdg3/(hd?,2), and XP is hgd1/(hd?,0).  But which disk??? hd0, hd1, hd3??? ah...

BTW, what is hde1? A data partition or another windows system partition (it's got boot * flag)

---

### Post by chicken101 on 2008-07-16
Did you try to use the supergrub to fix the GRUB menu?  I've done it many times, it definitely works.

---

### Post by Azrael90 on 2008-07-16
hde1 is a data disk like games music and so on.
hdg1 is windows xp
hdg2 swap
hdg3 linux
sda is data storage



chicken101 yes I am using SGD all the time because I cannot boot otherwise.


One quick question. Which boot should I use ? can the Windows Boot Manager handle Linux and can GRUB handle Windows ?

---

### Post by chicken101 on 2008-07-16
> **Azrael90 said:**
> hde1 is a data disk like games music and so on.
hdg1 is windows xp
hdg2 swap
hdg3 linux
sda is data storage



chicken101 yes I am using SGD all the time because I cannot boot otherwise.


One quick question. Which boot should I use ? can the Windows Boot Manager handle Linux and can GRUB handle Windows ?

You need to use the supergrub disk to fix the menu, take a look at their wiki which is [here]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub").  It explains everything probably better than i can explain it.:popcorn:

---

### Post by logos34 on 2008-07-16
> **chicken101 said:**
> You need to use the supergrub disk to fix the menu, take a look at their wiki which is [here]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub").  It explains everything probably better than i can explain it.:popcorn:

SGD will not fix menu.lst for you.  It will 1) boot your linux via menu.lst  or directly via 2) symlinks in /, 3) reinstall grub to MBR, 4) write grub to first sector of linux root. (or even uninstall grub from mbr).

---

### Post by logos34 on 2008-07-16
> **Azrael90 said:**
> 
One quick question. Which boot should I use ? can the Windows Boot Manager handle Linux and can GRUB handle Windows ?

yes to both.

And since you are having such a hard time, it might be time to try using windows to boot linux.

It's just that there's got to be a way with grub because it *was* working before you reinstalled, just can't figure out what could have gone wrong

---

### Post by logos34 on 2008-07-16
> 
Post #13:
Now reboot into the Bios and set the linux drive, hdg, first in the Bios hard disk boot priority. If it brings up the grub menu screen, press 'e' to edit ubuntu selection, 'e' again on 'root' line and change to (hd0,2). 'b' to boot.You did do exactly that, right?  (Bios **hard disk** order, not to be confused with **device** order)

If that doesn't work, try using windows bootloader to dual boot (again, the linux/xp drive hdg has to be first in the Bios boot order).

Run this in linux:

**sudo grub-install /dev/hdg3**

**dd if=/dev/hdg3 of=grub.mbr bs=512 count=1**

Copy 'grub.mbr' to windows c:\ drive

Open **boot.ini** file in c:\ (if you do this in windows simply type the name in address bar--it's a hidden file)

add this line to end:
[B]
c:\grub.mbr="Ubuntu"

[/B]Restore windows bootloader to MBR with Super Grub Disk.

---

### Post by Azrael90 on 2008-07-17
okay I am going to. actually I cannot change the disk boot order in the bios because this does not detect the pci adapter so I have to set boot with the installed software for the adapter. But since windows and linux are on the same drive it doesnt matter because it has not been changed.

I am going to do that now

so boot.ini looks like this now
```

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
c:\grub.mbr="Ubuntu"

```

It says when booting that NTLDR is missing. I already tried to copy the NTLDR from the windows cd using the windows repair console. The weird thing is that in the repair console the drive letter of my windows partition is switched from C: to E: and my CD-drive is G: instead of E: .

---

### Post by Azrael90 on 2008-07-17
Okay so now we are getting somewhere. I now have the option to chose between Ubuntu(which brings grub up) and Windows. Ubuntu is only bootable if I change hd3,2 to hd 0,2 so I guess I have to change the menu.lst to make this work ?
I am giving it a trie

---

### Post by Azrael90 on 2008-07-17
FINALLY IT WORKS
Okay it is working now. Thank you Logos34 for all your patience and knowledge you really saved my *** because 12 hours more and I would have thrown my computer out of the window.
I have one last question which does not concern install:
How do I make a folder accessable for the network ? Like in windows by just right klicking and klicking on the right tab.

---

### Post by logos34 on 2008-07-17
my pleasure.  I like troubleshooting, others do crossword puzzles or sudoku.  

For the record, I almost jumped out the window once when I had grub problems! 

Hope this helps re file sharing:

[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

enjoy!

---

### Post by Azrael90 on 2008-07-17
well the folder I want to be available in the network is on another computer which runs under ubuntu server edition and there is no easy way like it is described in the link you gave me ... any idea ? or are you not familliar with server edition ?

---

### Post by logos34 on 2008-07-17
oh, I saw this 

> Like in **windows** by just right klicking and klicking on the right tab.

and jumped to conclusions (SMB, etc).

Maybe this is what you're looking for (->NFS):

[https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html)

---

