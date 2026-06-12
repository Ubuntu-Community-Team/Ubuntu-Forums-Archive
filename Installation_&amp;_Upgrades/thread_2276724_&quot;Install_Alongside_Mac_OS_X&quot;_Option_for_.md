---
title: "&quot;Install Alongside Mac OS X&quot; Option for Ubuntu 14.04 Missing on Macbook Pro 6,2"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by bzodonnell on 2015-05-04
[COLOR=#111111][FONT=Ubuntu]I am trying to install Ubuntu 14.04 on my Macbook Pro 6,2 (mid-2010) alongside Yosemite. Using this [handy guide]("http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/"), I installed rEFInd and made a bootable USB drive. I had some problems starting the installer from the bootable USB, so I instead burned the .iso to a DVD.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When I put the DVD in, rEFInd recognizes that the DVD is a bootable drive, and I can boot off of it under the "Try Ubuntu" option. I then run the installer, but instead of giving me the option to "Install Alongside Mac OS X", it says that Ubuntu did not detect any other operating systems, and gives the me the options to erase my disk, or do the process manually ("Something else"). I tried using the computer's built-in boot option by pressing alt upon startup, and had two disk icons: Windows and EFI Boot. EFI boot didn't get me anywhere, but Windows got me to the same Try Ubuntu screen, but with the same problem.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've got a 1 TB hard drive with 900 GB partitioned to HFS+ for Yosemite, leaving about 100 GB of "Free Space."

Any ideas?

(Also, I wasn't sure if this belongs in the "New to Ubuntu" subforum instead. Sorry if I posted to the wrong place, hah.)[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2015-05-04
Hi and welcome.

Use 'Something else' to deal with the partitions and then install as normally.

---

### Post by bzodonnell on 2015-05-04
Got it. So it won't be a problem down the line that Ubuntu doesn't recognize OS X?

---

### Post by yancek on 2015-05-04
I don't think Ubuntu will be able to write to a Mac as a default install.  Some info on the link below on the software you will need.  

[http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

---

### Post by bzodonnell on 2015-05-04
Okay, cool. Looks like I won't be able to screw up my OS X installation then by toying around with Ubuntu. Thank you for your help!

Out of curiosity though, is there any known reason why the "Install alongside" option doesn't always work on Mac OS X?

---

### Post by yancek on 2015-05-04
I don't think Ubuntu will be able to write to a Mac as a default install.  Some info on the link below on the software you will need.  

[http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

---

