---
title: "Dual Booting MBR Problem"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by EmagdniM on 2007-04-21
I am very new to linux so please give me a break. My problem is I have five hard drives two are 36.5 gig sata raptors that are raided 0 together and they contain windows on it. Then i have two other storage drives a 200 gig and a 400 gig. My final drives is a 40 gig ide hard drive that I found laying around. I have currently installed Ubuntu on that 40 gig hard drive but when ever I start the computer up it just automatically goes to windows no Grub option menu. I have tried switching the order of the hard drives in the bios and that didn't help at all just gives me an error failed to load operating system. I feel it skips grub because on my raided hard drives I don't think Ubuntu has drive support for it and I feel like it is installing the MBR to one of the raptor hard drives and it makes it so the computer cant find the MBR for Ubuntu but I may be way off. So this is why I come to you. I would like to have it so windows is my default and when I start up it automatically goes there but I would like an option menu where I can select to go to Ubuntu. If this is possible it would be awesome. Thank you very much for your time and help.

---

### Post by Leadroflstsouls on 2007-04-21
This is strange I had this problem a while back but I had a friend fix it I would like to know how this turns out.

---

### Post by upchucky on 2007-04-21
I just finished fixing my grub problems using this very informative post.
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by bulldog on 2007-04-21
> **EmagdniM said:**
> I am very new to linux so please give me a break. My problem is I have five hard drives two are 36.5 gig sata raptors that are raided 0 together and they contain windows on it. Then i have two other storage drives a 200 gig and a 400 gig. My final drives is a 40 gig ide hard drive that I found laying around. I have currently installed Ubuntu on that 40 gig hard drive but when ever I start the computer up it just automatically goes to windows no Grub option menu. I have tried switching the order of the hard drives in the bios and that didn't help at all just gives me an error failed to load operating system. I feel it skips grub because on my raided hard drives I don't think Ubuntu has drive support for it and I feel like it is installing the MBR to one of the raptor hard drives and it makes it so the computer cant find the MBR for Ubuntu but I may be way off. So this is why I come to you. I would like to have it so windows is my default and when I start up it automatically goes there but I would like an option menu where I can select to go to Ubuntu. If this is possible it would be awesome. Thank you very much for your time and help.

You can install GRUB on the hdd which has ubuntu on it.
You only need to switch the boot order in your BIOS to this hdd to see the GRUB menu and to be able to boot ubuntu.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
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

Where the setup (hd0) command is,you have to replace it with the hdd you'll get with the 'find' command.

---

