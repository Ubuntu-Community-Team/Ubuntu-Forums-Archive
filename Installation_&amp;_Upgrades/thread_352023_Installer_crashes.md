---
title: "Installer crashes"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by jcsewell on 2007-02-02
Hi, I'm having major problems installing Edgy.

It's a new machine.  I upgraded my 6 yr old PIII to an Athlon 64 3200+.  Of course this required new mobo, 512MB RAM and video card, so it's essentially a new machine.  I kept the old case (needed a new ATX 2.0 PS), IDE HDDs and optical drives.

The live CD boots OK, and I get through the "questions" portion of the installer.  I am wiping the drive and letting the partioner do what it wants.

The installer gets through the partitioner, seems to copy files OK, and crashes after that.  It's never at the same point.  I've installed 5+ times and it always crashes but never at the same point.

Early in my attempts to install, I actually got it all the way installed, then after booting the first time and trying to update the packages, it crashed during the update.  It munged X and would not load the GUI when I rebooted.  I re-installed and got the GUI back, and did the update again and it crashed again during the upgrade.

At this point I attempted to install Windows 2000 (sacrilege I know).  That also went badly.  The character mode portion of the installer went OK, but I had problems when the GUI install came up.  At one point, all the characters were typing on top of themselves and I couldn't read what it said.  Another install attempt went better, and I actually got the OS to boot and log in.  Then I installed network and sound drivers and rebooted.  Then I got STOP errors on bootup complaining about different .sys files (several reboots, different .sys files every time).

I thought maybe it was a flaky or bad BIOS, so I flashed to the latest (ASUS A8S-X mobo, shipped with BIOS 0501, flashed to 1001).  This has not helped either OS get installed.

I thought maybe the HDD was a problem (not likely as this drive has been rock solid for 6 years).  So I swapped it out with an old 10G drive I had lying around.  I haven't installed 2000 since doing this, but Edgy still crashes in the installer in the same way (but never at the exact same point).

I was thinking it could be the RAM.  So I swapped to a different slot, and had the same problems.  This doesn't rule out the RAM module itself being defective, but it is brand new and (supposedly) tested before it left the computer shop.  The BIOS is seeing 512MB like it is supposed to.

I guess at this point, I have a very basic and possibly stupid question.  Can these newfangled 64 bit systems run 32 bit software?  Are they backwards compatible?  Or am I being an idiot for not using 64 bit software?  Would going to a SATA HDD help?  I'm on a budget so I kept my old drives, but for about $150 or less I can get a HUGE SATA drive.  So that's a possibility but I'd rather save that for later if I could.

Any help would be appreciated.


-James

---

### Post by jcsewell on 2007-02-02
Here's the "traceback" from the latest installer crash:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 166, in ?
    main()
  File "/usr/bin/ubiquity", line 161, in main
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 57, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 628, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1404, in ?
    install.run()
  File "/usr/share/ubiquity/install.py", line 335, in run
    self.configure_user()
  File "/usr/share/ubiquity/install.py", line 897, in configure_user
    raise InstallStepError("UserSetupApply failed with code %d" % ret)
InstallStepError: UserSetupApply failed with code 139

---

### Post by jcsewell on 2007-02-03
Since my last post, I have verified the CD using the built in verifier at the live CD boot screen.  It's fine.

I also ran memtest from the live CD.  I had one address fail one pattern.  Not sure if that means the RAM is bad or if that was just a fluke.

Right now I'm downloading the AMD64 desktop ISO.  I'll post again and let you know if that helped.


-James

---

### Post by jcsewell on 2007-02-03
Well, the AMD64 CD did no better.  This time it crashed while installing GRUB.

Here's the traceback:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 166, in ?
    main()
  File "/usr/bin/ubiquity", line 161, in main
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 57, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 628, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1404, in ?
    install.run()
  File "/usr/share/ubiquity/install.py", line 385, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1163, in configure_bootloader
    raise InstallStepError(
InstallStepError: GrubInstaller failed with code 1

So at this point I'm stumped.  Is it bad hardware?  Bad CPU or RAM?  Anybody seen this before?

Again, any help would be appreciated...


-James

---

