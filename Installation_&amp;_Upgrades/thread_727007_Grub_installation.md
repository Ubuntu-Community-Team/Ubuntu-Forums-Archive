---
title: "Grub installation"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by wawey on 2008-03-17
hii ,, i've got a dell xps m1330 with vista.

i've got 3 partionins as follow 
sda1 (1° partition of primary) (grub hd0,0)
sda2 (2° partition of primary) (grub hd0,1)
sda3 (3° partition of primary) (grub hd0,2)

I made a partition in vista with 6 giga then i boot with the live cd and g parted that partition to 

Extended      sda4 (grub hd0,3)
ext3  (logic)   sda5 (grub hd0,4)
swap (logic)   sda6 (grub hd0,5)

and continou installation ,, i choose the manual and continue,,, i change the boat loader from (hd0) to (hd0,4) ,, the installing went fine but when i restart ,, it goes to vista directly and the grub did,t appear ,, i checked the menu.list forthe grub and every thing was intalled correctly ,, any ideas how to solve the confusing matter.

---

### Post by markjensen on 2008-03-17
GRUB didn't appear because you told it not to.

The bootable code is written to sda, not to any partition in it.  So when you put it into the fifth partition (0,4), you put this GRUB that needed to execute and handle your dual booting into an area that Vista's boot loader never points to.

Why are you doing all this partitioning by hand?  Is there something specific in your configuration you are after?    Because it seems to me that you are making extra work for yourself in an area that you are not quite familar enough to get a bootable system.

---

### Post by wawey on 2008-03-17
actually i did it normally wit the guided free intallation ,, but fatal error when installing Grub came !! thats why i did it this way

---

### Post by wawey on 2008-03-17
what shall i do to make it installed properly ?

---

### Post by sandysandy on 2008-03-17
have a look at these links

[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

[http://ubuntuforums.org/showthread.php?p=2219437](http://ubuntuforums.org/showthread.php?p=2219437)

regards

---

### Post by wawey on 2008-03-17
i will check them and tell u the resut ,,

thanks

---

### Post by wawey on 2008-03-18
I did install ubuntu with several attempts but after using it , the wireless hangs and i restarted the pc and ten when the starting screen (ubuntu) it hangs again ,, i tried to CTRL C but nothing happened.. is there a way to reinstall it without loosing vista and grub !!

---

