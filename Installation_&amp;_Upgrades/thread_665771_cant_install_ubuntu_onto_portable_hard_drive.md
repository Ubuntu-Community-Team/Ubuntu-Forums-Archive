---
title: "cant install ubuntu onto portable hard drive"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by dzuari on 2008-01-12
im new to linux and dont kno to much about all this but heres my problem.

Iv been trying to get Ubuntu onto my portable hard drive, and i have followed the instructions on pendrivelinux.com but when disengage my internal hard drive and reboot with just my portable hard plugged in my computer will start to read the cd with something that looks like this

DHCP.....
PXE-E53: no boot filename recieved
PXE-MOF
invalid partition table


i have been able to run Ubuntu through Qemu but id like to just be able to boot from my portable hard drive.

-Iv download the Ubuntu 7.10desktop and Alternate and put them both on a CD-R
-changed my portable hard drive from FAT32 to NTFS
-formated my portable hard drive through Com prompt

my comp is a Gateway GT5468
my portable hard drive is Western Digital passport

---

### Post by jcwmoore on 2008-01-12
The Master Boot Record is the first thing your computer looks for when it starts loading an OS, now when you install ubuntu the Grub boot loader is loading into the MBR.  The MBR is actually stored on you main hard Drive, the one you disconnected...  just plug it back in and you should boot in to a menu with all the avaliable OS's, just go the to the ubuntu and hit enter and you should be off to the races...

---

### Post by jcwmoore on 2008-01-12
Hold on, I think I may have misunderstood... so do you actually have ubuntu installed on the external HD yet?

---

### Post by dzuari on 2008-01-12
no i dont, im running off XP but i bought the comp with vista and partitioned 120G to XP, pain in the ***, and i also cant find my other 280G :) but atleast i dont ahve vista now

---

### Post by dzuari on 2008-01-12
im also putting debian on a CD right now, this is a noob question but u extract the files out of the zip folder then put them on a CD right, or do u just put the whole zip file on the CD, iv been extracting then putting all the files on the CD

---

### Post by jcwmoore on 2008-01-12
ok, that sounds like at BIOS issue....  now before you messing with the bios boot order, plug the main HD back in and stick the CD in.  if you go to windows then you will need to reorder the BIOS boot order to boot from CD first USB drive second (but this is not important untill the install is finished) and internal HD 3rd.  now also if you have this 280G "Lost" in the HD you may want to considering installing Ubuntu to some of that space.  You should be able to see that space in the Partition Editor on the Live CD...  research Dual Booting with XP and Ubuntu.  you can find lots of info on how to do it right on the forums or by googling it

---

### Post by dzuari on 2008-01-12
im running off my Internal HD right now, if i have my internal HD pulgged in my comp will just automaticly boot to XP and i do have my boot set up 1.CD 2.USB 3.HD, does ubuntu 7.10 come with Grub on the CD?

---

### Post by wolfen69 on 2008-01-12
the portable drive must be fat32 not ntfs.

---

### Post by dzuari on 2008-01-12
k

---

### Post by dzuari on 2008-01-12
ummm... its not letting my convert my drive back to FAT32 through com prompt

---

### Post by swimmerbody on 2008-06-26
I had good experience when installing in a portable hard drive but the same experience as the initial post when installing onto a new Western Digital Hard Drive.  

With Supergrub I am able to boot and run the western digital hard drive but there is something about this particular piece of hardware that makes it loose the grub or the mbr.  I will pursue the answer.  

I am interested in learning of any experience similar.

---

