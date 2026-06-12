---
title: "auto supergrub on USB - invalid system disk"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by uberdonkey5 on 2008-07-29
Dear community - please help!

I was trying to get rid of Dell Media Direct on my dual boot (windows and hardy heron) laptop because I wanted to free more space for ubuntu. I wiped the files, then using Windows (Vista) I got rid of what I thought was the paritition where it was stored. I'm guessing I was wrong.

My other computer at work can't burn CDs (and only has windows) so I tried auto supergrub to install files on a USB device. It downloaded 3 files onto the USB. When I try to boot from the USB drive (I have 4 ports) it says Invalid System Disk.

(Ideally I would boot from the CD, and I tried SIX copies of hardy heron but I am guessing the images were bad because it only ever goes to the screen where it gives 6 options - any option just gives a temporary pause before doing nothing and allowing another option).

Please please, any advice. PS I don't have access to another linux machine. Also, I am pretty inexperienced (as you can tell!)

thanks,
Ian

---

### Post by uberdonkey5 on 2008-07-30
OK! well I used UNetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
to create a version of Ubuntu 7.02 on a USB, using my windows system (it was VERY simple) and worked first time.

HOWEVER. Now I get this message (after the Ubuntu emblem and load up bar):

Failed to start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem (yes/No)?

If I press Yes all seems normal except for:
(EE) NV(0): No display devices found
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found

Going into the detailed output I get:
directory "/usr/share/fonts/X11/cyrillic" does not exist. Entry deleted from font path

well, I'm guessing that helps to suggest what partition I reformatted (it was around 4GB on a 260GB disk, and I know it is neither my data or the two operating systems)

PS. I now have a command line on the USB stick

---

### Post by uberdonkey5 on 2008-07-30
OK, well I am guessing that the USB stick method was duff...
... I managed to get a WORKING CD copy of Ubuntu (8.04) from a friend.

I booted from CD drive and am currently backing up all my data from ubuntu into the windows partition, and also onto hard drive or disks.

I hopefully can then either repartition (though I am very wary of this now) or reinstall ubuntu (which I guess is better option) and select a larger space for the ubuntu partition

---

### Post by uberdonkey5 on 2008-08-01
well, in my monologue...
backed up, completely reinstalled dual boot. The windows recovery program was a piece of sh**.. despite the fact that all I was missing was my boot partition I could not access this or really do anything useful with the recovery program (possibly cos I also formatted it differently as well).

What have I learnt during this?

1. **ALWAYS keep a working copy of the ubuntu CD**
2. Even if you think you will use ubuntu more than windows, the speed with which you can copy files in ubuntu must by at least 10 times that of windows and thus I tended to keep larger files (like videos and photos) on ubuntu. THUS - **an equal partition split (50-50) is advisable**, even if you think you won't use it at first.
3. It is best NOT to have a seperate home partition (it makes absolutely no difference, except extra hassle... see other threads)

ALSO BACK-UP regularly (preferably with a good external hard drive, which is much faster and easier than DVD). This is the 3rd time I have reinstalled in 1 year. I am guessing it may happen again. This is now my long term operating procedure:

1. Keep a list of software you install on ubuntu and windows (and notes of how to deal with problems installations) so you can reinstall the identical system easily. (and for windows, keep the CDs!)
2. Back up regularly
3. keep email and bookmarks on-line (e.g. gmail) rather than on your computer.
4. Keep all your files in the home directory so back up is easy.
5. Think long and hard about the partition when you start your computer and don't mess around with it once it is done!

In this way if you have ANY problems like viruses or old files that you can't get rid of filling your system, you can backup, reformat and start again. Indeed, I wonder if ubuntu users have ever considered copying all their downloaded software to a CD before executing it, and then using this CD as a method of quick reinstall?

I hope somone, somewhere, out there in the mysteriously silent ubuntu community finds this useful

Ian

---

