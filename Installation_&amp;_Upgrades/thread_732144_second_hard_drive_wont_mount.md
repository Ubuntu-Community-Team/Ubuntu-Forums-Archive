---
title: "second hard drive wont mount"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by cowboyup02119 on 2008-03-22
hello to all!!!

i just killed vista because i got the blue screen of death six times, while installing and doing updates....

i install everything in my first hard drive and did all the updates and got all the drivers...thanks to developers who including everything in the updates you all are awesome!

i have a second hard drive 500GB with only media on operating system on it. when i go to places>computer

i can see my second hard drive but when i click to open it says CANNOT MOUNT VOLUME.
> UNABLE TO MOUNT THE VOLUME "MEDIA FILES" thats the name of second hard drive, i have like 10 GB of music and over 200GB of DVD's saved there. is there any way to recognize it and use my media on there...

thanks to all you can help and god bless!
__________________

---

### Post by tvtech on 2008-03-22
what does your fstab config look like?

in terminal 

user@localhost:~$gksu gedit /etc/fstab

---

### Post by cowboyup02119 on 2008-03-22
dont know what that means when i go applications.accessories.terminal 

all thats there is 

eldin@mini-beast:~$

---

### Post by fela on 2008-03-22
he means when you see that text, type ```
gksu gedit /etc/fstab
```

and then enter. 

I would suggest trying to mount the drive manually with the terminal, as nautilus sometimes plays up. type ```
sudo fdisk -l
```

in terminal and give me the output, so i know what device the 500gb drive is. Once you know the device (e.g. /dev/sda), type ```
sudo mkdir /mnt/media_500gb && sudo mount -t <filesystem type, e.g. vfat is FAT16> <device e.g. /dev/sda> /mnt/media_500gb
```

for what i just told you, you need to know exactly what your doing, as you could all to easily end up bricking your system and losing your data. You have been warned. Btw, the < and >s in that command aren't supposed to be there, i just did that to emphasize that they were variables and you replace them with the appropriate values.

---

