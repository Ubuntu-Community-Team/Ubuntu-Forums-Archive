---
title: "Grub will not start, comp just restarts."
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by format C: /q on 2009-12-02
Hello.
I must start whit saying that i have now used ubuntu for like 2 month and must say that i am impressed ! Great work to all of you programmers out there making this OS as good as it is.
 
But the sad thing is, the reason im posting in this forum is becouse my little netbook is feeling bad. I am using a dualboot setup whit Ubuntu 9.10 and Windows Xp Home.
 
It all started out when i got the birght ide to use a partion program in windows. I was in the making of a USB startup stick. When i thought i was in the USB stick and pressed make MBR.... 
Did not think more of it untill the next day when i bootet up .. nothing worked. Well i got the Ubuntu 9.04 Live cd on a memorycard so i just plugged that in. Booted up and found everything on the comp. Made some backups of the data i wanted and decided to reinstall Ubuntu.
 
Ubuntu 9.04 up and running and everything was a blast ! Updated to 9.10 and still everything was a blast. Now i want to install Windows Xp. 
The thing is that i do not have Xp on a cd or stick, its on a partion on the HDD. But GRUB finds that partion and i chose it and installs Xp still everything is blast. After the install GRUB finds Ubuntu 9.10 (and recovery) , Memtest, Vista loader(Xp installer) and so Windows Xp. FINE ! Boot up Xp and updates all the stuff that MS thinks we all need to update .. i install Avast Antivirus as well.
And then i reboot...
 
Grub 1.5 flashed in the left corner and comp restarts.. try it all over again and still the same. I can not boot, my computer just restarts. 
 
Now comes the realy tricky part. It seems like i need to install Xp and then Ubuntu ? But i can not install Xp if i do not get Grub to function? (i need to get to my installer partition)
 
When i use the LiveCd i cant get a internet connection..to update Grub,  so im cinda stuck and could use a hand in this matter. So if anyone got some time over and feel like they can help please i need help here.

---

### Post by namok on 2009-12-02
I think you need to install grub2 in the MBR, but to be quite sure [follow this link]("http://ubuntuforums.org/showthread.php?t=1291280") and add RESULT.txt to the next post.

---

### Post by darkod on 2009-12-02
Yes, it's better to have first XP installed and then Ubuntu. Especially since you are installing XP from a recovery partition and you can't really know if that process will hurt the already installed Ubuntu and how much.
You say you have no way to use the recovery partition without already working computer. Usually there is a button you can press during boot that should allow you to use the partition. That's the point, for example if you completely mess up your system, there must be a way to recover it.
Look very carefully when booting up, and see if something like that comes up. Also if you have the manual of your computer check there too.
If you find a way to use the partition, the preferred option is to recover XP first, if it takes the whole hard disk use Gparted to shrink it (just that, do NOT install ubuntu immediately), boot XP few times to do it's disk checks and to settle down after the shrink.
Then just boot with ubuntu cd, select Install Ubuntu, and either tell it to use the free unpartitioned space, or create manually the partitions, which ever you prefer.

---

### Post by format C: /q on 2009-12-18
I did the thing i should have done from the start. 
I Now got a single system. Whit Ubuntu as my only OS !

Cheers and take care

---

