---
title: "installing dual boot with two drives"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by 40VxbzW3pdg on 2011-09-29
Hi 
I am very new to Ubuntu, and I do not have any background in operating systems at all. I have installed other distro's but have never really understood how linux works, or what the basis is for using the terminal commands. I have to say though that I installed Ubuntu using wubi, and a flash drive. But, then ran into to problems with the install using disk memory to the point that my drive started running out of space. So, I uninstalled Ubuntu before disaster occurred. I have two drives that are both about 80gig a piece, and want to install Ubuntu on my drive that does not have windows XP professional service pack 3 on it. I found out last night that it isn't as easy as I thought it was, and I ended up not installing Ubuntu. First I was told that Ubuntu could not find root file system, and then after using the drop down menu's that are available to start the install I found out I did not use the right options so Ubuntu 11.04 did not install anything.
Could someone tell me from non-tech point of view the easiest way to install a dual boot in which you already have Windows installed, and want to use Grub to choose which op you would like to boot to. I have done research on the suggestion of making the Ubuntu drive master, and making the windows drive slave, but I do not think that is a good solution. I think I would like to have set up so that Ubuntu is a choice, but windows is still the first choice.
Thanks for any help!

---

### Post by oldfred on 2011-09-30
I like Herman's site, but for a new user it may seem like overkill as he explains everything and has links to even more info. But it explains the process with two drives which very few do.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

The important thing with two drives is to use manual install so you have an option on where to install grub2's boot loader to. Otherwise it defaults to sda which is usually your Windows drive. Then in BIOS change to boot sdb. If the install does not auto find your Windows then this should from a command line in Ubuntu:
```
sudo update-grub
```

If you have an older system with IDE/PATA drives, does your BIOS let you choose boot (usually not)? Older IDE drives only boot from primary master which is set with jumpers or location on cable if using cable select. With master/slave IDE drives you have to install grub to the master or sda drive. That will overwrite the Windows boot loader, but grub's menu will give you the option to boot XP.

You can reinstall the XP boot loader to the MBR of sda if needed as long as you have the XP install disk or a Ubuntu liveCD. You should have both.

---

