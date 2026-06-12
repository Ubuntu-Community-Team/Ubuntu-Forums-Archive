---
title: "Installation issues with ubuntu ...."
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by levent20 on 2008-03-04
managed to install Ubuntu yeah!!!

formatted the drive ext3 and the installation went smoothly.

managed to fix grub error 
however from the menu, when i go to start ubuntu it gives me error 21:unable to find drive??????

Thanks
Levent20

---

### Post by dgray_from_dc on 2008-03-06
What grub error did you fix?  Could that have caused your current problem?

Have you tried recovery mode?

---

### Post by levent20 on 2008-03-06
Halo again,

i imagine that during the process a lot of awful things happen.... like i made a mistake with the terminal and there goes my system. but i had my information saved so it's ok.

back from the beginning though...

what i did id i learned about the terminal. so i wrote...

sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd0) here i made a fullish mistake to write once setup (0,1) where my windows were ..... no comments


can you please help on how i should install and do things from now... though also of installing and finally trying our ubuntu on the main drive and placing windows on the external.

Learning from the many mistakes...
Thank you in advance...
Levent20

---

### Post by Pumalite on 2008-03-06
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by levent20 on 2008-03-08
Thank you very much for your comments.

All done. Have windows in my hard disk and ubuntu in my external hard drive installed successfully. in the next few days i will try out the new system to see what i can do with it. 

Found a very good post and all i did was in the advance menu to install the bootloader in hd1 and place grub in root (0,0).

Can you please revert me also to a few sites on where and how to install beryl?

Thank you,
Levent20

---

### Post by thisiam on 2008-03-08
i have 7.10 and beryl came with it so you might already have it. right click your desktop->visual effects
if not [http://www.beryl-project.org/](http://www.beryl-project.org/)

---

### Post by Pumalite on 2008-03-08
7.10 comes with compiz-fusion, the wave of the future.

---

### Post by jken146 on 2008-03-08
To get the interesting compiz-fusion plugins, install the package **compizconfig-settings-manager**.  Then press Alt+F2, type **ccsm** and press Enter.  Play with the options.

---

### Post by levent20 on 2008-03-08
Thank you again,

Don't have the visual effects menu so i will try downloading it...

But i installed the updates and i have a question.... The installation was a success but i'm doing it from the grub in the beginning. meaning all the time i press e, e change root (0,0) ,b and the system boots. now i would like to make a change in the menu.lst but it says i have no permissions. when i go to the terminal and press "su" i put in my password but still no permissions.... 

any ideas???

Thank you
Levent20

---

### Post by jken146 on 2008-03-08
To edit menu.lst:
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by levent20 on 2008-03-10
Thank you,

Directions for the terminal and installing Comprizconfig-settings-manager worked.  

the system  seems to crash when another external hard drive is plugged in ....maxtor 300gb to be exact.... 

Maybe also not crashing down but stops working... all of a sudden the software starts loading and nothing actually loads!?

Thanks,
Levent20

---

### Post by Pumalite on 2008-03-10
Check your cables. If IDE, Master, slave, etc. Jumpers too.

---

### Post by levent20 on 2008-03-10
Sorry forgot to mention my computer details...

Dell inspiron 6000 laptop
2gb ram
120 external ext3
300 external ntfs
ati x300

a friend of mine said that i should place on the main 60 gb hard drive with win xp... what do you think?
checked with the partition editor and the 300gb external shows to be /boot and a triangle next to it. should i try to save the information and reformat it? 

They system becomes inaccessible and i have to restart when it is idle for some time say 15 min. doing nothing.... 

thanks,
Levent20

---

### Post by levent20 on 2008-03-12
It also tells me input/output error?
What should i do?



Thanks 
Levent20

---

