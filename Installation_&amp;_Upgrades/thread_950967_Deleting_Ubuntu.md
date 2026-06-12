---
title: "Deleting Ubuntu"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by ajmannen on 2008-10-17
hi guys, I've just got myself a brand new computer, and it is going to be Ubuntu only. So I'm going to delete Ubuntu on my laptop to free some HDD space. Only problem is that my laptop is a Acer, and Acer somehow found out that built in recovery partition is better then CD ....and GRUB blocks the built in recovery partition >_< 

So, I want to delete Ubuntu, but I do not have the recovery CD. All I do have is the Ubuntu CD. Anny suggestions

---

### Post by Pumalite on 2008-10-17
I imagine you are happy with Ubuntu and have saved your data. Just install and choose 'Guided>Use Entire Disk'

---

### Post by reinaldistic on 2008-10-17
without the recovery cd there may be dificulties, you may want to get the recovery cd by buying it

there are free ways to get your old os cd but they are illegal

---

### Post by Pumalite on 2008-10-17
Is it going to be only Ubuntu or dual boot? Your first post is confusing.

---

### Post by ajmannen on 2008-10-17
So, is there no way to just ..delete the Ubuntu partition/files and then go into Ubuntu Live CD and remove GRUB?, I need Vista for school work (yes we have certain applications we MUST have ..and none of them are Linux compatible :/)

---

### Post by Patrick793 on 2008-10-17
Really? The only MS only program we use at my school is Microsoft Office, and for us with Linux/Mac, they reccomend Open Office.

If your laptop has Vista, boot into Vista, and download EasyBCD. Use that program to restore the boot loader to Vista's. After that, boot the Ubuntu cd and delete the Ubuntu partition, then resize the Vista partition.

---

### Post by ajmannen on 2008-10-17
I have IT class and we have some applications made by the government for us, and they only work under Windows. We also learn how to use Adobe products like Flash, DreamWeaver and PhotoShop ..and as far as I know they don't work to well under Linux

---

### Post by Pumalite on 2008-10-17
'hi guys, I've just got myself a brand new computer, and it is going to be Ubuntu only'

???

---

### Post by ajmannen on 2008-10-17
what? I wrote that my old computer should be Windows only aswell ..making the laptop at school PC. So I want only vista on it, but have no Vista CD ..get it?

---

### Post by Herman on 2008-10-17
> Only problem is that my laptop is a Acer, and Acer somehow found out that built in recovery partition is better then CD ....and GRUB blocks the built in recovery partition >_< 

So, I want to delete Ubuntu, but I do not have the recovery CD. All I do have is the Ubuntu CD. Anny suggestions:) I don't think that GRUB actually 'blocks' the 'Recovery Partition' does it?
In my Acer laptop it's not listed in the GRUB menu, but I think if I made an entry to chainload the Recovery partition it would boot okay. That would then probably erase Ubuntu and all your data though. I'm not sure, I've never used my Acer Recovery partition.

If you have Windows Vista but you don't have any Windows Vista Installation disc you can go download a 'Vista Recovery CD'. [B]
**See lswest's and bodhi.zazen's thread**[/B], [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB ]("http://ubuntuforums.org/showthread.php?t=740221")

Regards, Herman :)

---

### Post by ajgreeny on 2008-10-17
If I understood you properly your difficulty is that you don't have a windows install CD to restore the windows MBR on your laptop from which you are deleting ubuntu.  If I remember correctly you can restore the MBR using the Supergrub recovery CD which you can download from the internet.  Do a better search and I think you will find a way quite easily.  Once you have restored that you can then use gparted on the ubuntu live CD to enlarge the windows partition, or do you mean you deleted the windows partition completely?  If so I think you may need to get in touch with Acer for a recovery CD.

---

