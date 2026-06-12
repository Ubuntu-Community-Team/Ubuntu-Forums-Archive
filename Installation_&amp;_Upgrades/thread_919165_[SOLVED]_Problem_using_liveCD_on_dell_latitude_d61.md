---
title: "[SOLVED] Problem using liveCD on dell latitude d610: won't partition correctly"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by tuffguy45 on 2008-09-13
I have a Dell Latitude d610 that I'm trying to dual boot windows XP and ubuntu on however, when I try to partition 10gb off to use for ubuntu it gives me an error and won't let me install.

I am correct in my procedure for dual booting right? You just move the slider to the size of the ubuntu partition and then after it installs it will notice that you have windows on there and set up grub without an editing of the menu file?

I already installed windows xp and ubuntu on two different hard drives earlier today on a separate desktop computer so I have a little experience but, try to be as simple as possible as I'm not quite familiar with unix terminal commands but, I am a pretty savvy windows user.

---

### Post by Partyboi2 on 2008-09-13
What is the error message?
Have you tried to manually partition? You can do this by selecting "manual" and making a / (root) partition with the mount point set to / and a swap partition roughly double the amount of your onboard ram but probably wouldn't go more then 2gig.
So for a 10 gig and if you had 1 gig ram you would use
8 gig /
2 gig swap

---

### Post by tuffguy45 on 2008-09-13
Yeah it still does that if I try to do manual, I knew I should have wrote it down but, it might take me a bit as I'm having domestic problems right now... It was something really simple like "Error encountered with partition process aborted" and it gives you two options but, I forgot what those were.

I think I'll download a newer LiveCD since the one I installed on the other computer was 7.10 and I'm trying to use that LiveCD again. It took almost two hours to update but that was a 433mhz computer with only 256mb of ram.

---

### Post by tuffguy45 on 2008-09-13
[[IMG]http://img93.imageshack.us/img93/9539/0913081921oe6.jpg[/IMG]](http://imageshack.us)
By [tuffguy45](http://profile.imageshack.us/user/tuffguy45)

Thats the error I get whether I do manual or guided

Sorry, about the quality that's the best thing I could think of doing besides writing it down and with my bad handwriting an laziness I'd probably screw it up I'd also like to say the my regular forum (GameFAQs) uses VERY basic html so I'm not really into the more advanced stuff so if I look stupid for posting huge pictures or not being able to use the code function thats why...

---

### Post by tommcd on 2008-09-13
Try using parted magic live CD to partition the hard drive. Boot off the parted magic CD and partition the hard drive as needed.
[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)
Or use the gparted live CD:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Just free up some space with parted magic or gparted and install Ubuntu to the new free space. Or create linux partitions (one for /root, swap, and /home) and then install Ubuntu. Just format partitions with ext3 file system and install Ubuntu.

---

### Post by tuffguy45 on 2008-09-13
So how will it show up when I try to install Ubuntu? Like as a seperate hard drive or what? I'm warry to use those utilities because I completely trashed my system with Partition Magic once.

---

### Post by tommcd on 2008-09-13
Just free up some space with parted magic or gparted and install Ubuntu to the new free space. Or create linux partitions (one for /root, swap, and /home) and then install Ubuntu. Just format partitions with ext3 file system and install Ubuntu. (I edited my previous post to include that, but you replied before I finished). 

Probably the easiest thing would be to shrink your windows XP partition to create enough free space for Ubuntu, and then install Ubuntu to that. Defrag the Windows XP partition first.

---

### Post by tuffguy45 on 2008-09-13
I understand what you meannbut after I set up my partitions, how do they show up when I boot from the Ubuntu liveCD? Like when the partition screen comes up do I say manual and then click on the partitons I made?

---

### Post by tommcd on 2008-09-13
Since you are only planning to allocate 10 GB for Ubuntu the easiest thing would be to just free up 10GB free space with gparted or parted magic. Then boot up the Ubuntu live CD. The 10GB free space will show up as "unallocated space" or something like that. Create 2 logical partitions. The 1st will be a 1GB swap partition. (If you have  1GB or more of RAM then you can probably get by with 500MB swap). The 2nd logical partition will use the remaining space for /root. Setup these partitions then continue with the installation.

---

### Post by tuffguy45 on 2008-09-13
Someone answered my question in the other topic, all I had to do was defrag the C in windows.

---

