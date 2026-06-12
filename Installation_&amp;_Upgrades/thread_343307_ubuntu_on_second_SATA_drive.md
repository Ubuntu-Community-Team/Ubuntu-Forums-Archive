---
title: "ubuntu on second SATA drive"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by yiannis_t on 2007-01-21
Hello to everybody!!

I have recently bought an 80gb SAtA II hard disc drive(still unplugged)..

I am planning on installing ubuntu on that drive as on my 250gb SATA II drive i have winxp:biggrin: ..
Should i unplugg that drive before installing ubuntu??I am asking just because i have read it somewhere and i am not sure what's the purpose of that..

ANd something else ..After installation i am planning to change my bios settings so as to boot from the new hard drive(80gb) .what should i add to my bootloader file in order to add "Windows XP" on the bootloader menu...??



Thank you in advance !
Have a nice day! :)

---

### Post by bulldog on 2007-01-21
You can disconnect your windows hdd,but it's not necessary.
You only have to know which drive is seen by ubuntu as the master boot device,because it will install GRUB there by default.
```
cat /boot/grub/device.map
```
If your new 80GB ubuntu drive is listed first you're clear to go.

To make your windows entry work in this new config. you have to add two lines in menu.lst,and make your windows entry look like this,just change the partitions to the one you use.
```
### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1
```

Have a nice day too

---

### Post by yiannis_t on 2007-01-21
Where should i write the cat command?? Let's say that i have just plugged my sata drive and run a live cd..I should open a terminal session and write it there?

Also a clarification about the remap commands in the bootloader.. As i have said i have a 250gb SaTA II drive and i ve recently plugged the 80gb SATAII..SO the commands sould be exactly the ones you ve written as an example,shouldn't it?? (hd0,0) and (hd1,0)?

---

### Post by bulldog on 2007-01-21
> **yiannis_t said:**
> Where should i write the cat command?? Let's say that i have just plugged my sata drive and run a live cd..I should open a terminal session and write it there?

Also a clarification about the remap commands in the bootloader.. As i have said i have a 250gb SaTA II drive and i ve recently plugged the 80gb SATAII..SO the commands sould be exactly the ones you ve written as an example,shouldn't it?? (hd0,0) and (hd1,0)?

You have to put the cat command in a terminal and take a look at the output.[ALT+F2 and type gnome-terminal]
Yes,the command should be the same,and if windows is on the first partition you can use the rootnoverify (hd0,0) to,only change the /dev/hda1 into sda1

To enter the menu.lst after the install,boot into ubuntu,open a terminal and```
gksudo gedit /boot/grub/menu.lst
```
Make the modifications and save the file.

---

### Post by nfear24 on 2007-01-21
Im also trying to install ubuntu edgy 6.10 on a sata drive.  I have windows xp installed on the other sata drive.  Problem is I get a grub error everytime during the install.  It keeps trying to write it to hd0 and I change it but still cant get it to work right.   None of the commands listed above work when booted to the live cd because grub directory doesnt exist in the /boot.

Thanks Nick

---

### Post by bulldog on 2007-01-21
**@Nick**

I presume hd0 is your windows disk?
Change the boot order in your BIOS so the ubuntu disk is the master boot device.
Grub will now install in the MBR of this hdd,and you can use it to boot ubuntu and windows as well.
To boot windows,which is now on the second hdd,you have to modify your menu.lst after you installed ubuntu.
Make your windows entry like this,presuming windows is on the first partition.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

---

### Post by nfear24 on 2007-01-21
I have a stupid highpoint onboard controller on my Abit IT7 Max2 board.  when my computer boots I hit 'Ctrl h' to enter the raid config.  I dont have raid setup,  dont want it.   I set the sata drive to boot.   Still has been a no go.  I am able to install fine to to ata drives, but not sata ones on this stupid hpt374 controller.   I like ubuntu because I have everything running on it like my mailserver and webserver and also my laptop.  I just cant get it installed on my sata setup.

> I continue to get Executing 'grub-install (hd0)' failed.   I have tried others like hd1, hd2, sda0, sda1, sda2, sdb0, sdb1, ect......

Thanks Nick

---

### Post by dabl on 2007-01-21
The Edgy ISO CD is _very_ picky about where it will and won't put Grub -- you can't just change "sd0" to "sd1" or something like that -- it will abort.  I spent a week trying every combination of that routine with my two hard drives (1 IDE (with Win XP on it) and 1 SATA), and ultimately gave it up and let Grub go on the IDE with Win XP. All the rest of Linux went happily on the SATA drive, in three partitions.  I've read subsequently that if you use the "Alternate Installation" CD, you will have more choices about where Grub goes. Next time (Feisty) I'll do it that way ...

---

### Post by nfear24 on 2007-01-21
> **dabl said:**
> The Edgy ISO CD is _very_ picky about where it will and won't put Grub -- you can't just change "sd0" to "sd1" or something like that -- it will abort.  I spent a week trying every combination of that routine with my two hard drives (1 IDE (with Win XP on it) and 1 SATA), and ultimately gave it up and let Grub go on the IDE with Win XP. All the rest of Linux went happily on the SATA drive, in three partitions.  I've read subsequently that if you use the "Alternate Installation" CD, you will have more choices about where Grub goes. Next time (Feisty) I'll do it that way ...

Ok,  Just another question here.  If I choose to manually edit my partions and I create a '/' and a swap partition.  When I get to the Prepare Mount points screen.   Select which partions you want to use I choose '/' in the mount point but when I click on the Partition drop down box.   There is no options.  why is that?  Its just blank in the drop down box .
[IMG]http://www.tickus.com/images/partition.jpg[/IMG]

Thanks Nick

---

### Post by nfear24 on 2007-01-22
I also notice my drives arent mounted in Computer area.  If I load the installer for ubuntu feisty I can see the hard drives in there.  But I cant install feisty because the screen goes weird on me after I select the keyboard settings.

---

### Post by bulldog on 2007-01-22
> **nfear24 said:**
> I also notice my drives arent mounted in Computer area.  If I load the installer for ubuntu feisty I can see the hard drives in there.  But I cant install feisty because the screen goes weird on me after I select the keyboard settings.

Maybe you should consider Dapper or even Edgy.
I don't think it's a wise choice to go for Feisty,if you haven't that much experience.

---

### Post by dabl on 2007-01-22
Here is a pretty nice tutorial on how to partition and then how to create mount points:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


But it will not cover every step of the Ubuntu installation routine for every version, especially not the new one for Feisty.  You may need to become an fstab and grub/menu.lst editor to get things the exactly way you want.

---

### Post by nfear24 on 2007-01-22
> **bulldog said:**
> Maybe you should consider Dapper or even Edgy.
I don't think it's a wise choice to go for Feisty,if you haven't that much experience.

Actually Im pretty experienced.   Im using Edgy fine on my DL360 and DL380, running my webserver and mail server.   This is just the first time I have not been able to install something.  I am trying to install Edgy.  I was just saying that Feisty actually allows me more control over the partitioning and if it didnt crash the screen it would work fine with my sata hpt374 controller.  That mounts and partitions fine.  I think its something to do with Edgy and the hpt374 onboard controllers.

---

