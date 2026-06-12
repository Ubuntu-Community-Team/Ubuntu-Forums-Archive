---
title: "Good partition set up"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by flummoxed on 2006-03-14
For future reference in installing of ubuntu, I'm interested in knowing what a good way to set up partitions would be. I have an 80GB SATA hard drive for ubuntu (ubuntu seems to recognize about 76GB of that). Now, when I type in df -h in the terminal, I get this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  5.1G   62G   8% /
varrun                506M   84K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  136K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/hda1              75G   49G   26G  66% /media/hda1

When I installed Dapper, I got it to auto partion, and it gave me a big Sda1 partition and a 3.2 GB swap file (I think it was that big). So ubuntu automatically creates varrun, varlock, udev, and devshm? 

Here's what I've come up with:

1 GB for /
5 GB for /usr
20 MB for /boot
30 GB for /home
5 GB for /backup

What should I use the rest of of the space for?

---

### Post by flummoxed on 2006-03-15
Suggestions?

---

### Post by Sutekh on 2006-03-15
[QUOTE=flummoxed]I have an 80GB SATA hard drive for ubuntu (ubuntu seems to recognize about 76GB of that). [/QUOTE] You probably lose some to formatting and some to marketing ploys.

Sometimes manufacturers say 80GB (80*1024*1024*1024 = 85,899,345,920 bytes) when they really mean 80 billion bytes (80,000,000,000 bytes), which is obviously less.  Anyway to your real question


[QUOTE=flummoxed]
1 GB for /
5 GB for /usr
20 MB for /boot
30 GB for /home
5 GB for /backup

What should I use the rest of of the space for?[/QUOTE]
Firstly I'd give a bit more to /,  but that depends on how much goes in /usr.  If /usr gets 5GB then maybe / only needs 1GB, I'm not really sure.

/boot needs more than 20MB to be sure.  /boot is where the kernel images reside (and they are fairly big, I'm sure they are around 20MB each, and if your ever want more than one it could get tricky.)

30GB for /home looks okay, and 5GB for /backup sounds fine.

I'd also plan to give about 1.5 times the size of your RAM to /swap.  3.2GB is *massive* and very unlikely to ever get used.  I have way too much swap (2.5GB) in my system (I have way to much HDD space so I didn't mind), and with 1GB of RAM, my swap is barely touched (100-200MB maximum)

If you have left over space then I'd use it as extra space for /home or maybe a /multimedia partition, or even a /shared partition (FAT32) if you dual-boot with Windows.

---

### Post by flummoxed on 2006-03-16
Yeah, I already knew about the marketing ploy thing. It's kinda stupid, they should give what they advertise.

So 1.5 GB for the swap? I have a GB of RAM... it sounds good to me. A shared partition is a good idea too, never though of that. I'll be sure to put more for the kernel as well. This should be useful for the next time I format. Thanks. :)

---

