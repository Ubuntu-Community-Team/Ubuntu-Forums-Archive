---
title: "Oneric 11.10 beta2 hangs updating 11.04"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by Goover on 2011-10-07
Hi, last night I tried to install/update, via the US-English Oneiric Ocelot 64bit Desktop Beta2 Live CD (md5 was verified correctly), the 11.04 64bit version with the very latest updates.
 
After a while the installation hangs with the screen "Removing conflicting operating system files".
 
The screen information is sparse, to say the least, the update bar(?) does not move, and only a rotating mouse pointer is visible. After a while moving over the interface I find the "Skip" to the right above the progress bar, and also up/down arrows at the right end of that bar. Using Up/Down I can see some lines of info, but nothing suggesting what to do or indication of this hung situation.
 
This is clearly a situation where the fancy interface has taken precedence over any useful information...
 
The hardware: Clevo laptop P170HM, 8GB RAM, BlueRay, 2 OCZ Vertex2 drives (different sizes though) using IDE interface.
 
/dev/sda is boot with W7U
/dev/sdb1 is W7U/NTFS D: data partition
/dev/sdb2 is/was Ubuntu 11.04 64bit English Desktop version with English language settings but Swedish keyboard et. c. using GNOME as default. 
The /sdb also contains a 16GiB linux-swap partition.
 
So, is there anything I can do to resolve move back to 11.04?
And, how can this be reported as a bug?
 
Regards,
 
(G(r)oover

---

### Post by Goover on 2011-10-07
Oh, I forgot:
 
Processor: i7-2630QM
 
Graphics: nVidia GeForce GTX485M
 
AND,
 
no it doesn't really 'hang', it just dont continue at removing conflicting oprating system files. The menues for connections et c at the top right work, like network connections including Wi-Fi.
 
But I simply just don't know what will be the best to do in this situation?
 
G(r)oover

---

### Post by dino99 on 2011-10-07
purge the ppa(s) first if you use some of them

---

### Post by Goover on 2011-10-07
Hi, and thanks for that suggestion, but now it is too late to try to salvage something. (On that computer I do not do any programming or real neccesary things - although I will use it in the future when I'm on the road.) So, this really was a test of the Ubuntu environment and stability and ease of use. I have 11.04 on another computer, and will not update that one until further tests.
 
Since there was no real easy or even moderately easy way to get the old system back, thrashed GRUB et c, I used Gparted Live to take away the "battered to death" partitions and attempted a fresh install of Beta2.
 
The installation of Beta2 is still on its way, right now updating from the 'net, I will just installe it and install a few software things I need tested for my further cross platform development. After the release of 11.10 I will install that one fresh too and test.
 
However, what can really be seen already is that there is too much fancy stuff around the installation and absolutely not enough info on the choices one have, nor any explanations. It did not offer any choice of fs, like I want ext4. nor any choice of swap size - something that is otherwise pointed out everywhere as. The "fancy interface" also does not provide a real easy visual coloring scheme - What is available and what is later enabled in the form of buttons is less that obvious.
 
So, Why has design taken over Ubuntu instead of an easy and reliable OS?
 
Well, I am still wondering...
 
Regards,
 
G(r)oover

---

