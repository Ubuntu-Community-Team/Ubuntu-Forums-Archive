---
title: "ubuntu 7.10 fails to load after install"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by drahcirybbob on 2008-03-07
got my ubuntu cd from the mail (7.10) the other day and started messing with my computer. i'm planning to use the entire disk solely for ubuntu (no other OS's or dual boot.) 

followed the instruction for install using guided - entire disk setup. the setup went well, but after the reboot, the splash screen would display with a tiny bar at the beginning and would sit there forever. tried reinstaling it trice now but still stuck on the same screen.

tried both cds (64 bit edition and the pc edition), still getting the same result.
i'd also tried installing the alternate cd (cd integrity - OK), but still getting the same result.

--------------------------------
here is my system specs:
AMD Athlon 64 3000+
1G RAM
40G HDD PATA

---

### Post by Pumalite on 2008-03-07
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by taurus on 2008-03-07
What graphic card and monitor do you have?  Try booting into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by drahcirybbob on 2008-03-07
> **Pumalite said:**
> Boot your Live CD and post:
sudo fdisk -lu


here is the result and let me correct my previous info, looks like i only have 30GB HDD, sorry.


GB Disk /dev/hda : 30.7 GB 3075003182 bytes
255 heads, 63 sectore/track, 3738 cylinder, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier : 0x029ce29ce

Device         Boot          Start            End        Blocks     Id     System
/dev/hda1          *             63   57496634   28748286     83     Linux
/dev/hd2                57496635   60050969   1277167+      5     Extended
/dev/hd5                57496698   60050969    1277136      82     Linux Swap/Solaris

---

### Post by Pumalite on 2008-03-07
I imagine you are at the Live CD. Mount your partition. At the Terminal:
sudo mkdir /media/hda1
sudo mount -t ext3 /dev/hda1 /media/hda1
Now, from that partition; post:
cat /boot/grub/menu.lst

---

### Post by drahcirybbob on 2008-03-07
> **taurus said:**
> What graphic card and monitor do you have?  Try booting into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```


i'm using an onboard graphics card (GEForce 6100) and a CRT monitor (<- not sure about this answer if thats the info you need)

i run that code, not sure if i did it on the place where it should be, but i run it where the console stops, it did nothing. i assume it should reboot the whole system, but it did not.

by the way, this might help: on the latter part of the recovery console. i got this series of info:

[29.256631] ide : failed opcode was : unknown
[29.300460] hda : dma_intr : status = 0x51 {DriveReady Seek Complete Error}
[29.010079] hda : dma_intr: error = 0x84 {DriveStatus Error BadCRC}

---

### Post by drahcirybbob on 2008-03-08
> **Pumalite said:**
> I imagine you are at the Live CD. Mount your partition. At the Terminal:
sudo mkdir /media/hda1
sudo mount -t ext3 /dev/hda1 /media/hda1
Now, from that partition; post:
cat /boot/grub/menu.lst

after typing > sudo mount -t ext3 /dev/hda1 /media/hda1
this message came up:
mount: special device /dev/hda1 does not exist

---

### Post by Pumalite on 2008-03-08
From your fdisk:
'/dev/hda1 * 63 57496634 28748286 83 Linux'

---

### Post by drahcirybbob on 2008-03-09
> **Pumalite said:**
> From your fdisk:
'/dev/hda1 * 63 57496634 28748286 83 Linux'


yes, thats from sudo fdisk -lu comand.
its the table but i just copied it and it didnt look like a table after i pasted it.
heres how it should look like..

```

GB Disk /dev/hda : 30.7 GB 3075003182 bytes
255 heads, 63 sectore/track, 3738 cylinder, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier : 0x029ce29ce

Device        Boot     Start          End      Blocks     Id     System
/dev/hda1       *         63     57496634    28748286     83     Linux
/dev/hd2            57496635     60050969    1277167+      5     Extended
/dev/hd5            57496698     60050969     1277136     82     Linux Swap/Solaris

```

---

### Post by Pumalite on 2008-03-09
Check your commands. /dev/sda1 does exists.
Copy and paste in the Terminal the commands I gave you.

---

### Post by drahcirybbob on 2008-03-10
yes i did copy & paste it.
i typed/pasted:
```
sudo mkdir /media/hda1 
``` 
then it went down to the prompt
then i typed/pasted:
```
sudo mount -t ext3 /dev/hda1 /media/hda1
```
this message came up:
mount: special device /dev/hda1 does not exist

---

### Post by Pumalite on 2008-03-10
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Post a screenshot

---

