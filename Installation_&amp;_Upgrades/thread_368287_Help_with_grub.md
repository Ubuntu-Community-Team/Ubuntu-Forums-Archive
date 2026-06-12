---
title: "Help with grub"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by hansoffate on 2007-02-23
I just installed kubuntu.  Now when i boot to grub it isn't configured it just says

grub> _  

With the _ blinking.  What should i do?  I know my / partition is /dev/sda3

Thanks for the help
-Hans

---

### Post by Herman on 2007-02-23
Hello Hans,
It looks like you probably have a [Grub Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

If you know you have Kubuntu on sda3 you should be able to boot Kubuntu from the grub command line with these commands,
```
root   (hd0,2)
``````
kernel   /vmlinuz root=/dev/sda3
``````
initrd    /initrd.img
``````
boot
``` Those commands should boot it. Then you will probably want to find out why you didn't get your grub menu. You would want to check and see if you have a problem of some kind in your menu.lst file.

Do you have only the one hard disk? 

Regards, Herman :)

---

### Post by hansoffate on 2007-02-23
when i typed 
kernel   /vmlinuz root=/dev/sda3

It gave me  an error.  It said it wasn't there.  Should i just try to reinstall ubuntu all together?

Thanks for the help
-Hans

---

### Post by bulldog on 2007-02-23
You can just reinstall GRUB that's enough.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

This should do the trick for you.

---

### Post by hansoffate on 2007-02-23
Ok.  I will post back later today when I am home and have my macbook to do this on.  Does it matter that I think i am using GPT?  Do i need to mount any of the partitions?

/dev/sda1  refit  (osx boot menu [http://refit.sourceforge.net/](http://refit.sourceforge.net/))
/dev/sda2   osx
/dev/sda3   main linux partition (the default filesystem ubuntu uses)
/dev/sda4   swap

I hope this works and thanks for the help
-Hans

---

