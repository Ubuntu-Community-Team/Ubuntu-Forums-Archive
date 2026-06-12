---
title: "Ubuntu blank screen"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by ttiell on 2008-01-20
There seems to be many posts on this promblem.  But all of the answers are tailored to those people's specific problems.

My System
Pros - Pentium E2140
Mobo - Intel DP965LT
Ram - 2GB (1x1) Munshkin DDR2 800
Vid Card - Nvidia 8400GS 256 MB 64-BIT GDDR2
IDE Harddrive (75% XP Pro, 25% left over for Ubuntu)
Second Partition isn't made yet.  planned to do it with Ubuntu install

If I use the LiveCD (x86), My screen comes to main menu, I can run memtest and verify CD.  If I go into Ubuntu 7.10, I get a black screen.  If I go intu Safe Graphics Mode, I get "display server shutdown 6x in 90 seconds...waiting 2 minutes before trying again with an OK button.  It then gets to running local boot scripts 6 times before going back to previous screen.

If I use the alternate CD (x86), My screen comes to main menu, I can run memtest and verify CD.  If I go intu Ubuntu 7.10, I get a black screen and continuos beebing until I do a Hard shutdown.  If I go into Safe Mode Graphics Mode, I get the same thing.

I also can't get wingrub to install.  Problem is that when I go into run-cmd.  The cammand prompt comes on right away...waits half a second, then closes itself.

If anyone can help me on my particular problem.  That would be great.  Thanks

---

### Post by gsiliceo on 2008-01-20
Go into ubuntu and then the blank screen appears, hit ctrl+alt+delete
If that works, install restricted software for the nvidia drivers
If it doesnt type ctrl+alt+f1 to command line, login and then type
dpkg-reconfigure xserver-xorg, when asked choose the "nv" driver, for the rest of the questions left the default options. Reboot
If you get a blank screen again, try again the last command and this time go forthe "vesa" driver.
Provide feedback =)

---

### Post by ttiell on 2008-01-21
still need help, I think.

the ctrl+alt+del didn't work
the ctrl+alt+f1 did send me to a command prompt.  I don't have a log-in at this point but I was able to do sudo commands.  The "nv" driver did nothing.  The "versa" driver was a lot better but... When I would try to start Ubuntu after the reboot.  I didn't have anymore glitchy graphics.  The screen still went blank after the orange bar filled up and got to the end.  However, my moniter never clicked off.  I mean it never lost a signal from my computer.  But it still did stay blank.  I left it like this for about tem minutes.  Do I need to be more patient?  about how long should I wait if I do need to wait longer?

side note: I got my cammand prompt to come up in windows (to install wingrub).  The "run" command "cmd" wouldn't work.  So I typed out "command prompt".  That worked perfectly.  This makes for another good reason to try to leave the silly windows enviroment.

---

### Post by PmDematagoda on 2008-01-21
Are you sure that you got the Alternate CD and not the Live CD when you said:-
> If I use the alternate CD (x86), My screen comes to main menu, I can run memtest and verify CD. If I go intu Ubuntu 7.10, I get a black screen and continuos beebing until I do a Hard shutdown. If I go into Safe Mode Graphics Mode, I get the same thing.

The above is usually true of Live CD's since they are graphical whereas the Alternate CD's are text-based installers and are not affected by incompatible VGA cards.

You can get the Alternate CD from [here]("http://releases.ubuntu.com/7.10/").

---

### Post by ttiell on 2008-01-23
Ok, I re-downloaded the alternate cd.  It verified ok.  It installed Ubuntu.  But now my computer won't start up.  I get past bios and then get a error 13 (no executable *).  i'm guessing that the ubuntu re-wrote my mbr.  I tried SuperGrub cd and couldn't get it to work.  the only thing I could get supergrub to do was to boot into ubuntu but then the screen would just go black.  If anyone has any ideas on this, that would be great.  If i don't hear anything.  My plan is to put this harddrive into slave and try to fix the mbr from another windows computer.  If anyone knows what my mbr should be, supergrub will let me type it directly in.
a little background for the mbr
this is 1 ide harddrive
partition 1 is Windows XP Professional SP2 (primary)
partition 2 is Ubuntu 7.10 (primary)
partition 3 is Swap drive made by Ubuntu (logical)
I also did have wingrub working on partion one before the Ubuntu install
thanks for any help

---

### Post by ttiell on 2008-01-23
I found my note on what I could read when I got the error.  This may give more info.

set aux_hd="hd0"
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0 0 300
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0x1fe2
rootnoverify (hd0,0)
makeactive
chainloader +1

Error 13: Invalid or unsupported executable format

---

