---
title: "Dual booting Xp/Ubuntu (2HDDs)"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Racerx15923 on 2007-05-01
Hello all!
I am new to Ubuntu and linux in general.  I have downloaded and been using the Live CD for a few days now and I've fallen in love with it.  But i have a need for windows that over-shadows my love for Ubuntu.

Luckily after lurking around on these forums I came across a lot of dual-booting threads.  To my surprise a lot of people are in the same shoes as me. So ill lay out my hardware:

I have two HDD's and both are IDE
The first with windows XP (sp2) is a 160gb (130gb filled)

And my second HDD
40gb (empty)

Now i plan on keeping my Windows hard drive untouched and making it the slave, While my new Ubuntu 40gb is the master.  The threads I've found all had great info, about partitioning (I had though of a partition style but nothing that would specifically help me, the hard drive is too full) Another thread on two hard drives, One IDE and one Sata (Sadly i don't own a compatible motherboard or HDD).

Is there anyone that can point me in the right direction?

---

### Post by bulldog on 2007-05-01
Well,what is the question?

Making your windows slave and ubuntu master before you begin to install is perfect.

Maybe you should download the gparted live cd ,to make it a lot easier to partition your 40GB hdd.
It has a graphical interface,so it shouldn't be too hard.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Burn this to a cd and boot from it.

Some advice,but you're totally free to do it your own way.
Create a 10GB partition for /  [root] file system ext3
Create a 1GB  partition for swap file system swap [similar as the windows page file]
Create a 10GB partition for /home file system ext3
Create a 19GB partition for /data file system ext3

The /home is where your personal settings and data will be stored,most handy in case of a reinstall,and the /data partition you can use
to store data which you want to keep.
Of course you can choose to make no /data and increase your /home that's up to you,it's just a proposal to lead you in the right direction.
You must have a / partition and a swap the rest is at your choice.

When your satisfied with your partition setup,hit apply and it will be created.
When done,exit the gparted cd and pop in the ubuntu install disk.
Boot to the desktop,and hit the install button.
Answer the simple questions,till you come to the partition section.
Choose manual partition and 'mount' your partitions at the proper place.
That is 10GB /
1GB swap
10GB /home
19GB /data

Proceed with the install and install GRUB to (hd0) in the end.
You will be asked if windows must be on the menu.lst,answer yes,and when done,reboot as asked.

Now you can boot ubuntu,but......not windows,I'm afraid.
No panic,we gonna solve that.
Boot to the ubuntu desktop and hit ALT-F2
This will open a box,type in this box gnome-terminal.
Now you have a nice and shiny terminal,which is in your menu too.
Type in the terminal```
gksudo gedit /boot/grub/menu.lst
```
This will open your menu.lst in a text editor.
Scroll to the bottom and there should be your windows entry listed.
You have to enter some things,**don't change your boot options**
just edit it till it looks like this one.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	+1

```add the mapping entries,don't change your boot options,save the file and type in your terminal```
sudo update-grub
```
Now you can reboot if you want and you should be able to boot windows and ubuntu as well.

---

### Post by Racerx15923 on 2007-05-01
Hmm.

I am at a complete loss at how to do it.
I've never undertaken something like this and so far i have two hard drives with an OS on each.
The way I'm doing it now is unplugging one an putting in another, I don't know how to get them set up so i can select which i want to boot with (Without manually unplugging or entering the BIOS every time).

---

### Post by bulldog on 2007-05-01
Look at my edit,it should be clear,I think:)

---

### Post by cosborn72 on 2007-05-01
Racerx, this is kinda scary stuff if you have never done it before.  I certainly understand if it is confusing.  (Although it is correct.)  At what point are you running into problems?

---

### Post by 13thMonkey on 2007-05-01
You're saying you've got a hard drive with Windows on and another unformatted/empty hard drive? Both IDE?

Just tell the Ubuntu installer to load itself onto the non-windows hard drive. No need to worry about masters and slaves - the installer will load up GRUB (the boot manager) and work it all out for you so you can choose which OS to use when you boot :)

---

### Post by Racerx15923 on 2007-05-01
Well after reading bulldogs post i decided to do a fresh install of Ubuntu. (Which i am on now)

When i boot, i don't see grub, although my windows os hard drive is unplugged. Should i be seeing it or should i plug in my other hard drive and then it will pop up.

---

### Post by Racerx15923 on 2007-05-01
Haha! it works great.
Thanks everyone for the info, especially bulldog.

---

