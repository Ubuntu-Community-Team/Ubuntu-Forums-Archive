---
title: "Cannot install ubuntu on HP m7160n"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by tksownz on 2008-04-21
I am receiving multiple errors --"exception Emask" when trying to boot from the live cd with all versions of ubuntu.  Eventually, if I dont touch my computer then the live cd will eventually make it to the GUI.  Then I try to format and install but the live cd cannot see any of my harddrives.  Any help would be greatly appreciated.

---

### Post by Pumalite on 2008-04-21
This might help:
[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)

---

### Post by tksownz on 2008-04-21
Ill check that out, but I believe the problem lies with the harddrive from HP.  I am still trying to figure it all out, also alot of those resources are for laptops, I dont believe that I would be experiencing the same problem as them, but who knows, right?  Thanks

---

### Post by Pumalite on 2008-04-21
Are you using Vista or XP?

---

### Post by tksownz on 2008-04-21
Windows Media Center 2005

---

### Post by crs0328 on 2008-04-21
I actually have (or at least think I have - I'm at the office) the exact same computer and had alot of trouble getting Ubuntu installed.  But the good news, I eventually got it installed.

Is your hard drive by any chance a Maxtor?   If it is, you might consider replacing the hard drive.  I got Seagate and it really made all the difference. Apparently, that particular type of Maxtor HD that shipped with our computer, something about it made the Linux kernal freak.

Anyways, I replaced the hard drive, and put in the Gutsy liveCD.  I still was getting an error, so I did some search and found by putting:  all_generic_ide   at the end of the grub installer line (hit F6 at the liveCD screen and enter that after the - quiet splash --)  and it installed.

It would look something like:  file:// <something> quiet splash -- all_generic_ide

You might try doing that with your current hard drive and it might work, but I opted to replace it.

Also, as of now, I haven't been able to get the Hardy beta version working.  So, if I were you, I'd start with Gutsy.

---

### Post by Maintech on 2008-04-21
There is a kernel bug that hits the new chipsets. One of the fixes is to put --nomsi into the boot option. That is what I had to do to mine.

---

### Post by crs0328 on 2008-04-21
Oh that's cool.  I actually didn't run across that in my searching, but if that works too, then great.  I only wish I'd tried that before I bought a new hard drive.  I know I had a very difficult time installing, not only Ubuntu, but most every other popular distro.  I guess that makes sense if it is a kernal bug.  Oddly enough, the only distro I got to work straight out-of-the-box, was PCLinuxOS Gnome 2008.  Perhaps they are using an older kernal?

---

### Post by Maintech on 2008-04-21
Mandriva, SuSE, and PCLinuxOS all set the kernel --nomsi as their standard install. You'll have to ask them why. All of those would load on my computer but no Ubuntu would. I tried everything. Then I ran across a forum about the new kernels and that was one of the subjects being discussed. It needs to be put up as a sticky.

---

