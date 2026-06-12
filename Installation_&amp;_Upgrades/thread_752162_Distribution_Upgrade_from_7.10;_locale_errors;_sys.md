---
title: "Distribution Upgrade from 7.10; locale errors; system will not boot"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by forestial on 2008-04-11
This has now happened to me twice on two virtual machines.

I was running 7.10 on a virtual machine under VMware Workstation (Windows Vista host, Ubuntu guest).

There was a prompt saying that updates were available.  When I clicked on this it asked me if I wanted to do a 'distribution upgrade'.  I said yes.  The upgrade downloaded several hundred files and started to install them.

Watching the log messages of the upgrade fly by, I kept seeing messages like this:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").


After the upgrade was done (several package would not install) it said the upgrade had failed and it was going to do some sort of rollback (didn't capture this message).  After this was done it prompted me to reboot, which I did.

Now the (virtual) machine will not boot.  When I try, I see a blue DEBIAN startup screen (not the usual orange ubuntu one) and the system seems frozen.  Pressing Alt-F1 shows a console with the word (initramfs) and nothing more.  I can type commands here but most don't work 'ls' says /bin/sh: ls: not found.... 'cat' seems to work but I don't have any files to cat :-(

Is there any recovery from here?

As I mentioned essentially the same thing has happened to both of these virtual machines.   Neither is bootable at this point.

---

