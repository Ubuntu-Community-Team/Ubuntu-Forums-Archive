---
title: "Monitor &quot;Frequency Overrange&quot; during CD start up"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by jkvv_1973 on 2006-09-25
I have a radeon pro9700 with a Viewsonic CRT 19" monitor...

I have Ubuntu 6.0 CD

I start to boot up and choose CD/Install option
loads up UBUNTU splash screen

my monitor signals "FREQUENCY OVERRANGE"
then does standby...I

from here I cannot revive monitor...

what should I do???](*,)

---

### Post by Cai876 on 2006-09-25
i am having similar problems but with 6.06

---

### Post by jkvv_1973 on 2006-09-25
oops:o  I meant 6.06

hehe nice to know someone had the same prob...I guess will wait for answer...if not Im looking @ FEDORA:-k

---

### Post by wpshooter on 2006-09-25
If you WAIT does the installation of Ubuntu not evenutally proceed ?

Are you using the DESKTOP CD or the ALTERNATE CD ?

---

### Post by jkvv_1973 on 2006-09-25
I wouldnt know if it continues...it loads the splash screen and it gets to 60-70% then I get the monitor black out...but the drive does seem to read on...

as to the cd its the Desktop CD...:D

---

### Post by wpshooter on 2006-09-25
How long are you waiting after the screen goes blank ?

All of my 3 computers that are using similar video cards to yours, did this same thing, but after waiting a brief period the CD went on to the desktop.

This out-of-range problem has to be corrected once you get the O/S installed.


Also, have you checked the integrity of the CD with the verification function that is located on the initial Ubuntu boot screen menu ?

If after checking the CD integrity and it passes and you still get this same behavior, i.e. it will NOT go on to the desktop after the screen goes blank, then download and try the ALTERNATE CD.

Write back if you need more help.

Good luck.

---

### Post by jkvv_1973 on 2006-09-26
hmmm...I assumed it wasnt going back up cause it took to long after I showered... I will try again and wait longer...oh and btw I dont plan to install the os just yet...just wanted to boot from cd...

when you say "fix it" how?

if all else fails Ill try the alternate cd...thanks for the help!;)

---

### Post by Cai876 on 2006-09-26
my problem is different. after it loads from the first menu it goes blank.

---

### Post by wpshooter on 2006-09-26
> **Cai876 said:**
> my problem is different. after it loads from the first menu it goes blank.


Make sure you check the integrity of your CD by running the verification function from the initial Ubuntu boot screen menu.

If it passed that and still will not go on without going blank then download and try the ALTERNATE CD version.

Good luck.

---

### Post by jkvv_1973 on 2006-09-26
FYI...

someone in the forums had the same problem...he was able to solve this black out thing (he was using the alternate cd ) he would choose the VGA option (on the boot up menu) and only pick the 640x480 resolution...I will also try that...

---

### Post by needlenose on 2006-09-26
I'm also having this problem. I'v set my resolution to every option givin at boot up with no luck. I'm currently running WinXP and openSuse 10.1, I've tried changing screen resolution on both os before rebooting to Ubuntu 6.06 LTS DVD with no luck. I'm looking to switch from SUSE to UBUNTU because I can find more support in both print and on-line.

hp pavilion 743c
Compaq fs940 (Monitor)

Thanks in advance for any help you can provide.

---

### Post by jkvv_1973 on 2006-09-28
update:
I tried the same thing you did...and it still wont boot up (differe nt res...) DESKTOP CD

I also checked the integrity and the cd was fine.

I tried VMWARE on another computer with this cd and it just sort of hangs in the brown screen...with ubuntu box....

NEXT STEP...

will try the alternate cd...

---

### Post by dcstar on 2006-09-30
> **jkvv_1973 said:**
> update:
......
will try the alternate cd...

You can install the server (non-GUI) version with that CD, and then later install the ubuntu-desktop meta-package to get the X stuff.

Once you have the basic system up you can then later edit the /etc/xorg.conf file (if necessary) to manually set the refresh rate to suit your monitor.

---

### Post by JGuru on 2006-09-30
You can solve the problem by booting in **Safe Graphics Mode** or
 if you are using a Ubuntu CD, press F4 or F5 (I don't remember exactly)
 that'll display the VGA options, choose '800x600' screen resolution. 
 See if it solves your problem.

---

### Post by GadgetsGuy on 2006-09-30
See if this helps you

[http://www.hotubuntunews.com/blog_03.shtml](http://www.hotubuntunews.com/blog_03.shtml)

---

### Post by ryboto on 2006-10-01
I've got a thread about this same problem.  I have an x800 video card.  I've tried the desktop cd, and alternate cd.  The desktop cd will load, I'll see it go through a checklist, and then the monitor loses signal.  I've checked the disc for errors, it has none.  I've tried forcing the resolution, using the options at the bottom of the screen to 640x480, and 800x600, still, blank screen.  I tried the safe mode, still, blank screen.   I used the OEM install on the alternate disc, the installation finalizes, i reboot, ubuntu load screen is visible, but then the monitor goes blank.  If i type my username, hit tab, then password, and enter, i hear the ubuntu startup sound.  I waited a few minutes until the hard drive had stopped being accessed, and still, blank screen.  

I'm having similar trouble with debian, startx returns a missing display error.

---

### Post by dcstar on 2006-10-01
> **ryboto said:**
> I've got a thread about this same problem.  I have an x800 video card.  I've tried the desktop cd, and alternate cd.  The desktop cd will load, I'll see it go through a checklist, and then the monitor loses signal.  I've checked the disc for errors, it has none.  I've tried forcing the resolution, using the options at the bottom of the screen to 640x480, and 800x600, still, blank screen.  I tried the safe mode, still, blank screen.   I used the OEM install on the alternate disc, the installation finalizes, i reboot, ubuntu load screen is visible, but then the monitor goes blank.  If i type my username, hit tab, then password, and enter, i hear the ubuntu startup sound.  I waited a few minutes until the hard drive had stopped being accessed, and still, blank screen.  

I'm having similar trouble with debian, startx returns a missing display error.

When the screen blanks, press CTRL-ALT-F1 (at the same time) and you should get a text login screen.

You should be able to log in and do some diagnostics then.

---

### Post by ryboto on 2006-10-02
> **dcstar said:**
> When the screen blanks, press CTRL-ALT-F1 (at the same time) and you should get a text login screen.

You should be able to log in and do some diagnostics then.

what could I do as far as diagnostics go?  I'm relatively new to linux..again..

---

### Post by jkvv_1973 on 2006-10-13
I burned a new install cd...so far it blacks out still on normal start...I tried safe mode and Im good...

Im currently trying Ubuntu and trying to partition one of my drives...so Im happy for now...

thanks for all your help...crossing my fingers during the partitioning process...

thanks

---

### Post by jkvv_1973 on 2006-10-15
Hello Ubuntu Users,

I just wanted to officially say after going through install problems I finally got Ubuntu to work...I never really had the time to trouble shoot so it was just now that I had it up and running the way I wanted it to...

First of all I want to mention that if anybody had "grub errors" (I had grub error 22)...that the "Super Grub Disc" helped alot (google it)

now Im using Ubuntu but still have one of my drives dedicated to windows xp...Im probably going to use Ubuntu alot to do simple basic stuff like browsing and maybe cd/dvd burning...as I find win xp to be troublesome on my aging AMD pc (xp2400)

Linux seems to use alot less resources ( half of what winxp consumes) and thats nice to know...

my problem now is to get macromedia flash installed...aye](*,) 

thanks all for your help...this thread should be considered resolved...

---

