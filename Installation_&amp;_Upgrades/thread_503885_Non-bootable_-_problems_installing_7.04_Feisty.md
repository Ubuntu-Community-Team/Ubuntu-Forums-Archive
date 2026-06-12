---
title: "Non-bootable - problems installing 7.04 Feisty"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by professor-g on 2007-07-18
Found out after 2 weeks that I have been using 32-bit version of Ubuntu (loser).Fine.
There are 8 machines with this same problem.
Trying to upgrade to 7.04 feisty.
Did not remove the current version on the machine - wanting to simply use new install to wipe the old one.
Downloaded server-amd64 version from this site.
Burned to CD.

It is non-bootable for some reason - and I am not aware of how to 'make it' bootable 
(if there is some means to do so).

Options :
- make use of this seemingly non-bootable version somehow
- reburn a bootable version

I am avoiding having to re-burn a bootable version (as I dont have anymore CDs right now) and am KEEN on getting this going this evening so as to get the 8 machines immediately computing using a program compiled for 64-bit.
 
QUESTIONS: 
Is it possible to make the version I have burned on the CD bootable ?
If not - is it possible to somehow put the required files for installation somewhere on the local drive ?
If not - then on another machine and access them over net ?

Thx.

---

### Post by tgm4883 on 2007-07-18
> **professor-g said:**
> Found out after 2 weeks that I have been using 32-bit version of Ubuntu (loser).Fine.
There are 8 machines with this same problem.
Trying to upgrade to 7.04 feisty.
Did not remove the current version on the machine - wanting to simply use new install to wipe the old one.
Downloaded server-amd64 version from this site.
Burned to CD.

It is non-bootable for some reason - and I am not aware of how to 'make it' bootable 
(if there is some means to do so).

Options :
- make use of this seemingly non-bootable version somehow
- reburn a bootable version

I am avoiding having to re-burn a bootable version (as I dont have anymore CDs right now) and am KEEN on getting this going this evening so as to get the 8 machines immediately computing using a program compiled for 64-bit.
 
QUESTIONS: 
Is it possible to make the version I have burned on the CD bootable ?
If not - is it possible to somehow put the required files for installation somewhere on the local drive ?
If not - then on another machine and access them over net ?

Thx.

As long as you burned it as an image then it's bootable.  Have you checked your bios to make sure the boot order has your cd drive first?

---

### Post by professor-g on 2007-07-18
Yes - I have double checked the BIOS to ensure boot order has CD first, then HD.
Recount what I have done (I use windows VERY infrequently - thank god - but had to use it as it was the only machine with a CD burner in it):

- downloaded file (which was RAR'd - which I am not familiar with - but do know it is similar to gz and bzip2)

ubuntu-7.04-server-amd64 (WinRAR type of file - apparently)

- unRAR'd it to a directory
- burned directory
(dont see any files or anything with an .iso ending)

Directory looks as such on this windows machine (so you can recognize quickly if all-is-well):

DIRECTORIES therein:
.disk
dists
doc
install
isolinux
pics
pool
preseed

FILES therein:
cdromupgrade
md5sum
README.diskdefines
ubuntu

---

### Post by professor-g on 2007-07-18
Once again answering my own questions it seems - including why certain O/Ss are FRUSTRATING at best ...
(grrr xp ...).
It seems that this O/S here automagically opened the downloaded file (the ubuntu-7.04-server-amd64.iso) and provided me with the 'convenient' option to un-RAR (which I did). Then I burned that.
PRESTO - automagically rendered my bootable .iso image un-bootable.
Hunting now for fresh CD to burn the original un-RAR'd .iso image.
Counting the minutes before I am up and running again with something (anything) unix-based.
Thx.

---

