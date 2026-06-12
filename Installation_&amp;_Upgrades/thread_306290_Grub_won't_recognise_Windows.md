---
title: "Grub won't recognise Windows"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by whitworth on 2006-11-24
Dear all,

I am a bit of a newbie. I installed Ubuntu 6.10 from the desktop cd onto my computer but left a 4gb Windows 2000 partition. The windows partition is /dev/hda5 and it mounts fine on Ubuntu. However, the installer did not automagically add the Windows partition to grub. Furthermore, when I added the Windows partition to menu.lst, grub still refuses to load Windows. 

Here is the output of fdisk -l:

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1             392         522     1052257+  82  Linux swap / Solaris
/dev/hda2             523        1026     4048380    f  W95 Ext'd (LBA)
/dev/hda3   *           1         391     3140676   83  Linux
/dev/hda5   *         523        1026     4048348+   7  HPFS/NTFS

Partition table entries are not in disk order



Here is the relevant section of the grub file menu.lst:

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Windows 2000
root		(hd0,4)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot


I would simply like to boot Windows again, one way or another. Any help would be appreciated.

---

### Post by bulldog on 2006-11-24
Yes,well you have to have windows on the first primary partition.
It writes the boot files to the first partition,which in your case,can't be done.

I'm afraid you have to reinstall,but maybe someone else has a solution for this.

---

### Post by louieb on 2006-11-24
Like bulldog said it is my understanding that windows need to be in a primary partition (hda1 - hda4).  Your only NTFS partiton is logical partition hda5.   
You said the partiton mounts just fine under Ubuntu. Does it look like a normal Windows install? (does it have folder named windows? does it have a folder named "Program Files"?)
What happens when you choose the windows grub entry? What error message do you get?
You might try changing the windows entry in menu.list.
Change root to rootnoverify.

---

### Post by whitworth on 2006-11-24
Right, I didn't realise Windows had a restriction on which partition it was on. (Why is that necessary?) I'm a little puzzled because I used to boot into Windows 2000, and I haven't done anything to that partition. Maybe it is because I had a Windows 98 partition I never used, which I wiped in favour of Ubuntu - perhaps that is what was necessary to boot it up.

To louieb: Yes it is an ordinary Win 2000 install with WINNT, Program Files etc. I can't really be bothered to fiddle with the configuration files if it seems the consensus that booting cannot work.

I think I'll end up obliterating the Win2k partition in that case. It doesn't have that much on it anyway.

Thanks for your help.

---

### Post by bulldog on 2006-11-25
You can put XP where ever you want **if** your first partition is capable of hosting the windows boot files.
If your first partition was a FAT32 your boot files where stored there.

But by removing that partition your capability of booting win200 was gone either I'm afraid.

---

### Post by shpook on 2006-11-25
First of all, try running
```
sudo update-grub
```
See if this detects your windows partition automatically.

If it does not, then looking at your menu.lst file it seems you are missing 'boot' instruction in the windows entry.

```
title Windows 2000
root (hd0,4)
makeactive
chainloader +1
```

should read

```
title Windows 2000
root (hd0,4)
makeactive
chainloader +1
boot
```

Change your menu.lst and try booting, you can also try entering those four commands manually: when grub menu appears press 'c' to enter command mode.

---

