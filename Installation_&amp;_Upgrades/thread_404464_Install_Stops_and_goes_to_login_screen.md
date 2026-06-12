---
title: "Install Stops and goes to login screen"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by xJudahx on 2007-04-08
Well the situation is that I was having problems with Ubuntu after running it for a year or so. So, I decided to reinstall.

I have two harddrives, the main one which has Windows XP on it, and a second one which I had ubuntu on. I removed the partitions on the second drive and created a new partition. 

When I go to install 6.1 off the cd, once I select English as the language and click on the next button, it flashes the time zone select screen, then goes to the login screen, logs in user ubuntu after 30 seconds, and goes back to the desktop. It does this each time I try to install.

I assume this has something to do with the boot partition being on my other harddrive. For instance, the boot loader still comes up at boot-up. Of course, Ubuntu cannot boot-up. 

Could someone throw some advice my way? Thanks!

-J

---

### Post by ffxr on 2007-04-08
yeah i think with the live cd the bootloader has to be written to the first hard drive..
this limitation doesnt exist on the alternate cd, try that.

---

### Post by xJudahx on 2007-04-14
I fixed the MBR using MbrFix.exe. I still get a hang-up after I select english.

If flashes the location selection window, then goes back to the login screen, over and over when installing 6.10. I tried to install 6.07 and it tells me I have a logical failure, I think the disc may be bad.

Any help would be appreciated, I'm being forced to use windows at the moment and it's painful.

---

### Post by zvacet on 2007-04-14
Just an opinion.Try to unplugg win HD and install Ubuntu on second.When you are finish plugg win HD again.

---

### Post by xJudahx on 2007-04-15
I tried it with the alternate cd and it hung on the select and install software section.

That is with the windows drive unplugged.

Guess I'll try 7.04 and see what happens

---

### Post by xJudahx on 2007-04-19
I tried to install 7.04, and I got this message while partitioning:

The ext3 file system creation in partition #1 of IDE2 master (hdc) failed.


Think the hard drive is bad?

---

