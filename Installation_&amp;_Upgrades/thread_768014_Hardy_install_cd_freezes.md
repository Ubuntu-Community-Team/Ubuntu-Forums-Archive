---
title: "Hardy install cd freezes"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by positron on 2008-04-26
Hi all, I recently decided to install Hardy on my pc which has been running Gutsy perfectly for several months. I have two hard drives, an IDE as master and a SATA as slave. I will list all my symptoms because I think I may have bad hardware somewhere :(

1. First I tried to install Windows XP. This was foolish of me, because I have tried before.  Every time I try to install Windows it installs fine, but does not recognize my graphics card or my ethernet port. I tried everything, I tried to manually install the drivers from the motherboard manufacturer but everything gave me errors.  Even the drivers thought my ethernet port simply did not exist! This didn't bother me too much because I would only use Windows to play games anyway.

2. Then I tried to install Hardy. The live cd freezes as soon as X starts. I either get the sweet new default background and a frozen X cursor or a blank tan background with a frozen normal cursor. I downloaded the iso file from two separate sources, burned it on two different laptops using two different brands of cds, checked the md5 sums, verified the cd etc. I know it's not the cd.

3. Found an old Gutsy cd lying around.  It boots and installs, however when I boot newly installed Gutsy off the hard drive it freezes when X starts. A blank screen comes up with the "waiting" cursor, except for the cursor is frozen.  This happens whether I install it on the SATA or IDE hard drive.  When I boot the Gutsy install in recovery mode (just the root shell) the internet does not work. Neither ping nor dig can reach the internet.

What is going on??  The gutsy live cd works so that proves my hardware works fine right?  Internet, sound, graphics, everything works. But the install messes up, and Hardy live cd doesn't work at all... And keep in mind Gutsy has been running perfectly for months.

:confused::confused::confused:

---

### Post by PmDematagoda on 2008-04-26
About booting the Hardy Live CD, did you try booting the CD using options like "noapic", also, did you try booting the CD in Safe Graphics Mode?

---

### Post by positron on 2008-04-26
Yes, I tried a wide variety of options and combinations of options, including noapic.  The Hardy Live CD doesn't have a Safe Graphics Mode that I could find though.

---

### Post by positron on 2008-04-26
I guess I should have mentioned I have a dual monitor setup. I unplugged my secondary monitor and everything works. The Hardy Live CD works. My Gutsy installation works.  I'm installing Hardy right now :-)

Now, what the heck happened? I used the exact same cd to install Gutsy last time (I think). Is there anything I can do to make sure this doesn't happen to other people? Should I post a bug report somewhere?

---

