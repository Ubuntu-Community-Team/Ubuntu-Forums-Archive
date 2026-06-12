---
title: "An other Hardy 8.04 install problem"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Thespian on 2008-04-27
Just tried to install 8.04 from the live CD.  The kernel loads, the Ubuntu logo comes up, the orange bar goes back and forth, then (running form liveCD) I get the basic Ubuntu beige background screen with a mouse pointer that won't move, and nothing happens, or (booting from disk after using the Windows installer) I get the Heron background, with a non-moving mouse pointer.  In both cases, the system just hangs.  No error messages, no response to keyboard or mouse, just dead.

I tried one of the other forum thread suggestions of adding "noacpi" to the boot options with no effect.  I've run memtest on my machine (all good) and I've verified the CD burn (also good).

Any suggestions on what to try next?  This machine ran Fiesty and Gutsy form LiveCD just fine.

Thanks,

Thespian
------------------
Desktop system specs:

Windows XP Professional Service Pack 2 (build 2600) 	  	
1.60 gigahertz AMD Athlon XP
128 kilobyte primary memory cache
256 kilobyte secondary memory cache 	  	Board: ASUSTeK Computer INC. A7V266-E REV 1.xx
Bus Clock: 133 megahertz
BIOS: Award Software, Inc. ASUS A7V266-E ACPI BIOS Rev 1011 08/20/2002
Drives 	
200.04 Gigabytes Usable Hard Drive Capacity
20.96 Gigabytes Hard Drive Free Space

PIONEER DVD-ROM DVD-116 [CD-ROM drive]
PLEXTOR DVDR PX-760A [CD-ROM drive]

ST3200822A [Hard drive] (200.05 GB) -- drive 0, s/n 5LJ0YX9M, rev 3.01, SMART Status: Healthy 	  	1536 Megabytes Installed Memory

Slot 'DIMM 1' has 512 MB
Slot 'DIMM 2' has 512 MB
Slot 'DIMM 3' has 512 MB
-------------------------------------

---

### Post by sysyphus on 2008-04-27
Try booting up in recovery mode, you should be able to see where the hang is (I'm having similar issues)

---

### Post by Thespian on 2008-04-27
Sysyphus, I'd be interested to know what you find out.  

How does one boot Ubuntu in recovery mode, and where should one look for the cause of the hang?

Thanks,

Thespian

---

### Post by Thespian on 2008-04-30
I didn't see a "rescue mode" on the boot options.

I did try hitting Ctrl-Alt-F1.  All I could tell was that everything seems to start "OK" then it begins Ubiquity, the Heron image appears, there is an "X" cursor for a few seconds which responds to mouse movement, then the cursor turns into an arrow pointer, and everything stops responding.  no mouse, no keyboard, no disk activity, nothing.

Still looking for suggestions.

Thanks,

Thespian

---

### Post by housam on 2008-04-30
Try the alternate cd.

---

### Post by Thespian on 2008-05-03
More info and an other question.

By adding "noapic" and "acpi=off" to the boot line for the installer, the boot was able to complete.  Heron screen came up, many files were copy and configured, and all seemed to go well.

Now when I try to boot up (even adding those options to the boot line) I get all the way to the login screen.  At this point, the mouse still works.  But immediately after entering the login password, I get the same symptom as before... beige screen, and system hangs.  Cursor and keyboard non-responsive.

The fact that the options help the install boot complete makes me think it's related to that, but I'm not sure what needs to be changed, or what is called after successful login.

Any suggestions for log files I can look in?  I at least now can get a working shell prompt.

Thanks,

Thespian

---

### Post by Thespian on 2008-05-22
I've been scanning the forums off and on, and trying various suggested fixes, and nothing has worked so far.  There are a lot of similar symptoms being reported from a number of different causes.

Most likely candidate seems to be a problem with gnome-keyring-demon.  A number of other threads have talked about fixes, but none of what's made it to the current mirrors has fixed my problem.

The symptom is: a few seconds after logging in, before the desktop shows up, everything freezes.  This happens only most of the time, not all, and it happens after a reboot between which I've changed nothing on the system.

Many other folks with Nvidia cards seem to be having the issue, but it doesn't seem to be related to the drivers.

I'm still not seeing any errors in any log files, and once the problem hits, the whole system is locked.  I thought going into the "failsafe terminal" and manually starting "gnome-session" had fixed it, but the 2nd time I tried it, same lock-up.

I'd really love to know if anyone else has hit this.

---

