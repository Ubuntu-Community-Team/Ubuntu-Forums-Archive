---
title: "Installing Windows..."
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by glyons on 2005-07-27
Hi everyone,

I would like some help for installing Windows on my PC without killing Ubuntu.

My setup is:
1. 80GB HD in hda, empty.
2. 160GB HD in hdb with ubuntu and my files.

I would like to install windows in the 80GB HD without damaging grub, and add a menu for windows in grub. Also, I'd like to know what would happen if I swapped the drives? would ubuntu still work? there are a lot of references to hdb1 (the ubuntu partition) in fstab.

Any help would be greatly appreciated.

---

### Post by angkor on 2005-07-27
I'm no expert, but usually it's better to do it the other way around. I think windows is going to overwrite the mbr anyhow. But you can re-install grub after that.

---

### Post by audax321 on 2005-07-27
That's a good question and something I was looking to do. I have this setup right now:

40 GB (boot drive) with Ubuntu - 3 partitions (/, swap, and /home)
200 GB (FAT32) with just random storage garbage
27.3 GB (NTFS) waiting to be installed with windows


If I install windows to the 27.3 why would it overwrite grub? I always thought what hard drive windows booted from depended on what was selected in the bios. What if I just temporarily unplug the 40 GB and 200 GB drives?

Secondly, if windows does overwrite grub, how do I go about reinstalling it without destroying any data on the 40GB or 200GB drives.


EDIT: Here's a website that says it can be done by just temporarily removing the linux drive: [http://www.linuxforum.com/forums/index.php?showtopic=151261](http://www.linuxforum.com/forums/index.php?showtopic=151261)

---

### Post by Xian on 2005-07-27
Here's a method: [Installing Windows After Linux](http://keithdevens.com/weblog/archive/2005/Jun/25/Install-Windows-after-Linux).

---

### Post by audax321 on 2005-07-27
Thats a good method as well, although I'd like to add that instead of Knoppix you can use the Ubuntu CD and go to rescue mode by I think typing rescue at the prompt you get when booting from cd. Then you can just type:

grub-install /dev/hda (or whatever the path is to the harddrive).

Then just add windows as to grub as needed from within Ubuntu.

---

### Post by glyons on 2005-07-30
well, i've created quite a bloody mess here... 
I installed Windows XP on hda1, assuming linux wouldn't be borked because it's on hdb1 and grub is installed there too, however, after windows is installed i get an Error 17 from grub. 
I restored grub on hda1 using 'rescue' from the install cd, but my windows partition became unreadable for ubuntu and for the windows install cd. 

So I'm back at ubuntu for the moment.. 

Please, help me, I really need to use some windows-only apps (though I really dislike it now, the shell sucks, the GUI is ok.. )

How can I install grub in hdb1 so it's completely stand-alone and does not depend on ANYTHING on hda?

here's the output of fdisk -l
```
gaston@MC:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1218     9783553+   7  HPFS/NTFS
/dev/hda2            1219        9732    68388705    f  W95 Ext'd (LBA)
/dev/hda3            1276        2550    10241406    7  HPFS/NTFS
/dev/hda5            1219        1275      457789+  82  Linux swap / Solaris
/dev/hda6            2551        9732    57689383+   7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1912    15358108+  83  Linux
/dev/hdb2            1913       18654   134480115    5  Extended
/dev/hdb5            1913        2043     1052226   82  Linux swap / Solaris
/dev/hdb6            2044       18654   133427826   83  Linux

```

Thanks a lot to everybody..

---

### Post by codejunkie on 2005-07-30
[QUOTE=glyons]well, i've created quite a bloody mess here... 
I installed Windows XP on hda1, assuming linux wouldn't be borked because it's on hdb1 and grub is installed there too, however, after windows is installed i get an Error 17 from grub. 
I restored grub on hda1 using 'rescue' from the install cd, but my windows partition became unreadable for ubuntu and for the windows install cd. 

So I'm back at ubuntu for the moment.. 

Please, help me, I really need to use some windows-only apps (though I really dislike it now, the shell sucks, the GUI is ok.. )

How can I install grub in hdb1 so it's completely stand-alone and does not depend on ANYTHING on hda?

Thanks a lot to everybody..[/QUOTE]
since you had your computer booting from hdb1 before and have added windows to hda1 and installed grub there you need to change your bios to boot to hda1 also.

---

### Post by glyons on 2005-07-30
No, my computer was indeed booting from hda1 all the time, for some reason ubuntu installed grub there when I installed it the first time, however I did a 'grub-install /dev/hdb' hoping it would install grub in hdb, if I boot from hdb and Windows' boot manager is in hda I get an Error 17 'cannot mount partition', If I restore grub in /hda with grub-install I cannot boot into windows and the partition appears to be damaged.

thanks for the fast reply
 :)

---

### Post by codejunkie on 2005-07-30
[QUOTE=glyons]No, my computer was indeed booting from hda1 all the time, for some reason ubuntu installed grub there when I installed it the first time, however I did a 'grub-install /dev/hdb' hoping it would install grub in hdb, if I boot from hdb and Windows' boot manager is in hda I get an Error 17 'cannot mount partition', If I restore grub in /hda with grub-install I cannot boot into windows and the partition appears to be damaged.

thanks for the fast reply
 :)[/QUOTE]
when you install grub to hda is windows listed in grub but not working or is the windows option just missing from grub?

---

### Post by glyons on 2005-07-30
[QUOTE=codejunkie]when you install grub to hda is windows listed in grub but not working or is the windows option just missing from grub?[/QUOTE]

is missing, if I add 
```
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

```
to menu.lst it just goes to an infinite loop.

---

### Post by mingus on 2005-07-30
IMO, for your configuration this is the cleanest:

1.  Change the XP stanza in menu.lst -

title Windows XP
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

2.  Install grub to hdb 

3.  Set BIOS to boot from second drive 

The map command fools XP into thinking it is booting from the first drive in the BIOS sequence, which is an XP requirement.

---

### Post by glyons on 2005-08-01
[QUOTE=mingus]IMO, for your configuration this is the cleanest:

1.  Change the XP stanza in menu.lst -

title Windows XP
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

2.  Install grub to hdb 

3.  Set BIOS to boot from second drive 

The map command fools XP into thinking it is booting from the first drive in the BIOS sequence, which is an XP requirement.[/QUOTE]
 It Still does not work :( 
using that justs loops to the grub menu

---

### Post by mingus on 2005-08-01
[QUOTE=glyons]It Still does not work :( 
using that justs loops to the grub menu[/QUOTE]

Try changing "root" to "rootnoverify" . . . does grub give you an error message?

---

### Post by mingus on 2005-08-01
I reviewed this thread and am not sure what exactly is where on your system.  E.g., posts refer to installing XP on hda1 and then grub on hda1 - if that is what was done, XP will not boot . . . it may help to summarize the  bootstrap process . . . 

XP requires a pgm installed in the MBR of the first drive in the BIOS boot (not IDE) sequence *unless* this step is bypassed by using another boot loader (grub) installed to the MBR, which also must be on the first drive in the BIOS sequence.   The MBR code looks at the partition table for the active (or "bootable" or "boot flagged") primary, finds sector 1 on that partition, and transfers control to the pgm installed there.

Sector 1 is the "boot sector."  In XP it holds ntdetect.com, in grub stage1.5. ntdetect looks for ntldr in a hard-coded location; stage1.5 looks for stage2 in the partition it was instructed to when it was installed.

When ntldr runs it looks at boot.ini to determine which partition holds the W$ OS (i.e., system32).  MS calls the combination of ntdetect.com, ntldr, and boot.ini the "system partition."  Grub's stage2 looks at menu.lst and will load the OS ref'd there *except* W$ - since only ntldr can load W$, grub "chain-loads" to the W$ boot sector in its system partition.

In your configuration, you want hdb to be the first drive in the BIOS boot sequence because you want grub to control bootstrap.  Grub should be installed to hdb (now hd0), it should have a stanza to chain-load to the hda1 bootsector (hd1,0), using the map command to fool W$ into thinking hd1 is hd0 (because that is where ntdetect is going to look for ntldr).

On hda (now grub's hd1), you do not need anything in the MBR (although if the W$ MBR is installed, you could boot straight into W$ by changing the BIOS boot sequence back to the IDE sequence; a good fall-back to have).  You *must* also have the W$ system partition in the active primary, with ntdetect.com in the boot sector 1.

So here is where the bad news may possibly be.  If grub was installed to hda1, then the W$ boot sector is missing and the system partition is damaged.  According the MS docm, using the "fixboot" command in the XP Recovery Console should re-write the boot sector - note that some docm indicates this only applies to a FAT system partition, while other docm does not.  If this does not work, probably ntldr is mislocated or the partition table hosed (W$ uses it for other strange purposes in the bootstrap), in which case you'll need to do a repair install.

Hope this helps.

---

