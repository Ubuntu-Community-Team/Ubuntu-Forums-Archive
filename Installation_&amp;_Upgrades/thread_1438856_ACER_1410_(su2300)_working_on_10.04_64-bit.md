---
title: "ACER 1410 (su2300) working on 10.04 64-bit"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by hongsup on 2010-03-25
Hello -

I recently purchased an ACER 1410-2920 (su2300 processor), running 64 bit Win 7 Home Premium.  While the setup of the 10.04 beta1 release was fairly straight forward, I thought I'd share the steps I went through to get this working.

1) Started the download of the 64-bit Ubuntu desktop 10.04 beta1 release (this takes a while) ... [http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-beta1-desktop-amd64.iso](http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-beta1-desktop-amd64.iso)

2) I had ordered a 2gb x 2 (4 gb total) Memory upgrade with the laptop.  I installed this before even turning on the machine.

3) Removed bloatware from Win 7 & created recovery DVDs.

4) Updated Acer's BIOS (this is something that is very simple in Windows).
  a) download new BIOS from ACER website.  I was running 3113 (you can check in your BIOS config when starting up in H20 splash screen).  Go to acer.com, click on Service & Support, Driver Download, Notebook, Aspire, 1410 (11.6"), BIOS tab.  I downloaded 3303.
  b) Here's the easy part in Windows ... open the zip file, and find the 64bit version of the BIOS, and double click to launch the upgrade.  It takes 5 minutes and you have to restart.
  c) DISCLAMER ... updating the BIOS may brick your machine if you choose the wrong file ...
  d) there are a few advantages to the new BIOS including the support of ACHI for Ubuntu & WIN 7.

5) Rebooted and went into the BIOS to change the startup boot sequence to the USB DVD drive I had attached (with the 10.04 B1 release inserted).

6) Went through the install of Ubuntu via the DVD drive. (dual-boot)
  a) NOTE:  I've done a handful of Ubuntu installs, and I always get depressed when I see the blue screen / text based installation screens as opposed to the nice graphical one ... it usually means that the graphics card / drivers are not going to work ... but a bit of forshadowing here ... keep going, it will all work out :) ... also installed the GRUB loader

7) After the sandard install, I restarted and launched Ubuntu (not the default OS :P ).

8) I got a nasty flashing screen, and bad graphics on the login screen.  This was fixed by using a grub line addition noted by [pkmvancouver]("http://forum.notebookreview.com/member.php?u=310785") in [http://forum.notebookreview.com/showthread.php?p=6060987](http://forum.notebookreview.com/showthread.php?p=6060987).
  a) added "i915.modeset=0" to the grub launch line
  b) after this worked for me, I added it to the default grub launch text so I wouldn't have to enter this every time ...

9) THAT's IT ... there are a couple of quirks and minor crashes that I believe are already being worked on ... but desktop is there, wireless connection was immediate ... I was surfing the web in minutes!

10) App specifics
  a) Skype ... downloaded from skype website.
     i) webcam works by default
     ii) internal mic works after launching the app as: /bin/sh -c "*PULSE_SERVER*=127.0.0.1 *skype*" (as noted by [within]("http://ohioloco.ubuntuforums.org/member.php?u=632476") in [http://ohioloco.ubuntuforums.org/showthread.php?p=8898664](http://ohioloco.ubuntuforums.org/showthread.php?p=8898664))
     iii) I will check if it works after the mic fix under Rosetta Stone
  b) Installed Wine (via the standard packets in application control)
  c) Installed Rosetta stone under Wine (if you have questions on this, let me know).
  d) Audio Out works by default
  e) I believe I have figured out the internal mic ... I'll update here once I confirm that I have success.

Notes:
1) Out of the box, I get ~ 4 hrs of battery life under Ubuntu
2) I really like this setup, and the machine rocks ... much faster than expected
3) Hibernation works out of the box (a little slow on coming back up)
  a) shut down & startup is so much quicker than before, that I've found myself doing this instead of hibernating ...

Hope that helps.  I'll try to update as I find any issues / solutions.
thanks

---

