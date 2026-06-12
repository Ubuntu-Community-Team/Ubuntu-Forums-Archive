---
title: "installing software"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by vandenm on 2007-08-09
Hi

I am trying to install Mentor Graphics Calibre software. I have manged to do it when ubuntu is installed under vmware no problem but not when it is stand alone on a pc

If I type ./ixl_cal2007.2_34.24_mib.exe it says 'command not found', however this does work in the vmware setup I have on my laptop.

Mentor do not support ubunto so no help there, they only support redhat and susie

I have tried changing permissions etc and log in as root but no still no joy

Any help would be much appreciated.

Cheers

Mike V.

---

### Post by cosborn72 on 2007-08-09
Mike, 

You cannot generally install windows software in linux.  The OS uses its own set of software, separate from that developed for windows.

If you need the software, you have a couple of options.

-run it in vmware, as you have already done.

-contact the software developer and see if they have a linux version

-try to get it up and running using WINE (you can go to [http://appdb.winehq.org/]("http://appdb.winehq.org/") to find out if anyone else has been successful running the software.)

Lastly, you can try to find a open-source variant that has the same functionality as the windows program.


I hope this is helpful.

---

### Post by vandenm on 2007-08-09
thanks for the reply

I have spoken to the vendor and it is a linux file and ./ixl_cal2007.2_34.24_mib.exe should work but for some reason it does not in ubuntu.

I have also now managed to get it to work in mandriva

---

### Post by vandenm on 2007-08-11
Just thought I would post the solution to my problem.....

It turns out that the install program is 32bit and I was running 64bit ubuntu on 64bit hardware. To overcome the the problem I had to install the 32bit libraries for the install program to work.

sudo apt-get install ia32-libs

I would have thought a 32bit program would work on 64bit but obviously not the other way round.

---

