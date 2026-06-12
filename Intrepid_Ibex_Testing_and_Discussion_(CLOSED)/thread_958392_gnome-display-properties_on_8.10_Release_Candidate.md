---
title: "gnome-display-properties on 8.10 Release Candidate"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by secdroid on 2008-10-25
The gnome-display-properties application appears to have regressed between the Beta and the Release Candidate.  

In the thread containing post [http://ubuntuforums.org/showpost.php?p=5952231&postcount=8]("http://ubuntuforums.org/showpost.php?p=5952231&postcount=8") I learned that the 8.04 "ALT-F2 gksudo displayconfig-gtk" application had been replaced in 8.10 with "ALT-F2 gksudo gnome-display-properties"  

I was successful in invoking the gnome-display-properties application from the Beta i386 Live CD desktop and reducing the resolution to 1024x768x60Hz, as required by my monitor.

I was _not_ successful in accomplishing the same thing with the RC.  The application was successfully invoked and I changed the parameters as before, but the resolution did _not_ change when I clicked the Apply button.

One other issue was noted when I booted the RC with the F4-Safe Graphics mode.  While the resolution still exceeded the capabilities of my monitor, the gnome-display-properties application frequency selection options only offered "0 Hz".  When I booted  normally (without the F4-Safe Graphics mode), there were several frequency options.  As I recall, they were 75, 70, and 60, but I did not note them.  There was no 0 Hz option.  Note: I did not test this on the Beta.

More -- see [https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")

---

### Post by secdroid on 2008-10-25
I'm starting to feel that Debian's "release when ready" might be a better idea.  While Ubuntu's scheduled releases have many advantages, there can be unfortunate quality effects.

FWIW, 8.10 feels like it is being rushed out much too quickly.  Is this Release Candidate really not still Alpha quality?  Is the number of bugs assigned/unassigned acceptable for an RC?

I reported an apparent regression 10 Oct and it is still unassigned and with "Undecided" importance.  [https://bugs.launchpad.net/ubuntu/+bug/281491]("https://bugs.launchpad.net/ubuntu/+bug/281491")

Will there be an 8.10.1?  

Was 8.04.0 really not just a second Release Candidate and 8.04.1 really the final release?  Not appropriate, _especially for LTS_.

---

### Post by Kow on 2008-10-25
> **secdroid said:**
> I'm starting to feel that Debian's "release when ready" might be a better idea.  While Ubuntu's scheduled releases have many advantages, there can be unfortunate quality effects.

FWIW, 8.10 feels like it is being rushed out much too quickly.  Is this Release Candidate really not still Alpha quality?  Is the number of bugs assigned/unassigned acceptable for an RC?

I reported an apparent regression 10 Oct and it is still unassigned and with "Undecided" importance.  [https://bugs.launchpad.net/ubuntu/+bug/281491]("https://bugs.launchpad.net/ubuntu/+bug/281491")

Will there be an 8.10.1?  

Was 8.04.0 really not just a second Release Candidate and 8.04.1 really the final release?  Not appropriate, _especially for LTS_.

No because it encourages people to slack off. Every Ubuntu release starts with "it was rushed". Same thing happened with hardy and it turned out just fine.

---

### Post by wgrant on 2008-10-25
> **secdroid said:**
> The gnome-display-properties application appears to have regressed between the Beta and the Release Candidate.  

In the thread containing post [http://ubuntuforums.org/showpost.php?p=5952231&postcount=8]("http://ubuntuforums.org/showpost.php?p=5952231&postcount=8") I learned that the 8.04 "ALT-F2 gksudo displayconfig-gtk" application had been replaced in 8.10 with "ALT-F2 gksudo gnome-display-properties"  

I was successful in invoking the gnome-display-properties application from the Beta i386 Live CD desktop and reducing the resolution to 1024x768x60Hz, as required by my monitor.

I was _not_ successful in accomplishing the same thing with the RC.  The application was successfully invoked and I changed the parameters as before, but the resolution did _not_ change when I clicked the Apply button.

One other issue was noted when I booted the RC with the F4-Safe Graphics mode.  While the resolution still exceeded the capabilities of my monitor, the gnome-display-properties application frequency selection options only offered "0 Hz".  When I booted  normally (without the F4-Safe Graphics mode), there were several frequency options.  As I recall, they were 75, 70, and 60, but I did not note them.  There was no 0 Hz option.  Note: I did not test this on the Beta.

More -- see [https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")

You could at least tell us which video card and monitor you have, and which video driver you are using...

---

### Post by secdroid on 2008-10-25
> **wgrant said:**
> You could at least tell us which video card and monitor you have, and which video driver you are using...

OK.  This is old hardware that has been in continuous use with Ubuntu from Dapper through Hardy, as well as many other Linux distros.  Most distros, other than Ubuntu, default to an appropriate/usable resolution.  Ubuntu defaults to a resolution & frequencies that are _much_ too high.

No proprietary drivers in use, per Hardy 8.04.1 System->Administration->Hardware Drivers

Motherboard video disabled in BIOS

Mobo -- ASRock K7VM2 
Chipset -- VIA ProSavageDDR KM266

Video info from Hardy 8.04.1 hwinfo:
  101: udi = '/org/freedesktop/Hal/devices/pci_1002_5046'
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'
  info.subsystem = 'pci'
  pci.vendor = 'ATI Technologies Inc'
  info.parent = '/org/freedesktop/Hal/devices/pci_1106_b091'
  info.vendor = 'ATI Technologies Inc'
  info.product = 'Rage 128 PF/PRO AGP 4x TMDS'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'
  pci.product = 'Rage 128 PF/PRO AGP 4x TMDS'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_5046'
  pci.subsys_vendor = 'ATI Technologies Inc'
  pci.product_id = 20550 (0x5046)
  linux.hotplug_type = 2 (0x2)
  pci.vendor_id = 4098 (0x1002)
  linux.subsystem = 'pci'
  pci.subsys_product_id = 8 (0x8)
  pci.subsys_product = 'Rage Fury Pro/Xpert 2000 Pro'
  pci.subsys_vendor_id = 4098 (0x1002)
  pci.device_class = 3 (0x3)

From Hardy's dmesg:
[   36.816075] agpgart: Detected VIA PM266/KM266 chipset
[   36.830272] agpgart: AGP aperture is 128M @ 0xe0000000
...
[   61.783172] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   61.783221] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   61.783287] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode

From the monitor's sales literature (Ubuntu can't detect):
  Amphion Monitor (CM1772PF)
  Screen size -- 17" CRT
  Maximum resolution -- 1280 x 1024
  Recommended resolution -- 1280 x 1024 
  Horizontal scanning frequency -- 30-72KHz
  Vertical scanning frequency -- 50-135Hz
  Type of input -- Analog 

I usually run 1024x768x60Hz.

Any other info that would help?

---

### Post by secdroid on 2008-10-26
> **Kow said:**
> No because it encourages people to slack off. Every Ubuntu release starts with "it was rushed". Same thing happened with hardy and it turned out just fine.

Well, that's one way of looking at it.  Here's another (emphasis added):
> 
    [QUOTE]Is Ubuntu the easiest version of Linux to set up?

No. Try Mandriva and PCLOS for the easiest - they've still got the jump on Ubuntu for "it just works" with no fiddling. And their Control Center feature is better.

Otherwise I prefer and use Ubuntu. Been using it for three years on three boxes.

Ubuntu /does/ seem to work without fiddling for some people, and no doubt a few will flame here that I'm some sort of Microsoft Shill or whatever, but that's my experience. When I install Mandriva or PCLOS, those just work from GO, and I really wish Ubuntu would have a good look at what they're doing different.

Haven't installed Ibex yet. **I was one of the approx 25% of beta testers who had a wretched time, so filled out the bug reports and am now going to wait a month or two past release before trying the final.**

[http://linux.slashdot.org/comments.pl?sid=1007971&cid=25512727]("http://linux.slashdot.org/comments.pl?sid=1007971&cid=25512727")
[/QUOTE]

Guess I'm like the "approx 25% of beta testers who had a wretched time" and I'm having a worse time with the Release Candidate.  When you can't achieve a usable display resolution and ethernet doesn't work, you can't even begin to help test the Release Candidate!

I used to be a developer and I've been on both sides of the scheduled-release vs. release-when-ready debate.  FWIW, I still don't think 8.10 is really at Beta level of quality, let alone RC level, schedule be damned.  And I say this as someone who has been using and recommending Ubuntu for years.

When your LTS needs a .1 point release, it is hard to argue that the original shipped LTS version was of "acceptable" quality.  When Beta bugs are unfixed until a month or two after release, then maybe the Beta->RC->ship intervals are too rushed.

I really do admire a lot of what the Ubuntu community does, but there are areas that need improvement.  I admire Shuttleworth's willingness to be objective about achievements and areas that need work.

(BTW, the Slashdot thread contains lots of complaints about dual monitor with a consensus that it is better, but nowhere near good enough.)

---

