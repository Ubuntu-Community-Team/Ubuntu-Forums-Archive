---
title: "Xp 1 Ubuntu 2"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by Precapice on 2008-04-18
Hi Peoples

Jumping right in with a request for some help .....

I have xp on my first HD
I installed Ubuntu on my second HD.

I partitioned the second HD 3 times 1 = Ubuntu (/) ,2 = swap file, 3 = /home

Rebooted and I guess I expected magic to happen but alas it was not to be ...
Xp only boots up no choice for booting into second hard drive Ubuntu ....sigh

Changed the primary boot drive to Ubuntu in bios get a message no os detected ....ect

Help, lost, confused  .... miserable , hate xp set me free please !

---

### Post by Pumalite on 2008-04-18
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
You need to go 'Manual' and use the partitions already prepared. You have to let Grub install to MBR if you want dual boot.

---

### Post by ugm6hr on 2008-04-18
Installing to a 2nd HD is marginally more complex than dual-booting on one.

How exactly have you installed Ubuntu?

Best bet is to install Ubuntu on primary HD (1st boot, sda or hda).

---

### Post by Precapice on 2008-04-18
manual

2nd hard drive

10 gig partition root for Ubuntu
1gig partition for swap
70 gig partition for home as /

---

### Post by Pumalite on 2008-04-18
/home is /home.
Look out for this too:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

---

### Post by Precapice on 2008-04-18
> **Pumalite said:**
> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
You need to go 'Manual' and use the partitions already prepared. You have to let Grub install to MBR if you want dual boot.

Excuse my ignorance but your links deal with installing Ubuntu on a single hard drive correct ?
second , where is grub located ? A real noob question I am sure but .....

---

### Post by Pumalite on 2008-04-18
The staff member pointed correctly and in cases of 2 drives is better to install both OS's in the first drive (sda?) and keep the 2nd drive for storage or separate /home. Partly to avoid situations like the one I pointed out in my second post. Grub should be installed to MBR if you want dual boot.

---

### Post by metalf8801 on 2008-04-18
You can in stall XP on the first drive and Ubuntu on the second and then during start up you can press a button on your keyboard that lets you select which drive you want to boot from.  It should tell you which button to press on the first screen you see if you don't see it right away press Pause/Break and then look for it.

at least thats what I did for a while. 

now what you can also do is during install select manual then format your the drive you want Ubuntu then install it then make use that drive and only that drive is checked then click on install you don't need to do anything other then that

---

### Post by Precapice on 2008-04-18
Ok thanks for the advice I will go partition the first HD and install Ubuntu on that 1 .
Any last minute advice you can give me before I proceed ?

---

### Post by Pumalite on 2008-04-18
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by Precapice on 2008-04-18
Ok all done 

The solution was quite easy .... I just deleted windows and installed Ubuntu :)

Thank you to everyone for the prompt replay's

---

### Post by Pumalite on 2008-04-18
Well done!

---

### Post by Enlitend on 2008-04-18
LOL , that was easy . Congratulation, you finally free of Windoze.
I still kept it just for gaming need.
BTW, installing dual boot on separate drive wasn't that hard, you just have to play it around abit, there are tons of infos on this forum to guide you through. 
cheers :)

---

### Post by Precapice on 2008-04-19
Thanks guys.

I will have to do it later probably just waiting for my wife to throw her toys out the cot :)
but so far she seems happy.

Been setting it up and wow I had no idea how cool it could be . Love the expose thing , just like my mac but even better some how.

I love my mac but damn now I feel like I'm having an affair or something.

---

