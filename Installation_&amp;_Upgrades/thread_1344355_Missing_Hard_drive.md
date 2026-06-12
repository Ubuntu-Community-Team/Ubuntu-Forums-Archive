---
title: "Missing Hard drive"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Bert_421 on 2009-12-02
Decided to do a clean install of 9.10, formatted the drive and went to install the software now the hard drive is not visible in the install set-up. If i go to the gparted in ubuntu it sees the drive i want to install, if i go the disk utility the drive is visible. 
What am i missing?    

9.10 64 bit cd
250gb hard drive 

p.s i had 9.04 and ultimate edition on same drive. i upgraded to 9.10 from 9.04 without any problem.

---

### Post by Ginsu543 on 2009-12-03
Give this a try:

1) Boot into live session with 9.10 Live CD (without installing)
2) Open a Terminal and run "sudo apt-get remove dmraid" (without quotes, of course)
3) Exit the Terminal and start the Installer by double-clicking on its icon

I had the same problem as you did, but this helped me get around the problem. If all goes well, you should be able to see the hard drive during install.

---

### Post by Bert_421 on 2009-12-04
Thank you Ginsu543 that did the trick.

---

### Post by Ginsu543 on 2009-12-05
Excellent!

---

### Post by Christian&gt;&lt;&gt; on 2009-12-08
I am having the same problem with nearly the same hardware configuration.  I tried the fix and it did not work.  I still cannot install onto the hard drive...:confused:

---

### Post by Ginsu543 on 2009-12-08
Have you tried using the alternate CD? Others here who have had this issue have had success installing Karmic using the alternate CD instead of the Live CD. The alternate CD uses a text-based installer rather than a GUI like the Live CD.

---

### Post by brewster1134 on 2009-12-19
that solution worked great!

but then when i later wanted to reinstall using the minimal cd, that same drive wouldnt show up.

how would i achieve the same thing using the minimal cd / text installer?

---

### Post by bluedalek on 2010-10-16
> **Ginsu543 said:**
> Give this a try:

1) Boot into live session with 9.10 Live CD (without installing)
2) Open a Terminal and run "sudo apt-get remove dmraid" (without quotes, of course)
3) Exit the Terminal and start the Installer by double-clicking on its icon

I had the same problem as you did, but this helped me get around the problem. If all goes well, you should be able to see the hard drive during install.

Done this on many other installs and had it work flawlessly.. trying to install on an HP G62 laptop, and it's not working.  Am able to launch the live CD, but as the previous posters, is not detecting the hard drive.

Another option that I saw posted on here previously, is to go into the BIOS and change the HD from SATA to IDE (compatibility), do the install, then change back after.

HP, in their wisdom, has locked the BIOS down and am unable to make any significant changes.

Other than the text based installer, any other thoughts or options?

Thanks in advance!

---

### Post by bluedalek on 2010-11-09
Fixed the installation issue... removed the hard drive, inserted fresh-from-package SSD... :KS

---

