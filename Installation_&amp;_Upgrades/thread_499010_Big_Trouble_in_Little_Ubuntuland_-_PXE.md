---
title: "Big Trouble in Little Ubuntuland - PXE"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by workaholicbe on 2007-07-12
Hi all,

yesterday i started to install an ubuntu 6.06 LTS server on an old Dell poweredge 2500 server. All went well, partitioning...till i entered the basic installation fase ... The damned thing gave me a lot of errors like core-utils corrupt etc... So the installation process stopped at 6%... 
*My first thought : OK cd defect... let's try another CD :confused:

*Trying a new CD ...not possible...he only accepts the first CD, which gave corruption errors (because his installation has not ended yet) 

*My second thought: maybe defect CD-reader... will try to use USB DVD-writer (Lacie). Poweredge doesn't have a bios recognition (even booting with a SMARTBOOTMANAGER...or maybe i'm not capable of working with it) :confused: 

*So becoming already desperate... i started to look at other options... PXE ](*,)

*Installed tftp on my Windows XP machine in the same network (1 router&modem connects them) 
 following the link [http://www.bbc.co.uk/dna/h2g2/A6199815](http://www.bbc.co.uk/dna/h2g2/A6199815) 

Situtation:
*on the tftp i can see that there's a connection... 
 ==>on Windows XP machine (tftp) : Seeing MAC-address of target machine
*on target machine looks like i have a connection to
 ==>The cursor stops just after the words ...GATEWAY 192.168.2.1 

So my question is... what should i do? Did i miss something? 
Where should i start?  :-k

---

### Post by benanzo on 2007-07-12
I can't speak very well to the PXE issue, but my initial thought on the corrupt package errors on the disk was that you possibly downloaded a corrupt ISO.  You should go to the site you got the ISO and verify it's integrity with the checksum provided for it.  You might have to download it again.

Good Luck!

---

