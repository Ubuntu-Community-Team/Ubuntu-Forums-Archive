---
title: "floppy boot GRUB to .iso file on a FAT32?"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by brallan on 2005-11-12
I wanna dual boot XP/linux on an older laptop (DELLinspiron4000 PIII 128M ram 20G HD USB1.0, floppy, no CD drive) i've FIPSed 8 G of free FAT32 on the drive. 

I've got both the live and install Hoary Hedgehog cds at home but I have an external USB CDRW that is NON-BOOTABLE. i even flashed the BIOS, no luck. No broadband for a network install. 

I'm figuring the easiest way to install is to rip an ISO file to the XP partition, (or copy all the files from the CD onto it) and get GRUB on a floppy (im afraid to touch the MBR as i cannot rebuild XP - no CDs)  to boot to it. 

can anyone help me modify ed_agamemnon 's excellent post:
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)
HOWTO: Install Ubuntu Linux without burning a cd  (about using GRUB to start a network install) - to work with an iso file on the C: drive?. One problem i forsee is that the linux.bin file isn;t on the disk. Can i use isolinux.bin in place of it or do i need to download?

everything i read about grub is like Egyptology. AAAARGH! I MUST get GEEKIER....

i'd be grateful just to get this thing going, failed attempts at defragging and repartitioning and redoing the BIOS and googling everything has taken this newbie DAYS!

brian

---

### Post by brallan on 2005-11-12
i mean, i guess what im asking is, with these files:

c:/boot/     :    isolinux.bin, initrd.gz

c:/Ubuntu_Live_CD/Ubuntu_Live_CD.img

and this entry (in menu.lst):

```
title Ubuntu_Live_CD
kernel (hd0,0)/boot/isolinux vga=normal ramdisk_size=14972 root=/Ubuntu_Live_CD 
initrd (hd0,0)/boot/initrd.gz
```

why does GRUB say file not found?

grub does boot XP (from the floppy) OK...

WHAT AM I DOING WRONG?

---

### Post by jkil on 2005-11-13
hi:

i also met some problem in installation, however,i can basically figure out, only[B]kernel (hdX,Y)/vmlinuz[B] is valid, but not isolinux.

---

### Post by yesplease on 2005-11-13
@Brallan: there is a Howto to install from floppy [https://wiki.ubuntu.com/Installation/WithFloppies?highlight=%28install%29](https://wiki.ubuntu.com/Installation/WithFloppies?highlight=%28install%29) wich points to this [https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

I have never tried this but perhaps it can help you because you have a floppy disk.

---

### Post by brallan on 2005-11-13
well, in the end i got frustrated and just took the laptop to a network connection and did a network install. thanks for trying to help, all. I also found an interesting link, this fellow Balajint seems to have managed booting the ubuntu live CD via his hard disk:

[http://ubuntuforums.org/showthread.php?t=79319](http://ubuntuforums.org/showthread.php?t=79319)

but MAN am I  happy to have a linux laptop!!!! 

now if only i could get my external serial mouse to work...

---

