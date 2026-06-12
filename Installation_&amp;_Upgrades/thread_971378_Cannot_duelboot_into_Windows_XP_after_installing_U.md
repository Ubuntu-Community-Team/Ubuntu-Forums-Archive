---
title: "Cannot duelboot into Windows XP after installing Ubuntu"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Madigan on 2008-11-04
Hello Ubuntu Forums!

I just want to start by saying that I've spent the past two hours searching through these forums for help with this issue, but so far I haven't been able to find a solution.

First: The situation.

A friend of mine finally convinced me to try Linux last week and gave me a copy of an Ubuntu Live CD so I could try Ubuntu without actually installing it.  I liked it a lot, but didn't want to stop using Windows XP, so I decided to try for a duel-boot setup.  My PC has two hard drives, a 100 Gb one that I have XP installed on, and a 200 Gb one that I had partitioned into 2 parts and was using for storage and game installation.

So I decided the best course of action would be to clear out one of the two partitions on the 200 Gb drive and use that space to install and run Ubuntu.  The installation went through successfully and I got Ubuntu up to speed with drivers and basic software.  The trouble came when I tried to switch back to XP.  I restarted my PC, hit ESC to bring up the GRUB menu, and saw that there was no option to boot up XP.  I called my friend and he said that it was common for GRUB not to recognize an XP boot if it was on a different drive from where Ubuntu was installed.  I was getting pretty freaked out still, as the last thing I wanted was for Ubuntu to affect my usage of XP in any way.  I found a couple of examples on this forum of how to manually edit GRUB's menu.lst.  Here's the bottom of my menu.lst:

> ## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		afe94a3f-663c-4059-893a-bb26c7434656
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=afe94a3f-663c-4059-893a-bb26c7434656 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		afe94a3f-663c-4059-893a-bb26c7434656
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=afe94a3f-663c-4059-893a-bb26c7434656 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		afe94a3f-663c-4059-893a-bb26c7434656
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows XP Pro
root(hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0) 
chainloader +1

here's the results of running fdisk:

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x963f104a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       24320   195350368+   f  W95 Ext'd (LBA)
/dev/sda5            5100       24320   154392651    7  HPFS/NTFS
/dev/sda6               1         486     3903700+  82  Linux swap / Solaris
/dev/sda7             487        5099    37053891   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc657c657

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12187    97892046    7  HPFS/NTFS

The first drive (sda) is the 200 Gb drive that used to have 2 NTFS partitions.  You can see the 40 gigs or so that I deleted and turned into partitioned space for installing and running Ubuntu.

The second drive (sdb) is the 100 gig drive that I have XP installed on.


After editing my menu.lst and restarting my PC, I can now see the Windows XP boot in my GRUB menu, but when I select it the screen goes black and says "Starting up...", but does nothing else until I manually turn off the PC.  I'm pretty sure that I didn't set up my menu.lst right, so any help with what should be there would be great.

Thanks in advance to those that would offer me their time and experience!

---

### Post by crazyness003 on 2008-11-04
> **Madigan said:**
> title Windows XP Pro
root(hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0) 
chainloader +1 			 		

I dont know where you got the map options, but that might be your culprit.
This is my entry for the xp boot
```
title        Windows XP Ultimate
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

Of course, my xp is located on sda1.

I hope this helps

---

### Post by Madigan on 2008-11-04
Hmm... Changing it to that (well, keeping the root() line the same) still causes it to hang on "Starting Up...".   :(

---

### Post by zvacet on 2008-11-05
Try with this 

title Windows XP Pro
rootnoverify   (hd1,o)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by Madigan on 2008-11-05
Nope, sorry, Zvacet.

Instead of hanging at "Starting Up...", I got "Error 11: Unrecognized device string..."

I don't know if that's progress or not... :-s

---

### Post by caljohnsmith on 2008-11-05
Do you know which drive you are booting on start up? Is it the Ubuntu drive or Windows drive?

Please post the following to help clarify your setup:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
Also, it looks like you had a small typo in your menu.lst:
[QUOTE=Madigan]```
title Windows XP Pro
[COLOR="Red"]root(hd1,0)[/COLOR]
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```[/QUOTE]
There should be a space between root and (hd1,0) like:
```
title Windows XP Pro
[COLOR="Red"]root (hd1,0)[/COLOR]
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```
Give that a try first and see if it makes any difference; otherwise please post the output of the above commands, and we can work from there.

---

### Post by Madigan on 2008-11-05
Thanks, caljohnsmith. I double checked menu.lst, fixed the typo, and still got "Error 11". Here's the results of that code:

> sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 

sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system

sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff06                                   
0000002

sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump

---

### Post by caljohnsmith on 2008-11-05
OK, you should at least get that "starting up..." message if you use the Windows entry I gave in my last post, similar to what you got before; but you're getting error 11? I think that error would most likely be due to a typo in your menu.lst entry for Windows. How about trying:
```
title Windows XP Pro
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
And make sure you have all the spaces and everything correct. That should at least result in the "starting up..." hang, but not an error 11. If you still get an error 11, then just to make sure Grub doesn't have any corrupted files, please post the output of the following:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
```
Also, can you switch your BIOS to temporarily boot the Windows sdb drive once? It would be good to check that you can still boot directly into Windows. Let me know how it goes. :)

---

### Post by Madigan on 2008-11-05
Okay, well it turns out I DID have a typo in the menu.lst, but it wasn't what I thought.  Had a capital O in there instead of a zero... Don't ask me how that happened... :oops:

Anyhow, using the lines you just posted, caljohnsmith, got a new error:

> Starting Up...

NTLDR missing.

Press Ctrl + Alt + Del to restart.


hmmmm...

---

### Post by caljohnsmith on 2008-11-05
Sounds like you may be missing your Windows boot files, but you didn't even get the "starting up..." error this time? Have you done something with your Windows partition since that "starting up..." error that maybe you neglected to mention? 

How about posting:
```
sudo mount /dev/sdb1 /mnt
ls -l /mnt
```
Where the "-l" is a lowercase L, not a one. And also, have you tried setting your BIOS to boot the sdb Windows drive first, and what happens when you do that?

---

### Post by Madigan on 2008-11-05
No, I haven't done anything to the Windows partition since installing Ubuntu.

Here's the result of that code:

> total 2095172
drwxrwxrwx 1 root root          0 2008-10-29 23:49 Config.Msi
drwxrwxrwx 1 root root       4096 2008-11-01 14:29 cygwin
drwxrwxrwx 1 root root       4096 2007-06-07 06:25 Documents and Settings
drwxrwxrwx 1 root root          0 2008-08-20 17:46 found.000
drwxrwxrwx 1 root root          0 2008-09-11 01:21 found.001
drwxrwxrwx 1 root root          0 2007-06-07 18:59 MSOCache
drwxrwxrwx 1 root root       4096 2008-01-03 15:39 Netgear
drwxrwxrwx 1 root root          0 2008-08-20 17:33 NVIDIA
-rwxrwxrwx 1 root root 2145386496 2008-11-04 15:23 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-11-03 17:53 Program Files
drwxrwxrwx 1 root root          0 2007-06-07 18:56 RECYCLER
drwxrwxrwx 1 root root       4096 2007-06-07 22:06 System Volume Information
drwxrwxrwx 1 root root      40960 2008-11-03 15:30 WINDOWS

I'm going to try messing with my BIOS and seeing if I can change the boot order.

---

### Post by caljohnsmith on 2008-11-05
Hmmm... you are definitely missing your Windows boot files, but I can't figure out then how you originally got a "starting up..." message when booting Windows rather than the "NTLDR missing" error you get now. 

Well anyway, at least the good news is that since I also have Windows, I have the Windows boot files you need; I've attached them to this post. Just save the attachment to your Ubuntu desktop and do:
```
sudo mount /dev/sdb1 /mnt
cd ~/Desktop
tar xvf "Windows boot files.tar.gz"
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
After that, reboot, and let me know how far you get this time when booting Windows. :)

---

### Post by Madigan on 2008-11-05
Caljohnsmith, you'll be happy to know that I'm writing this reply from the familiar comfort of Windows XP.  It worked, although I'm really confused as to what could have erased my boot info.  The only thing I can think of is that because I'm using the old IDE Master/Slave setup for my drives, and Windows was installed onto the Slave drive, it still put it's boot sector on the 200 gig Master drive, even though it wasn't installed there.  And I guess when I re-partitioned that other drive it must have destroyed my Windows boot.... Hmmm..

Anyhow, it's all golden now, so thank you very much!!!

---

### Post by caljohnsmith on 2008-11-05
> **Madigan said:**
> Caljohnsmith, you'll be happy to know that I'm writing this reply from the familiar comfort of Windows XP.  It worked, although I'm really confused as to what could have erased my boot info.  The only thing I can think of is that because I'm using the old IDE Master/Slave setup for my drives, and Windows was installed onto the Slave drive, it still put it's boot sector on the 200 gig Master drive, even though it wasn't installed there.  And I guess when I re-partitioned that other drive it must have destroyed my Windows boot.... Hmmm..

Anyhow, it's all golden now, so thank you very much!!!
Yes, after thinking about it a little more, I'm sure what you say is spot on; your Windows boot files were in the NTFS partition on your master drive that you deleted. I was confused because you originally got the "starting up..." message and not the classic "missing NTLDR" message you get when the boot files are missing. Anyway, I'm really glad you can boot Windows now. Cheers and have fun. :)

---

### Post by crazyness003 on 2008-11-06
Happy to hear your problem is [SOLVED] (pun intended)

Anyway, another reason why ntldr went missing is because it does it more often than people think. Random corruption and bizzare deletion have happened to me more than once (without even messing with drives, or installing new os's). Just consider yourself lucky it was just ntldr. I hadntldr and boot.ini go bad on me and its kinda hard to replace boot.ini (depending on how your hdd is partitioned and configured, its config is different). I ended up having to reinstall (of course after using Knoppix liveCD to recover my docs. w00t Linux)

Cheers.

---

