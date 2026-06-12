---
title: "Error 15"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by Fredk on 2008-10-29
I have an Eee PC with Xandros installed. I have Ubuntu on an SD card which I can also boot to. I did an update which was enormous - I do not know what was changed. (I am a complete novice with Linux).  But now I cannot boot to the present Ubuntu kernel but I get Error 15.  When I attempt any other kernel in the list the same occurs. 
Can anyone help me to get out of this loop?

Fredk

---

### Post by caljohnsmith on 2008-10-29
Just to clarify, you mean a Grub error 15, is that true? If so, how about first posting:
```
sudo fdisk -lu
```
Figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -l /mnt/boot
sudo blkid
cat /mnt/boot/grub/menu.lst
```
And note "-l" is a lowercase L, not a one. We can work from there if you want. :)

---

### Post by Fredk on 2008-10-30
> **caljohnsmith said:**
> Just to clarify, you mean a Grub error 15, is that true? If so, how about first posting:
```
sudo fdisk -lu
```
Figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -l /mnt/boot
sudo blkid
cat /mnt/boot/grub/menu.lst
```
And note "-l" is a lowercase L, not a one. We can work from there if you want. :)

Forgive my ignorance - but I am not sure which of the two Linux partitions is the Ubuntu on my SD card.
I copied this from Terminal after entering "sudo fdisk -lu"
:

eee@anon:~$ sudo fdisk -lu
[sudo] password for eee: 

Disk /dev/sda: 4001 MB, 4001292288 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7815024 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfda3fda3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     4819499     2409718+  83  Linux
/dev/sda2         4819500     7775459     1477980   83  Linux
/dev/sda3         7775460     7791524        8032+   c  W95 FAT32 (LBA)
/dev/sda4         7791525     7807589        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 8201 MB, 8201961472 bytes
255 heads, 63 sectors/track, 997 cylinders, total 16019456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x514e3341

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    12450374     6225156   83  Linux
/dev/sdb2        12450375    15727634     1638630    5  Extended
/dev/sdb5        12450438    13478534      514048+  82  Linux swap / Solaris
/dev/sdb6        13478598    15727634     1124518+   b  W95 FAT32
eee@anon:~$ 

How do you suggest I proceed?  (I am an old DOS man but a complete novice with Linux/Unix.)  I would guess its sda2 .
Fredk.

---

### Post by caljohnsmith on 2008-10-30
So is the Ubuntu SD card the 4 GB or 8 GB drive? If it's the 4 GB drive, then please do:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
df
ls -l /mnt/sda1 /mnt/sda2
```
Note "-l" is a lowercase L, not a one.

---

### Post by Fredk on 2008-10-30
> **caljohnsmith said:**
> So is the Ubuntu SD card the 4 GB or 8 GB drive? If it's the 4 GB drive, then please do:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
df
ls -l /mnt/sda1 /mnt/sda2
```
Note "-l" is a lowercase L, not a one.

It's the 8 GB Drive

---

### Post by caljohnsmith on 2008-10-30
OK, please post the output of:
```
sudo mount /dev/sdb1 /mnt
df
sudo blkid
ls -lR /mnt/sdb1/boot
cat /mnt/boot/grub/menu.lst
```
And when you post the results, please highlight the text and press the pound sign # graphic at the top of the message box to put code tags around the text.

---

### Post by Fredk on 2008-10-30
> **caljohnsmith said:**
> OK, please post the output of:
```
sudo mount /dev/sdb1 /mnt
df
sudo blkid
ls -lR /mnt/sdb1/boot
cat /mnt/boot/grub/menu.lst
```
And when you post the results, please highlight the text and press the pound sign # graphic at the top of the message box to put code tags around the text.

This produces a scary lot of text and I'm not sure at all what I am doing. The last time (first and only) that I reproduced text was by copying and pasting - first into a text file and from there into my Message.
Also I think the £ sign on my (U.K.) keyboard is a # sign.
Is there a simpler way of getting the output copied into my message?
Last question - in following your above instructions is anything "saved" and thus changed?

---

### Post by caljohnsmith on 2008-10-30
> **Fredk said:**
> This produces a scary lot of text and I'm not sure at all what I am doing. The last time (first and only) that I reproduced text was by copying and pasting - first into a text file and from there into my Message.
Also I think the £ sign on my (U.K.) keyboard is a # sign.
Is there a simpler way of getting the output copies into my message?
Last question - in following your above instructions is anything "saved" and thus changed?
Yes, it will produce alot of text, but you should be able to do exactly as you did before by copying/pasting the text. Also, the pound symbol I'm talking about is the pound sign graphic at the top of the ubuntuforums.org message box in your browser, not your keyboard. And none of the commands will change anything permanently, they only give info I need to help you. :)

---

