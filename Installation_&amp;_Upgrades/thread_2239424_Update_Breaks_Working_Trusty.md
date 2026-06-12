---
title: "Update Breaks Working Trusty"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by r_avital on 2014-08-13
About 1 hour ago, I had a working installation of Ubuntu 14.04 LTS 64Bit.  Skype wasn't connecting, on a hunch, I went to Synaptic and found there was an update available.  Knowing how fincky Skype can be, I decided to mark it for update.  Noticing many, many packages flagged for update, I marked all for update. After update, got notification to restart.  Restarted.  

Message: Your system is in low-res mode, with an OK button.  No cursor on screen, mouse doesn't do anything.
Trying to press tab or Enter, no reaction whatsoever.

THANK YOU UBUNTU for messing up a working system.  And this is LTS, right?

What I've done in that 1 hour since: 
1. Booted into GRUB, tried the "failsafe" -- ended up with same result as above.
2. Booted into GRUB, selected older kernel -- endes up with same result as above.
3. Booted into GRUB, Select oder kerner with "failsafe" -- ended up with same result as above.

Whiskey Tango Fox do I do now????

Able to boot from Kubuntu 14.04 DVD, this is a desktop, not a laptop with uedfi or whatever that's called.

During the update, I saw that the nVidia driver was updated to 331 -- I believe I was on a WORKING 319.

Anything I can do short of re-imaging from an old Clonezilla image?

Thanks.

---

### Post by r_avital on 2014-08-13
Booted from GRUB into recovery. Enabled networking -- which re-mounts the file-systems in read/write mode, then dropped to root prompt.

Issued apt-get purge nvidia*
Rebooted.
System rebooted successfully, ran driver-manager (Kubuntu), which informed me it was using the Nouveau driver.

The options it shows me:
304.117 from nvidia-304
304.117 from nvidia-304-updates
331.38 from nvidia-331 (Recommended driver)
331.38 from nvidia-331-updates
Nouveau

That's it.  Tried all nvidia options, each time obtained the same un-bootable result, each time had to go through the GRUB-Recovery game mentioned above.

My graphics card is a respectable GeForce GT 640 which has never before had any issues with any nvidia driver under ubuntu.

So Congratulations, folks!  Now nvidia drivers are off-limits to ubuntu users.  At least back in Debian I could successfully compile one into the kernel, but I guess that's too much to ask of ubuntu.

This 14.04 LTS is **not** an LTS release.  It doesn't have the stability expected from an LTS release.  This is not even a usable OS.

Oh, P.S. Thanks everybody for your help.

---

### Post by r_avital on 2014-08-20
Ha ha.
Installed Debian. Satisfied all dependencies, and compiled driver downloaded from nVidia. Then, just for grins, compiled another one, in fact, the very one that caused the problem in the first place, in Trusty, when installed from "mark all updates" in Synaptic.  Zero incidents, zero errors, system boots correctly, starts X correctly.

Ubuntu "Trusty" 14.04-64 "LTS":
* Wi-Fi bug regression, can't connect to network, when Saucy could connect perfectly.
* k3b bug, error message when loading a blank dvd.
* Can't orient Unity Greeter with xrandr anymore.
* Implementations such as MATE have buggy panels that hide and never reappear.
* And now, an official, presumably safe, tested update crashes X.

A train wreck. But we're lucky, it's a good thing that so many programming/testing resources were devoted to the task "users will never again see buttons on the right" -- glad that monumental "problem" was solved.

Good.Bye.Ubuntu. It's been real.

---

