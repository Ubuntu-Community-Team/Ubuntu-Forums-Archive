---
title: "Grub failure after install"
date: 2004-11-28
forum: Installation &amp; Upgrades
---

### Post by thread_killer on 2004-11-28
The backstory....I have to use CAD (ADT 2005 to be specific) for work so I have to have a windows partion.  It's the only dang M$ partition on my entire network, I'm not really happy about having it after being Microsoft free for so long, but thems the breaks.  8) 

Anyway, I have a new machine, AMD 64 3700+,  1 GB RAM, 250 GB HD running off of a SIIG Ultra ATA controler card.

I wanted to put a *nix distro on optimized for the x86 64, so I find myself here.  I hate Red Hat, and abandoned them completely somewhere around 6.x, though I had found FC3 had 64 bit support, so I gave it a try....Yep, still don't like Red Hat based distros.  I'm too impatient to build a gentoo box (I did it once and it took me a week!) and that brings me to Ubuntu.

Looks good, I think to myself, and I'm very eager to try it.

So I had already had my  set my HD up as /dev/hde1 NTFS
/dev/VolGroup00 as the FC3 partion.....yeah, I let FC3 do it automatically.  I mean, I figured there was nothing I wouldn't be able to back out of later, right?   :oops: 

Anyway...I boot my Ubuntu cd....everything looks like it's going splendidly on the simple install.  I go to reboot and I get grub error 2....I mean, I get nothing, no splash screen or anything.

Alright, I try the expert install....it didn't detect the presense of any other OS's, but it still saw my NTFS partion at /dev/hde1.  I figured I'd be able to tweak grub.conf at some point in the install, but I couldn't.  No biggie, as long as Ubuntu will boot, I'll edit it later for dual boot.

Nope, still no boot.  I had to put FC3 back on so I could get back into the NTFS partion for work.

Any ideas what I can do differently in the install to get this thing to work?  Is it maybe the ATA card?  Can't find my hard drive?  I confess...I haven't looked up grub error 2 yet, that's what I'm about to do....

Thanks

---

### Post by jmarc on 2004-11-28
This look like the behaviour I reported recently... but I was using a far older
computer.

The current situation is that I've been able to boot using lilo or another version of 
grub (both coming from Debian 3.0), but not the version supplied with Ubuntu.

I've opened a bug report in bugzilla (4157).

Yours,

-- 
Jean-Marc

---

### Post by thread_killer on 2004-11-28
Hmmmm....well I tried gentoo for AMD 64 too and I found something interesting....

It hanges at boot (from the install CD) unless I use the kernel options *noapic nohotplug.*   That is regardless of whether or not apic is enabled or disabled on my motherboard.

I saw somewhere else on these forums that Ubuntu is using hotplug so that may be an issue, is there a way to turn it off at boot?  What about apic?

---

