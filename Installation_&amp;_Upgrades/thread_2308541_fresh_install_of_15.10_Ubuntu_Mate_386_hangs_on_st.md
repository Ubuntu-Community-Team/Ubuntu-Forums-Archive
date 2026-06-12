---
title: "fresh install of 15.10 Ubuntu Mate 386 hangs on startup"
date: 2016-01-04
forum: Installation &amp; Upgrades
---

### Post by Jay_E on 2016-01-04
Greetings...
-> Not consistently Reproducable. <-

I'll do my best to document the problem.
Thanks in advance.

I have an older 686 that was running an much older version and I decided to change to 15.10
The  upgrade to 15.10 had problems, so I decided just to wipe the partition and reinstall.
(see notes on details of where it hung further on..)

I tried both a USB and a DVD - but fail in the same way.

I went further back and burnt a DVD with Debian 8.2.0 Mate for 386 ( with 686 PAE option) and it worked OK.
I also tried Debian 8.2.0 Gnome  for 386 ( with 686 PAE option) and it worked OK.

I reloaded the ISO, then burnt another DVD.  Problem is still there.

So. 99.9% sure that  the problem isn't in the download media.

Where it hangs:
  Initial install runs OK. ( do not do upgrade at this time; but test to see if it  Ubuntu Mate 15.10 386 will reboot.
  First reboot with name and password works OK.
  got /etc/apt and edit sources.list - add restricted, universe , multiverse, and the Canonical partners...
  Install aptitude
   Did an aptitude update.
   (also did an install of my favs - rcs, sl, and gnuplot - nothing too exotic)
  
Reboot.
Hangs before user logon.

The default background is there, but no bar at top nor bottom. No icons of any kind visible. No cursor.
I did wait for 3 hours.  No disk noises of head movement. Very slow fan speed.
<ctl> C did not work.
<ctl> <alt> <delete> did not work.

I was able to stop it by forcing a power-down (hold power button > 15 seconds.
[ start non-sequiter }
-- tried doing something close to this by running the "Try Me" option on the install media (DVD).
Not a good idea: tried update and upgrade, but aptitude could not replace code on the read-only media.
Near the end, dpkg reported 2 errors - cups and ubuntu-release-upgrader;
unrecoverable fatal error. Then it tried to flush a tmp dir in var/lib.... and ran out of space
But on another occasion the hung after a display timeout of a black and white checkerboard.
[ end non-seqiuter ]

========= Try again ============
Able to start; login; see desktop; use firefox.

========= Try again ============
FAILS. (grub screen visible. I let it timeout and choose the default;
           Get a garbled screen for a few seconds;
           Get Ubuntu progress display (moving dots);
           Get the default backgound ;
           Hang.No cursor, Nothing for <ctl>c  or <ctl>alt> <del>
         had to force stop. I'm sure a chkdsk will be scheduled next time...

========= Try again ============
(grub screen visible. I let it timeout and choose the default;
           Get a blank, then garbled screen for a 25 seconds; (assume a chkdsk  in progress?)
           Back to the default background screen - with a difference
             a rectangular bar (a progress bar) off to left side, 50% filled solid light, lime green, 50% black)
           I wait 10 minutes this time before touching keys or touchpad.
           Fails. Hangs.

========= Try again ============
This time I select the default "UBUNTU" option on the GRUB menu before it times out.
Get the moving progress dots for about 15 seconds.
Then, default screen and Hang.

========= Try again ============
This time, I go for the advanced options;
       run fsck - it runs & finishes.
       drop to root; do a 'df' - looks OK 19% used on /; 20% used on /home
       give a Reboot command;
       REMOVE ETHERNET CABLE.
       GET the checkerboard pattern on entire screen.
       Force power off
========= Try again ============
       Select the default "UBUNTU" option on the GRUB menu before it times out.
      (Ethernet cable still unplugged.)
        Get Login screen. Login.
       PASSES! Starts up.


OK.  thanks for bearing with a *long* explanation..

I looked at problem reports. went through 4 pages - didn't see a similar prob.

Should I write a prob report?

Anyone else have an idea??

My best guess: There was a change in systemd. Maybe a race of async start ups for the 386??

Thanks again
Jay

---

