---
title: "Live CD not letting me install"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by A S C on 2010-05-01
After following nucleuskore's [post]("http://ubuntuforums.org/showpost.php?p=9195971&postcount=14"), I am finally able to boot the live cd. Just a few minutes ago I tried to install ubuntu. I got past partitioning my hard drive, and after I typed in my user/pass and pressed enter the install window just closed on me, without any error.

I noticed when I had chosen my password, it said it was "too short" but I went ahead anyway. So thinking that was the problem, I tried installing it again, making my password longer, but that didn't help either. What can I do now to try and install ubuntu?

---

### Post by necromonger on 2010-05-01
Did you check the disk for errors?

---

### Post by A S C on 2010-05-01
Before burning I checked the md5sum and that checked out, so the iso itself is fine.

I tried checking the disk for errors earlier when I couldn't figure out why my monitor wasn't working, but I ended up getting that same "black screen".

I'm running off the live cd right now and everything else seems to be working perfectly. I'm going to try and install it again. This time around I used GParted by itself instead of using the partition manager in the Ubuntu install. I had Arch Linux before, but I erased those partitions and re-made them (swap, /, /home) so hopefully it will work this time around.

---

### Post by razy60 on 2010-05-01
> **A S C said:**
> 

I'm running off the live cd right now and everything else seems to be working perfectly. I'm going to try and install it again. This time around I used GParted by itself instead of using the partition manager in the Ubuntu install. I had Arch Linux before, but I erased those partitions and re-made them (swap, /, /home) so hopefully it will work this time around.
 Personaly i would have used gparted to erase all partitions,reformatted the drive to either fat32 or ext3, then restarted the PC and installed from there as a fresh install on a clean drive. 
The one problem i have on my Pc is that 10.04 insists on trying to install on my second drive which is used for storage it ignores drive A unless i actually remove drive B from the case(unplug it actually), it then installs fine in the space provided,(i have 3 OS's).

Raz

---

### Post by A S C on 2010-05-01
Well, using GParted worked. I left to let Ubuntu install, expecting to come back with it finished, instead I see this error:

[IMG]http://img228.imageshack.us/img228/8685/screenshotob.png[/IMG]

I'm positive it is not because of the CD, I think it is because of my drive. It can't burn CDs anymore (used my bro's pc to burn ubuntu) and I can't really think of a time I've ever used it since it stopped burning CDs. I have to use a USB drive to install it now right? I used to use a program in the past called Unetbootin, but it only seemed to work with 32-bit distros for me. Maybe it is changed now to work with 64-bit, guess I will have to look into it. Is there any other way of installing Ubuntu just in case Unetbootin doesn't work?

---

### Post by razy60 on 2010-05-01
I used unetbootin to install 64 bit and 32 bit Ubuntu 10.04 on 3 different systems, I have found in the past that it seems to work better in windows for some reason, 
It works fine in 64 bit systems.
Which burning program did you use, Imgburn is the best it also works under wine if you don't have a windows pc.

Raz

---

### Post by A S C on 2010-05-01
Well my brother's pc has Mandriva installed on it, and I used k3b to burn. Thanks for letting me know 64bit works on unetbootin, I guess I probably did something wrong the last time I tried a 64-bit distro.

---

### Post by razy60 on 2010-05-01
If you can install wine on your brothers system then use Imgburn i never had much luck with K3b it just never seemed to do what i wanted.

Raz

---

### Post by A S C on 2010-05-01
Thanks for the advice. I'll give unetbootin a try first and see how that works.

---

### Post by razy60 on 2010-05-01
Good luck.

Raz

---

