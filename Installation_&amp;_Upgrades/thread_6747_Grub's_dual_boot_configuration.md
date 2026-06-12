---
title: "Grub's dual boot configuration"
date: 2004-12-01
forum: Installation &amp; Upgrades
---

### Post by ikoyk on 2004-12-01
Hello, I 'm a new user of ubuntu and I'm trying to make some configuration to the grub loader boot menu. What I want, is to reduce the timeout delay and to make WinXp as my  default OS. I tried to edit the menu.lst from the ubuntu text editor but it's in a read-only mode and I don't know for sure if it's possible to do it from there. From the boot loader itself I don't know what commands to edit. Can you direct me how to do it?

---

### Post by rthunstrom on 2004-12-01
Hi ikoyk,

I´m also new to Ubuntu linux, I installed it last night, and I can actually help you because i´ve been editing the menu.lst file a couple of times.. :(

1. Somewhere in the top menu inside Ubuntu you can choose "Open Root Terminal" or something like that.
2. Now you write **gedit** in the terminal window and a texteditor appears.
3. You are now able to edit menu.lst since it is no longer [read only]



My own problem is that I get this message when I try to boot my Win XP:

[COLOR=Red]Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please re-install a copy of the above file.[/COLOR]

I´ve been reading lots of forums today(at work!) and printed out some solutions that I´ll try later today.

---

### Post by ikoyk on 2004-12-01
[QUOTE=rthunstrom]Hi ikoyk,

I´m also new to Ubuntu linux, I installed it last night, and I can actually help you because i´ve been editing the menu.lst file a couple of times.. :(

1. Somewhere in the top menu inside Ubuntu you can choose "Open Root Terminal" or something like that.
2. Now you write **gedit** in the terminal window and a texteditor appears.
3. You are now able to edit menu.lst since it is no longer [read only]



My own problem is that I get this message when I try to boot my Win XP:

[COLOR=Red]Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please re-install a copy of the above file.[/COLOR]

I´ve been reading lots of forums today(at work!) and printed out some solutions that I´ll try later today.[/QUOTE]
 Thank you rthunstrom, I 'll try to follow your directions.

---

### Post by ikoyk on 2004-12-01
[QUOTE=ikoyk]Thank you rthunstrom, I 'll try to follow your directions.[/QUOTE]
 Thank you very much my friend rthunstrom, I followed your directions and I managed to edit menu.lst and apply grub loader to my needs. I was also wondering if there is  a way to take a backup of this boot loader, so as to be able to run the program from a diskette. Anyway, I did what I wanted, thank you again for your help.

---

### Post by rthunstrom on 2004-12-01
You´re welcome ikoyk!


I just solved my problem with "..<Windows root>\system32\hal.dll".

I changed partition number in boot.ini in MS Windows. Before it was 3, now it is 4 and voila!

---

### Post by UnCola on 2007-08-13
Hi I had this dual boot installation problem, I was thinking hal.dll is the famous Hal from 2001, it was driving me mad.

I was preparing a Windows reinstall anyway, good thing too cause the default guided installation made windows unusable.  Every XP reinstall worked but prevented Linux even appearing in boot list, and every linux re install created the hal.dll problem again.

Before trying the more technical approaches I tried the manual partitioning option on the Desktop CD  a few times.  Finally I tried the option of making it the last - not first - on the drive.

That worked - windows and linux both boot up fine.

Thanks to the person who mentioned on here somewhere that windows is confused if it isn't the first thing it comes to, that gave me the idea.

I've used Linux solo on a laptop just fine , but this dual boot install took a lot of time.

---

### Post by rekvijem on 2008-07-10
Heloo. I have been reading all of these threads on dual boot and hal.dll missing but I just can't get my to work.

I have a WinXP installed and a Ubuntu later. This is my result on fdisk

--------------------------------------------------
[SIZE="0.3"]Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32c032bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3885        5100     9767520   83  Linux
/dev/sda2   *        5101        7296    17639370    7  HPFS/NTFS
/dev/sda3            3642        3884     1951897+  82  Linux swap / Solaris
/dev/sda4               1        3641    29246301    b  W95 FAT32

Partition table entries are not in disk order[/SIZE]
------------------------------------------------------------------------

And now I'm not sure what is it that I need to change in GRUB's menu.lst file to make it work.

This is the end of my menu.lst file:

--------------------------------------------------------
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0688be71-a3e7-4fe4-9d06-9b9299c4dd92 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0688be71-a3e7-4fe4-9d06-9b9299c4dd92 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
----------------------------------

I appreciate every help and excuse me if this is already been explained, I really tried to find it but I couldn't.

---

### Post by Sand Lee on 2008-07-10
Try removing the savedefault and makeactive lines from the windows entry - usually solves my problems. However, I do not get missing hal.dll errors.

---

### Post by rekvijem on 2008-07-10
Tried.. unfortunatey problem stays..

---

