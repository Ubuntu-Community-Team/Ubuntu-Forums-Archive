---
title: "Installation freezes"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by gneo on 2008-11-07
Hello,

Newbie here so please be gentle.

I tried installing both 8.04 and 8.10 to an old laptop (Philips freevents X52) and the installation freezes. I've tried all possible options (Live CD, install inside windows, full installation) but nothing seems to be working.

Any help would be greatly apreciated.

---

### Post by Pumalite on 2008-11-07
Ram?

---

### Post by gneo on 2008-11-07
1 gb ram

---

### Post by dabl on 2008-11-07
"Installation freezes at xx%" is the classic indicator of a problem reading the installation CD.  Either it's a bad CD burn, or the old optical drive isn't up to the job.  Linux installation CDs use maximum compression and have to be burned slowly, at 4X speed, and using DAO mode if it is available.

---

### Post by Kevbert on 2008-11-07
Welcome to Ubuntu.
Have you burnt the ISO yourself (at a slow speed) ? Checked the ISO hash ? Checked the CD integrity via the install menu ? Checked your memory via the memtest option ?

---

### Post by Pumalite on 2008-11-07
Downlo0ad and install ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Once installed; go to Mode>ISO>Burn
Select 1x speed of burn. Clean the lens in your burner.
Before burning; do md5sum on your iso.
Use only good quality CD-R

---

### Post by gneo on 2008-11-07
No "installation freezes" message. Just crashes before it starts doing anything.

I've checked the integrity of the CDs. OK.

I followed instructions and used Nero to burn the cd image.

The installation actually begins, I get the first screen, I pick the type of installation I want and then everything crashes. A hard reset is required to go back to booting Windows XP.

---

### Post by Pumalite on 2008-11-07
Post:
sudo lshw

---

### Post by gneo on 2008-11-07
Eeerrrm what?

No Linux experience here. I hoped Ubuntu would be my first one!

---

### Post by Pumalite on 2008-11-07
Boot your Live CD; get to the Desktop; there go to Applications>Accessories>Terminal.
In the Terminal; type: sudo lshw, press 'Enter'
Copy and paste the output here.

---

### Post by gneo on 2008-11-07
Thanks Pumalite. I'll do this in about an hour when I get back home ;)

---

### Post by gneo on 2008-11-07
OK,

To make it clear: The laptop currently runs WINDOWS XP and the live CD doesn't have any options to check Applications>Accessories>Terminal so I can't do this.

---

### Post by gneo on 2008-11-07
What i mean is that the live cd is not loading too...nothing works!!!

---

### Post by Pumalite on 2008-11-07
Try to boot with 'Safe Graphics'

---

### Post by gneo on 2008-11-07
and where is this option?

---

### Post by Kevbert on 2008-11-08
It looks like you may have a CD/ISO problem. Have you set your PC to boot first from the CD (via bios) ? 
I'd go for the Hardy Heron 8.04 version as it's a long term supported OS (Intrepid Ibex 8.10 will be superseded in 6 months time).
You'll need to check your ISO file that you download prior to burning at a slow speed (around x4 best), to minimize any errors. Information on [[COLOR="Red"]burning[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto") and [[COLOR="Red"]MD5SUMs[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") are available for Windows and the [COLOR="Red"][hashes]("https://help.ubuntu.com/community/UbuntuHashes")[/COLOR] to check your ISO are linked here.

---

### Post by iainv on 2008-11-09
The Freevents laptops have a hardware conflict with the sdhci module.

You need to blacklist the module on install, or install a custom kernelbuild.

All the info you need is here:

[http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm)

(I'm running ubuntu 8.04 on a freevents X59)

---

### Post by gneo on 2008-11-09
Thank you iainv,

I've downloaded the patched version and i'll give it a go as soon as I get my hands on some cds...I've burnt all of my old stash already trying this.

---

### Post by quad on 2008-11-09
Do you have a combination of IDE and SATA harddrives installed in your system?

I encounter the same problem: freeze upon installation, not even the live-cd is working.

Symptoms:
after selecting "install", the loading begins, and the harddisk activity-led on my pc stays lit.

Anyone?

---

### Post by Pumalite on 2008-11-09
Review this thread:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

