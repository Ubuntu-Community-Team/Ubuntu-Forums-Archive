---
title: "Error &quot;your installation CD-rom couldn't be mounted&quot;"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by andyni on 2007-11-10
Running on a very old laptop - Fujitsu Lifebook S-4510. Piii at 400, 128MB RAM (and that's the max RAM it will support).

trouble is, I'm still a bit of a newbie, so I've stuck to full-blown Ubuntu for a while just so that I can find stuff in the GUI - I find particularly all the system settings difficult to find in anything but Gnome. However, with the upgrade to Gutsy it's slowed to a crawl. Thought I'd try all the luvverly lightweight stuff I'd been reading about.

downloaded fluxbuntu. checked md5. burned to CD. put CD in laptop. boots.
asks about language, keyboard etc, then scans for the CD and fails to mount it.

I thought maybe it was me, so I downloaded ubuntu-7.10-alternate-i386.iso.
checked md5. burned to CD. put CD in laptop. boots. same error, so it's something about Ubuntu (that fluxbuntu is based on) that can't mount the CDROM.

Any ideas? 

Full explanations and blow by blow please, remember I'm still not very conversant with *nix.

---

### Post by kellemes on 2007-11-10
It seems to be related to the following bug, not sure about this though..
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/143958]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/143958")
Maybe you should try the workaround in the bugreport..

---

### Post by andyni on 2007-11-10
A-HA!. Many thanks, looks like this might help me out muchly.

one question. a couple of users on the bug report mention using the busybox to resolve this by manually mounting the CD. how do I access this from the installer screens?

---

### Post by andyni on 2007-11-10
I've discovered how to get into busybox.

tried some of the things in the bug report mentioned above

mount /dev/scd0 /cdrom - this fails. "invalid argument"

TJ's changes to the "list-devices" also doesn't appear to work for me, although I may have got it wrong I suppose,

so, in the top part of the bug report is "Dropping to the BusyBox I find the following devices listed:".

how did you list these devices? what command?

---

### Post by andyni on 2007-11-10
I think I'm going to quit on this one now, looks like there are two related bugs which might be at work here. trying something else....

---

### Post by kellemes on 2007-11-11
> **andyni said:**
> I think I'm going to quit on this one now, looks like there are two related bugs which might be at work here. trying something else....

If you can't fix this problem you may try another distro.. assuming this is a Debian/*buntu specific problem.
If you need the "comfort" and features of Ubuntu and lightweight enough to have it running on your old system you may consider Zenwalk.

---

