---
title: "New Install of Ubunto Server 9.10 i386"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by PrairieShadow on 2010-04-08
I have burn 2 discs and both test discs freezes at 36% - checking file libruby1.8_1.8.7.174-1_i386.deb
 
If I try nad just do teh install it freezes at 33% in formatting the ext4 partition.
 
Do I need to try and download another installation or try burning the CD again?
 
Time for some :popcorn:, im hungry.

---

### Post by Mighty_Joe on 2010-04-09
The most common problem I've seen with server installs is that people download the 64-bit version (the default) and try to install it on 32-bit hardware.  
What hardware do you have?

---

### Post by moetunes on 2010-04-09
Did you do the "check cd " from the boot menu? If so is your h/ware standard type or is there something exotic in your box?

---

### Post by PrairieShadow on 2010-04-13
I did do teh check CD and it freezes round teh 33-36% mark checking file - libruby1.8_1.8.7.174-1_i386.deb
 
the first CD i burnt was the 64 bit version and the check disc did not work at all.
 
I do not believe that there is anything special on this computer. It is a PIII 1Gtz machine with 768 mb ram.
 
I have downloaded the ubuntu-9.10-server-amd64.iso (did not work - 64 bit) and ubuntu-9.10-server-i386.iso freezes on the check disc and install (durring partition)
 
Do I need to go to an older version?
 
I am :confused:
 
thanks for the helps

---

### Post by Mighty_Joe on 2010-04-14
> **PrairieShadow said:**
> I did do teh check CD and it freezes round teh 33-36% mark checking file - libruby1.8_1.8.7.174-1_i386.deb


That makes it sound like your CD's bad.  Can you try it on another computer?  Have a friend burn you one?  Make a bootable USB drive with [unetbootin?]("http://unetbootin.sourceforge.net/")

> **PrairieShadow said:**
> 
I do not believe that there is anything special on this computer. It is a PIII 1Gtz machine with 768 mb ram.

 
I'm running Ubuntu Server 8.04 on a Via C3 with 512mb RAM, so it will work on pretty weak hardware.

> **PrairieShadow said:**
> 
Do I need to go to an older version?


The 8.04 version is the current Long Term Support release and will be supported through April 2013, so it would be a good choice to try.  Right now, I don't think the version is your problem though.

---

