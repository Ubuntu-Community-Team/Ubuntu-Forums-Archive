---
title: "Install help please,cant get anything to happen !"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by x5452 on 2007-04-25
I have an old sony vaio laptop model pcg-fx150k that I wanted to install Ubuntu on to learn and practice with linux. I have completley wiped the hard drive of this laptop.   I downloaded the 7.04 distro from this site and popped it in.  Upon boot up I get a welcome/ setup screen and choose install ubuntu, I click it and the screen goes black except for a cursor. ( I know I have read the other posts similar to this but CTRL+ALT+F6 does nothing) after the cd spins down the screen is filled with colors/static like really fine flanel.  Thats it nothing else happens.  
Same exact thing if I try to start in safe graphics mode from the first screen.
I also tried downloading the alternate version from this site, and when I boot up I get the welcome type screen and click text install, the screen goes blank as the cd spins up, then cd spins down and I get the message 
"Your CPU does not support long mode. Use a 32bit distribution"
What does that even mean?  
Please help, any advice would be awesome, thanks in advance!

---

### Post by tchoklat on 2007-04-25
are you sure that you have not downloaded the 64 BIT version? What is the file name of the iso you downloaded?

---

### Post by Sef on 2007-04-25
Also if you have less then 256 ram, then you should get Xubuntu.  It is made for computers with less than 256 ram.

---

### Post by x5452 on 2007-04-26
> **tchoklat said:**
> are you sure that you have not downloaded the 64 BIT version? What is the file name of the iso you downloaded?

ubuntu-7.04-alternate-amd64.iso

Is the alternate version only 64 bit?  Because on the download page here I had the radio buttons selected for 7.04 release and standard personal computer, x86 architecture.  Also the check box for alternate version.  

What IS the alternate version by the way?  Is there a special way to install it?

edit- ok so I did dl the 64 bit version somehow, some of the mirrors for download are to the wrong version...  crap, ok redownloading now...

---

### Post by Sef on 2007-04-26
> ubuntu-7.04-alternate-amd64.iso

Is the alternate version only 64 bit? Because on the download page here I had the radio buttons selected for 7.04 release and standard personal computer, x86 architecture. Also the check box for alternate version.


The alternate version also comes in 32-bit.  Here is the [alternate install]("http://mirrors.csumb.edu/ubuntu/7.04/") download.  Click on "PC (Intel x86) alternate install CD" to download the alternate cd for 32bit systems.

> What IS the alternate version by the way? Is there a special way to install it?

It is a text-based installer.  You shouldn't have any problems installing with it.  It is real easy to follow.

---

### Post by x5452 on 2007-04-26
Great, thanks a lot1

40% done download, cant wait to  try again  :)

---

### Post by Sef on 2007-04-26
You're welcome.  Please post any other questions that you have.

---

### Post by x5452 on 2007-04-26
ok I downloaded the correct  iso, ubuntu-7.04-alternate-i386.iso, and tried again.
But now when I put the cd in and reboot, I get the same menu, click install text based, cd spins up for a minute and screen goes black save for blinking cursor, upper left.  After about 1 minute cd spins down, screen remains black, nothing happens.  Any Ideas?  :confused:

---

### Post by zvacet on 2007-04-26
Did you chek CD integrity?Did you burn it on lower possible speed?If you find some errors don´t panic.Download same version with torrent and point torrent to download in the folder where your iso is.torent will just replace corrupted files with good one and after that reburn iso,but very slow.

---

### Post by x5452 on 2007-04-26
Ok this was my last attempt.  The alternate iso image I downloaded continued to not work.  So I downloaded  a torrent of the alternate install, then burned it at 1x, slowest speed I had.  Then rebooted and chose check cd for errors, screen went black with blinking cursor and cd spun up fast for many minutes, then spun down and remained at blinking cursor, nothing happened. 
I then rebooted and chose install text mode and cd spun up, screen went black, cd spun down and nothing happened.  
I guess this computer just cant handle it or what?

---

### Post by ironmonkeygf on 2007-05-05
I had the same problem, and finally found something that works...

**acpi=off** has to be added to the install options. To do this, hit F6, which should bring up the box with the parameters in it; I just added it to the end.

My symptoms, if you'd like to compare, are here:
[http://ubuntuforums.org/showthread.php?t=431866]("http://ubuntuforums.org/showthread.php?t=431866")

---

