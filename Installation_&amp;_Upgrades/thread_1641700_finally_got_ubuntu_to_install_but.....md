---
title: "finally got ubuntu to install but...."
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by kitoisara on 2010-12-09
i dont have vista anymore on my computer and ubuntu doesnt work to well on my computer and i followed steps that some ppl gave me to duel boot my system but i dont know what happened adn there is no more vista and i want to have it back so does anyone know how to get windows vista home premium 32 bit back on my computer or can i download another vista OS somewhere for free

---

### Post by Megaptera on 2010-12-09
You can't get a free legal copy of Vista. Do you have restore discs if thry become necessary?

Post the output of

df -h
fdisk -l

from terminal to show people here what your partition set up is & if Vista is there somewhere.

---

### Post by kitoisara on 2010-12-09
well i had a recovery disk and used it earlier but it says it cant find anything in my system to recover it cant find anything thats windows vista so i think i have to just re install the whole OS but i dont want to pay for somthing since i had it one time before but i dont know

---

### Post by Megaptera on 2010-12-09
Where are you writing from now? Your Ubuntu system or somewhere else?

If you are in Ubuntu can you go to Menu > Applications > Acessories > Terminal and type in 

df -h
fdisk -l         (that is a small l not figure one 1) 

then cut & paste the result in an answer here please.

If you use a pirated copy of Windows it'll probably crash & trash ... and no decent forum will help you with fixing it.

---

### Post by kitoisara on 2010-12-09
Nahh im not at my system now i ll post it up when i get home and let u know and it was a windows computer it had vista already installed on it i just wanted to try out ubuntu

---

### Post by kitoisara on 2010-12-10
ok this i what i got 

  df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              19G  8.6G  8.9G  50% /
none                  1.5G  312K  1.5G   1% /dev
none                  1.5G  248K  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G  4.0K  1.5G   1% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw

fdisk -i
fdisk: invalid option -- 'i'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

i have no clue in what this mean really

---

### Post by Megaptera on 2010-12-10
Nor me! Let's see if someone else can help ...

Anyone out there?

---

### Post by sikander3786 on 2010-12-10
> or can i download another vista OS somewhere for free

That is called piracy and piracy is not allowed on the forums. See [Forum CoC.]("http://ubuntuforums.org/index.php?page=policy")

Regarding your issue with Vista, to see if it is still there, you need to post the output of this command.

```
sudo fdisk -l
```

Note it is a lower-case L and not i at the end of that line. Linux is case sensitive and you also need to put in sudo in the beginning of that line.

---

### Post by kitoisara on 2010-12-10
sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069598

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       27970       30402    19530753    5  Extended
/dev/sda5           27970       30402    19530752   83  Linux

---

### Post by sikander3786 on 2010-12-10
There is no Windows partition. So Windows is gone. You need to re-install once you grab a licensed copy ;-)

---

### Post by kitoisara on 2010-12-10
much appreciated i ll see what i can do.

---

