---
title: "WinXP changing GRUB?"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by poyner on 2005-04-09
Hi all, 
I'm having a bit of a problem getting WinXP and Ubuntu (Hoary)  to dual boot on my laptop. 
winxp is already installed on primary partition 1. I'm trying to install ubuntu on an extended partition that also contains some 'recovery' files for the laptop. 

I can install ubuntu fine and everything seems to be working... then i can reboot into ubuntu no problems.... and then i can reboot again and boot into winxp home.... but when i reboot after having been in winxp I get 

GRUB Loading stage1.5 

GRUB loading, please wait....
Error 17

Is it possible for WinXP to change something when it boots up that would stop grub from working? The only thing i did after booting winxp (before rebooting) was to open up partition magic and check the partitions. could this have altered grub in some way? 

any help would be appreciated as I'd love to be able to dual boot ubuntu on the laptop.

edit: oh yeah.. and I have done a search for error 17 but I couldn't find anyone else that has this problem where winxp seems to be changing something.

---

### Post by poyner on 2005-04-09
hmmmmm so noone's got any idea's???? what could winxp be changing on the system that would stop grub from working?

---

### Post by poyner on 2005-04-09
OK... I've just installed hoary for the third time. :) and am posting this from hoary

went something like this: 
1. stuck in hoary install cd and rebooted
2. chose all my regional settings, passwords etc. 
3. when it got to partitioning I erased the old ubuntu install partition and reset it as the root partition (using ext3). I also reset the swap partition. 
4. when it asked me where to install grub i entered /dev/hda
5. The computer then ejected the CD and I rebooted. 
6. the grub menu appeared fine and I chose ubuntu. 
7. It did all it's config and unpacking stuff. 
8. ubuntu starts and i get the login screen. 
9. I installed gparted to have a look at my beautiful new file system. :) 

here is fdisk -l

```
poyner@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4898    39343153+   7  HPFS/NTFS
/dev/hda2            4899       12149    58243657+   f  W95 Ext'd (LBA)
/dev/hda3           12150       12161       96390   83  Linux
/dev/hda5            6945        7066      979933+  82  Linux swap / Solaris
/dev/hda6   *        4899        6944    16434432   83  Linux
/dev/hda7            7067       10861    30483306    7  HPFS/NTFS
/dev/hda8           10862       12149    10345828+   b  W95 FAT32

Partition table entries are not in disk order
```

here is the bottom bit of my menu.lst

```
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

```

my device,map has
```
(hd0)	/dev/hda
```

my gparted looks like:

[IMG]http://web.aanet.com.au/poyner/images/Screenshot2.png[/IMG]

I now plan to reboot into Ubuntu.... and check everything again. seeya soon (hopefully)

---

### Post by poyner on 2005-04-09
[QUOTE=poyner]I now plan to reboot into Ubuntu.... and check everything again. seeya soon (hopefully)[/QUOTE]

Well I'm back.... everything went absolutely fine. Chose logout. Then restart computer. Then got all OK's then GRUB appeared no problems at all. chose Ubuntu and here I am. 

I also just tried mounting my winxp partition with 'mount /dev/hda1 /media/winxp -t ntfs -o umask=0222'

Then I browsed to it no problems. OK. now for the big test. Am going to reboot into Winxp.... unless anyone can recommend anything else I should do beforehand.

---

### Post by poyner on 2005-04-09
well things are still looking up.... I'm typing this from my winxp install. This type on the reboot I did a full 'shutdown' and then press the button to turn the computer back on. don't know if that makes any difference but thought i'd give it a try.... GRUB appeared just fine. I chose winxp and here i am. now for the really big test. The point where the whole thing has come to a screaming halt the last two times i've tried.... the reboot into ubuntu. :)

---

### Post by poyner on 2005-04-09
well I'll be!!!!! It worked!..... I'm now back in ubuntu..... so the only thing I did this time different to the last time was not opening up partition magic from within winxp..... I'd love to test out whether or not this does kill grub.... but I don't think I really want/need to install ubuntu for a 4th time today. :) 

whilst I'm here though... can anyone explain to me what 'Partition table entries are not in disk order' means.... and why hda6 comes before hda5 in gparted??? I assume the two are related.... why would it be?

---

### Post by Dave C on 2005-08-06
Yep, I had exactly the same issue.

The clue is in the message 'Partition table entries are not in disk order'.  
The problem is that GRUB was set up to point at the ubuntu partition, and then a windows partition editor re-numbered the partitions so they are in disk order.  

When you opened partition magic, or in my case the windows disk manager, it 'corrected' the error which means that grub goes looking for its files in the wrong partition. 

I fixed it by booting into the live session cd, and editing the partitions manually so the numbers were the same as before.  Rebooted and everything works ok, dual boots into ubuntu or xp.

... the sad thing is I had to go through this twice before I realised that I shouldn't use the windows tools. ](*,) 

Probably should edit grub conf file so that it will pointing to the right partition after windows 'fixes' them, and then correct the numbering to be in disk order so it won't happen again.

---

