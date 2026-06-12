---
title: "Ubuntu installation gone bad"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by BigSteve on 2007-07-11
ohoh,

Last week I tried to install ubuntu on my Windows XP computer. (HP Pavilion 7855). FIrst few attempts did not work. After reading posts and answers here, I purchased Partition Magic and made room for Ubuntu. Installation succeeded. COuld boot Ububntu doing nothing, or select XP from menu.

installed upgrades as suggested; installed a few apps like Monkey Bubble etc. , set up email and FTP. all worked.

Was installing supprot for my printer (HP Photosmart 7150) when things went south. System locked up. Had to shut down using power button. 

Now if I turn the computer on with no CD in drive, I get "No Operating System Found" message. If I start it with either a windows or a ubuntu CD in, I jsut get a blinking cursor, with no apparent response to keyboard or time.

DID I fry something? At a loss as to what todo next. Any ideas? 

Is my computer DEAD? 

Steve

---

### Post by confused57 on 2007-07-11
You could try reinstalling grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If this doesn't work, you might do a filesystem check:
[http://users.bigpond.net.au/hermanzone/p10.htm#Forcing_a_filesystem_check](http://users.bigpond.net.au/hermanzone/p10.htm#Forcing_a_filesystem_check)
the gparted live cd is probably the easiest method to do this.

---

### Post by Gremlinzzz on 2007-07-11
I f your not trying to save anything i would wipe the drives clean do the bois default thing and make sure the cd boots first. this is the free program i use to clean my drives.
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by Gremlinzzz on 2007-07-11
The easy way to dual boot ubuntu 
create two partitions one for windows other for linux.delete the linux partition which makes it free space. install windows first  then  ubuntu live cd  click install icon when you  get to the partition questions choose use largest continous free space.ubuntu does the rest.

---

