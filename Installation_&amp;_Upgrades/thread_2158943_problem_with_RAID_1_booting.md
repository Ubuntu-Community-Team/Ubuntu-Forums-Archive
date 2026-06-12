---
title: "problem with RAID 1 booting"
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by jefkebazaar on 2013-07-01
Hi there,     I have been experimenting with a software RAID 1 installation of ubuntu 12.04 LTS in virtualbox, but am having some issues here.  What I basically did: 2 disks in RAID 1. Both disks contain a mirrored partition that has /boot and a mirrored partition that contains an encrypted LVM. All this so far so good, it boots perfectly after install.  When I decide then to try to remove one of both disks in virtualbox, it just says "looking for encrypted source" (or something along those lines, can't remember exactly). After several more minutes, it drops to an initramfs console, where I am stuck...  And yes, I choose the option boot in degraded mode during install, I also checked in the initramfstools/conf.d, it states bootdegraded=true.  What am I doing wrong here? I thought a raid 1 was supposed to boot perfectly even if one disk completely disappears?  Thanks for any help you can provide!

---

### Post by jefkebazaar on 2013-07-01
Nobody any advice on this?

Even tried this one: [http://ubuntuforums.org/showthread.php?t=1864216](http://ubuntuforums.org/showthread.php?t=1864216)

Absolutely no success...

Still says waiting for encrypted source device... 
and then it drops me in an initramfs shell.

I tried the same thing with debian 7 in a virtualbox, and that just works out of the box. Remove one disk, stuff boots perfectly.

I thought Ubuntu was trying to position itself as THE enterprise alternative to redhat? Then I would guess at least that something as important as a raid 1 config would work out of the box...

---

### Post by jefkebazaar on 2013-07-01
I see a lot of people here have read this, nobody any hint on where to look to solve this problem?

---

### Post by ronparent on 2013-07-01
You have failed to state what type of raid - ie software raid or fakeraid. Each can have their own problems.

My own experience of the boot dropping to an initramfs prompt was when the dmraid program (for initiating a fakeraid) wasn't installed when Ubuntu 12.04 was installed. The work around was for me to chroot install dmraid to complete that install. Everything worked fine after that. You could have the same problem with either mdadm or the encrypted LVM. But they have their own workarounds. A better statement of your problem might get darkrod or oldfred to respond.

---

### Post by jefkebazaar on 2013-07-02
It's actually software raid, no fakeraid aka bios raid.
So I'm using the software raid 1 capability of ubuntu (through the install, configure manual disk layout, create raid partitions and devices, ...).

---

### Post by jefkebazaar on 2013-07-02
Nobody else have this issue?
Common people, you're not telling me I'm the only one having this problem :)

---

