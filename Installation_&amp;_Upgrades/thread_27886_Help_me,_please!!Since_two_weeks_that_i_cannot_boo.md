---
title: "Help me, please!!Since two weeks that i cannot boot Windows"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by look on 2005-04-18
Hello!!
 ](*,) this how i look like now!!!

I installed ubuntu two weeks ago, and the installation was good. Linux works very good, and i can access into my two NTFS windows partition from linux.
The command I use to mount it is:
sudo mount /dev/hda1 /mnt/windows
so windows is in the partition hda1 that is (hd0,0) for grub.

I will write now the content of /boot/grub/menu.lst

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

title		Other operating systems:
root

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

As i said, when launching linux there are not problems, but when launching Windows, it appear a black screen with a flashing cursor on the top left.

Any suggestion?
Thank you!!!

---

### Post by TravisNewman on 2005-04-18
In the section for XP, change
root (hd0,0)
to
rootnoverify (0,0)

grub can't mount NTFS

If that doesn't work, and it may not (this could be one of a few problems), try going into your bios and setting the access mode of the hard drive to LBA or Large.

---

### Post by Dr Gonzo on 2005-04-18
You didn't *write* anything to your NTFS volumes, did you?

---

### Post by TravisNewman on 2005-04-18
[QUOTE=Dr Gonzo]You didn't *write* anything to your NTFS volumes, did you?[/QUOTE]
 Gonzo has a point. Unless you're using Captive NTFS, writing to those drives could have screwed them over insanely.

---

### Post by look on 2005-04-19
No, I didn't write anything in my NTFS HD. As soon I installed Ubuntu I couldn't boot Windows. I already tried everything you told me to do.. But nothing.
Thanks anyway.
I hope someone can solve this problem  :???: 
Ciao.

---

### Post by laka on 2005-04-19
Hmm, can you really write to NTFS at all? Tought you just got an error... Didn't think that it would have any affect.

---

### Post by fdejkmtruds on 2005-05-09
[QUOTE=laka]Hmm, can you really write to NTFS at all? Tought you just got an error... Didn't think that it would have any affect.[/QUOTE]
 You can't write to ntfs in Ubuntu out of the box. You'll have to download captive to do that.

---

