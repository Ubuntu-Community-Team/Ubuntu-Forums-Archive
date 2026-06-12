---
title: "Karmic on PanP5"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by laos.lindberg on 2009-10-25
Hey fellow system76ers,

I have a panp5, and was wondering how karmic is doing?  should i do a fresh install to get grub2 and ext4?

thanks

---

### Post by betrunkenaffe on 2009-10-25
If as good as PanP4, thumbs up.

---

### Post by HotShotDJ on 2009-10-26
I'm running it on my PanP5, and Karmic is looking quite good. But there are some problems that I'm having.  I haven't been making any noise about the issues since a) it is not officially released, and b) Karmic is not supported by our friends at System76 yet --

1) Power Management.  Doesn't work quite right -- for some reason, it cannot figure out battery discharge or charge rates, and therefore is unable to calculate time to empty or time to fully charged. This is a major problem with the default configuration because the system doesn't know when battery power is critically low, and it will just shut off when the battery dies.  The work around is to use the gnome configuration editor and uncheck gnome-power-manager -> general -> use time for policy, and then set the following under gnome-power-manager -> thresholds:
[LIST]
[*]percentage_action    5
[*]percentage_critical    6
[*]percentage_low    10
[/LIST]
Under Jaunty, the problem was traced down to ACPI_AC being compiled into the kernel rather than as a module (recompiling as a module fixed this problem in Jaunty -- but caused my system to hang on reboot, which I suspect had something to do with the default scripts used for rebooting. Its a problem I've seen in the past with systems that use NVidia cards, but I didn't spend much time trying to figure it out since Karmic is about to be released).

While recompiling the kernel with ACPI_AC as a module does improve power management on the PanP5 under Karmic, it no longer fixes the battery time calculations.  I suspect the issue is with DeviceKit, which is new to Karmic.

2) Suspend. While it works, there is a major problem after resuming from suspend.  The "ondemand" governor gets locked at the lowest frequency step (800 Mhz with my P8700 cpu).  So far, nothing I do fixes it.  Interestingly, the "userspace", "performance", and "conservative" governors work just fine after resuming from suspend.  Ony "ondemand" is a problem.  Only a reboot fixes the stuck governor, which defeats the purpose of suspending in the first place.

In this case, I have no clue what is going on.  Since I've been playing with compiling custom kernels for Ubuntu, I tried compiling the cpufrequency kernel components as modules with no luck (although I did manage to get a kernel oops out of it which was fun for about 1 second.  LOL)

I was hoping that these issues would be fixed by the final release.  But they persist in Karmic RC, and with only 4 days until the release date, I don't hold much hope for them being fixed in time for the release.  Hopefully, the folks at System76 will have a fix that can be included in the next System76 Driver.

EDIT:  FPrint works at least as well as it did under Jaunty (not that I've EVER gotten it to reliably match my fingerprints, but thats another story).  I downloaded the latest tarballs from fprint and then used the fprint.py script from the system76 driver package as my template.  I did not compile libusb-1.0 as the driver package does.. I simply installed libusb-1.0-0 and libusb-1.0-0-dev from the repositories (note: the fprint software from the repositories doesn't work).

Another difference from the way it is done in fprint.py -- I replaced "sudo make install" with "sudo checkinstall" -- this makes apt aware of the package and makes it removable using Synaptic.  However, Synaptic Package Manager wanted to "upgrade" my compiled version of fprint-demo with the version from the repositories and install the repository version of libfprint0.  To prevent this, and possible future problems, I locked the versions for fprint-demo, libfprint, and pam_fprint.

EDIT 2:  Placing the following file into /etc/apt/preferences.d/ is a more elegant way of dealing with "apt-get dist-upgrade", "apt-get upgrade" and Update Manager.  However, Synaptic Package Manager, for some reason, doesn't seem to be honoring pin files in that directory.  A minor annoyance.```
Package: fprint-demo
Pin: version 0.4-1
Pin-Priority: 1001
```

Also, in the new versions of pam_fprint, enrolling finger prints via fprint-demo doesn't work with pam.  However, running "pam_fprint_enroll" from a terminal works brilliantly!  I'm able to login and sudo with the finger print reader MUCH more reliably than before.```
sudo pam_fprint_enroll --help
```

---

### Post by samalex on 2009-10-26
Hi Everyone,

Thanks for the info... Like many I'm planning on doing a clean install of Karmic on my PanP5 when it's released, so I'm anxious to see what kind of problems (if any) will creep up after it's done.  My only worry was Firefox 3.5 since I had been running 3.0, but an update this weekend under Ubuntu 9.04 pushed out 3.5 and it's working quite well.  

Just curious, for those planning on installing Karmic, are you doing an upgrade or clean install?  I'm planning on installing from scratch just so I don't have any of those orphaned files from 9.04 eating up HD space, plus being this is my first time to run Linux on my primary system in some years I went wild when I got my system -- so it's probably good to refresh it so I can install just the stuff I use.

Also why move up to 9.10 if 9.04 is working for you?  My reasons are mainly to get HDMI audio working and to see how the new improvements speed-up bootup (though the latter isn't really a reason I guess).  

Thanks and take care --

Sam

---

### Post by laos.lindberg on 2009-10-26
Thanks for the responses!
i think i will do a fresh install, i want to see how the new filing system works out and how the new boot loader is working.  I dont do anyhting with the HDMI and the Power managment issues dont bother me.  It's got a good buzz around the internet.

woo!

---

### Post by vgrisham on 2009-10-26
I have 64 bit tower running Karmic. You guys might want to wait a few days until [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536") bug is resolved. Though not debilitating, it's been quite the pain in the rear and it doesn't seem much closer to being solved (though the developers finally moved its status from medium to high on Saturday, and earlier today updated it from triaged to confirmed).

---

