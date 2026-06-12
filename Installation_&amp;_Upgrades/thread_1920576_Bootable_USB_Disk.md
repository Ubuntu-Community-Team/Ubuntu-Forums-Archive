---
title: "Bootable USB Disk"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by Shubham Sharma on 2012-02-05
Hello people!
I came across a strange problem when i made a bootable usb disk for installing Ubuntu 11.10 on my laptop. I had a 2gb sony micro sd card which i used for making bootable usb disk. after installation when i tried to format it to normal, it only frees 695 mb (exactly the size of ubuntu setup) and after many tries i couldn't recover the rest of the memory on the card. Can anyone help me out please... :(

---

### Post by Shubham Sharma on 2012-02-05
Hey problem solved! thank god... sigh :)

---

### Post by bogan on 2012-02-05
Hi! [B]Shubham Sharma,
[/B]
You Posted:> Hey problem solved! thank god... sigh :smile: Please let us in on the secret.

I have exactly the same problem, only with an_** 8GB **_USB stick!!

What did you do to access the full memory??

Chao!, **bogan**.

---

### Post by Shubham Sharma on 2012-02-05
Dude the solution is pathetically simple :\
When we create a USB bootable disk, it actually makes one more RAW partition in the disk which is the Ubuntu image, rest space is unallocated. To access that memory go to any windows xp/vista/7, plug in your device and go to disk management, there you'll see your USB drive and if you click on it, you'll graphically see the actual cause of the problem. :)
To access that memory delete the RAW partition and then make new partition with all the available memory and format it in desired format :)

PS- i think i got carried away and wrote too much :P lol :D

Ciao! :)

---

### Post by Shubham Sharma on 2012-02-05
i'm sure there must be a similar disk management tool in Ubuntu too but i didn't tried it as yet, so i rely on Window's one for the time being :)

---

### Post by sudodus on 2012-02-05
> **Shubham Sharma said:**
> i'm sure there must be a similar disk management tool in Ubuntu too but i didn't tried it as yet, so i rely on Window's one for the time being :)
I suggest that you try ***Gparted*** in Ubuntu next time.

---

### Post by Shubham Sharma on 2012-02-05
ok dude! :) will check it out as i get time

---

### Post by bogan on 2012-02-05
Hi!, **sudodus**,

I used the Disk Utility and it showed the whole 8GB USB Disk as W95 Fat32 (0x0b), available ghosted and '-'.

Check File System showed: "Partition 1 check completed. System is clean."

I have not yet tried gparted as I did not want to disturb the LiveUSB installation.

Win7 showed it as 7.45GB FAT32,  Healthy(Active,Primary Partition), 855MB used, 7GB free.

I am puzzled an confused.

Chao!, **bogan**.

---

