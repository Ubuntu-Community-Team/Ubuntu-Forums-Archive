---
title: "Got 20 Live CD's today, they don't boot"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by MattB on 2006-03-01
I got a package today containing 20 sets of ubuntu install cd's and live CD's.
I don't know why, maybe because of some of the magazines I subscribe to.
Anyway, I am a MS Windows guy (with some old SCO Unix experience). What the hell, I will give this a try.  I used the install cd in a VMware VM.  Piece of cake, no problem.

OK, let's try the live CD, that might be handy.  I have tried different copies (of the 20) in 5 different PC's.  

This is not a bootable CD.  
Yes, I know how to make a PC boot from a CD
What gives?


Thanks

Matt

---

### Post by bluedog666 on 2006-03-02
Only thing I can say is... weird. I know this might sound redondant, but have you tried booting from another live or instalation CD just to make certain you machine is not developping a character ?

Alex

---

### Post by K.Mandla on 2006-03-02
Did you try the non-bootable disc in a different computer?

---

### Post by Mustard on 2006-03-02
If you browse the liveCD what contents do you find?  Files and folders or an iso image?

---

### Post by MattB on 2006-03-02
I have tried 5 different copies of the CD in 5 different PC's

When I browse the CD, I see the following folders and files:


Folders

_DISK
DISTS
DOC
ETC
INSTALL
PICS
POOL
PPC
PRESEED

Files

MD5SUM.TXT
README.DISKDEFINES
UBUNTU

---

### Post by Bartender on 2006-03-02
Matt -
What exactly does your PC do?  My home-brew P4 3.0 GHz/ASUS P5GDC-V with a Sony DVD drive refused to spin any of the Live CD's.  As you say, yes I know how to navigate the BIOS.
The DVD drive would start to spin, then stop, start,stop,start,stop, then the PC thought about it for a few seconds, then it moved on to the main HDD where it booted up just fine to W2K.
Scrounged around on the forums, and tried several different things.  Turned off Enhanced IDE in the BIOS.  The PC wouldn't even get past boot.  Turned off APCI, that didn't help either.  Tried a couple of other BIOS settings, all of which either made things worse or at the least didn't help.
At this point I'm thinking that the next thing to try is a different CD or DVD drive, but I have a test Linux PC (sig) & not sure I want to mess with the reliable primary unit!

---

### Post by daveisadork on 2006-03-02
[QUOTE=MattB]I have tried 5 different copies of the CD in 5 different PC's

When I browse the CD, I see the following folders and files:


Folders

_DISK
DISTS
DOC
ETC
INSTALL
PICS
POOL
**PPC**
PRESEED

Files

MD5SUM.TXT
README.DISKDEFINES
UBUNTU[/QUOTE]
Looks like you're using the CD intended for Power PC processors. You want the x86 version, should be the one with the red trim IIRC.

---

### Post by MattB on 2006-03-02
Bartender:
Just like you, the CD begins to spin then the HD O/S boots instead.  I tried another boot CD (Barts PE) to be sure, it will boot from it just fine.

I had no problem booting from the install CD in VMware.  

Dave:
The CD Sleve doesn't say anything about PowerPC, just says a "PC with 128 MB Ram"  The CD is red ????

---

### Post by Bartender on 2006-03-02
Hmmm - the plot thickens -
Matt, I downloaded and burned the Kubuntu .iso a month ago.  I'm gonna call my home-brew machine PC1.  I used PC1 to d/l & burn the Kubuntu CD.  That CD installed just fine to the PC in my sig.  Call that PC2.  

PC1 recognizes the Kubuntu CD, which looks like this...


.disk
dists
doc
install
isolinux
pics
pool
preseed
md5sum
README.diskdefines
ubuntu

*No PPC folder!*

I've got another old beater - PC3.  I fired it up just a few minutes ago.  It recognized both halves of a stamped Ubuntu set; the Install & the LiveCD.  I explored both of those, again no PPC folders.  The back of the package says, "This PC Edition will run on Intel x86-based systems (including Intel Pentium and AMD Athlon).

Our symptoms are identical, and I was hoping that your post might help me resolve my questions.  But to me it looks like dave identified the problem.  Some of your CD's appear to be for an Apple.  Maybe some of them aren't?

---

### Post by MattB on 2006-03-02
Bartender & Dave:

You are correct!

I looked at all 20 of the CD's.  8 of them towards the bottom of my stack do have different contents and do boot!

This is the contents of the working CD:
folders:

.disk
bin
casper
disctree
dists
doc
install
isolinux
pics
pool
preseed
programs

files:

autorun.inf
md5sum.txt
README.diskdefines
start.bmp
start.exe
start.ini
ubuntu





All 20 CD's and their sleeves look exactly identical.  I guess that some of the MAC CD's were miss-labeled and put into the PC sleeves.

Thanks for your help

---

### Post by CodeMasterMike on 2006-03-06
Ive got the same filestructure as it above, but mine still doesnt boot at all.
Im using a Dell computer.

I restart, choose to boot from cd, the computer thinks about it for a second or two, then decides to load windows.

Any other theories about this issue?

I can say, that I couldnt burn the image directly, I opened it in in a virtual dvd, copy paste the files directly to a cd, and burned it.
The cd works fine within windows, the little explorer window-thingy comes up.

---

### Post by Bartender on 2006-03-06
Hi, CMM -

My W2K (PC1) won't boot from, or even recognize & allow me to explore, any of the LiveCD's or install CD's I received.  Took those same CD's & tried booting to 2 different PIII machines - no problems.  Didn't try booting to my old PII 400 (PC3) but it was at least able to recognize & explore them.

Your Dell notebook behaves the same as my desktop.  Well, not quite, if you can at least explore the CD's.  I feel sure it's hardware-related, but is it motherboard, DVD drive, SATA vs. PATA?  Somebody knows what those symptoms indicate, but not me!

---

### Post by CodeMasterMike on 2006-03-07
Thanks for the reply!

I think you have a point there. When I was sitting and thinking about it, I realized that I had an old live version of slackware hiding somewhere dark and smelly. And that one booted as it should.

Now, I am no genius, but as far as I can see, I have to bite the bullet, and find me another Linux-os (or another Ubuntu version instead of Breezy?), since it my hardware is not letting me go easy with Breezy.

---

