---
title: "External HDD install"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by newjersian1 on 2013-02-15
I have a dual booted HP Envy 17 (Ubuntu 12.04 and Windows 8). I wanted to install BackTrack :biggrin: as well but I have had major (read "resulted in total disk wipe") problems when I mess around with my partitions. I didn't want to install BT from a flash drive because I want plenty of room for fun stuff like word lists and rainbow tables. I wanted to put BT on my 1 TB external HDD. 

My steps:

1.) Downloaded BT and make a bootable live cd. 

2.) Removed my internal drive to avoid corrupting my MBR. (did that once, wont do it again:( )

3.) Booted from Live CD (without my internal drive) and made these partitions on the external HDD. (I dont know where the 5.56 MB space came from and if anyone has an idea that would be much appreciated.)
     
     [ATTACH]231437[/ATTACH]

4.) I then installed BT from the Live CD to the 211 GB partition. 


Now when I boot with the external drive I can choose if I want to run BT. Without the drive I can choose Ubuntu or Windows 8. This is exactly what I wanted. 

My questions:


1.) Did I do this in a smart way and if not what did I do wrong?

2.) Is there anything I should do to make the system more stable?

3.) Did I have to remove the internal HDD to avoid changing my MBR to the external drive? (I think I did that once though I'm not positive. I could only boot when I have the external drive connected otherwise I got a "Grub rescue" screen.)

Thanks for reading and for any assistance.

---

