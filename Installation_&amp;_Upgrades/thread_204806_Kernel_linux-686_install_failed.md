---
title: "Kernel linux-686 install failed??"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by CaptSammy on 2006-06-27
I ran sudo apt-get install linux-686
and on rebooting and selecting this new entry in grub I get:
preparing restricted drivers            failed
Then all drops to command.

My system is running fine with the 386 kernel with:
Celeron D Processor
nVidia video card
Soundblaster
1G memory

Any help appreciated

---

### Post by LordRaiden on 2006-06-27
[quote=CaptSammy]I ran sudo apt-get install linux-686
and on rebooting and selecting this new entry in grub I get:
preparing restricted drivers            failed
Then all drops to command.

My system is running fine with the 386 kernel with:
Celeron D Processor
nVidia video card
Soundblaster
1G memory

Any help appreciated[/quote]


You need to install the restricted drivers module for linux-686, so something like linux-restricted-modules-2.6.15-25 or something like that.

dothe following the shell:

```
sudo apt-get install linux-restricted 
```

and press the **TAB** key a few times. Find the one that matches your kernel and cpu architecture and install it, then reboot (sudo reboot).

---

### Post by CaptSammy on 2006-06-27
Did the above suggestion, installed the restricted, but the same failure. I do note however that it states in the commend error text it cant find hda4, bad block or some such. Works fine with my 386 kernel when I reboot and select my 386 kernel from the grub menu.
I think the relevant error is following the attempt to start the restricted:
mkdir: cannot create directory '/lib/modules/2.6.12-10-686/volitile': read only file system.
I didnt set any file attributes, this is a newly install system (Dapper)

---

### Post by LordRaiden on 2006-06-27
How many partitions and hard drives do you have?
 
Go into a shell and do
 
```
cat /etc/fstab 
```
 
and please copy and paste the contents here.

---

