---
title: "Grub help"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by Cyfr on 2005-08-11
Theres loads of threads with this already but for the life of me every one ive found hasnt helped.

I get 'GRUB Hard Disk Error' when I try and boot up after a fresh install. Im using a Toshiba Qosmio F10 laptop which I purchased only a few months ago so it's not old, however I can't seem to find that mode on my bios anywhere.. 

Any suggestions?

---

### Post by amohanty on 2005-08-11
GRUB Manual:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Your error:Hard Disk Error
    The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed. 

Try setting all recognized HDDs in your CMOS setup to be auto.

AM

---

### Post by Woodman on 2005-09-13
Loads of threads with this problem, some connected to dual-boot, some not. Mine isnt.

Im installing ubuntu-server as a single OS install on an old computer. (233 mhz 128 mb ram). The installation goes perfectly until reboot when I get 'GRUB Hard Disk Error'.

I know what this means and have tried both entering the hdd-values manually and letting the bios take care of it automatically, none of them works. I can boot perfectly from a floppy so I tried installing lilo instead, didnt work either, didnt get an error message but it wouldnt boot. I have no option for LBA in the bios but the harddrive is only 4gb. Tried commenting out lba32 in the grub config but that didnt work either. Worth mentioning is that earlier today I had a working windows 98 on the computer so the MBR part of the hdd shouldnt be damaged or anything like that.

Any and all ideas are appreciated :)

---

### Post by souki on 2006-03-30
I'm trying to install ubuntu (dapper flight5) on a Qosmio G10
same grub problem "GRUB Hard Disk Error"

I can boot from the dapper install cd choosing "boot from first hard drive"
I've tried to setup grub again with no success
```
root (hd0,0)
setup (hd0)
```

there is two hard disks on this laptop, I've choosen /dev/hda during install stage

any idea ?

---

### Post by rooreleased on 2006-05-09
Cyfr,

Uninstall the QosmioPlayer - grub will start to work again. To uninstall QosmioPlayer I believe you need to use the recovery CD/DVD that came with your laptop.

I have a Qosmio F20 and it doesn't suffer from this issue, perhaps this might be useful to you should you wish to contact Toshiba about this?

Have you tried Lilo as the boot manager by the way? Could be worth a shot.

---

