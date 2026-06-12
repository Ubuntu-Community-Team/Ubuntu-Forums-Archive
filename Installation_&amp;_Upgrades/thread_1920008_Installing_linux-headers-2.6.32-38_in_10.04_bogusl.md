---
title: "Installing linux-headers-2.6.32-38 in 10.04 bogusly claims disk full!  Totally stuck"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by Blueshell on 2012-02-03
update-manager just blew up on me because it claims it ran out of disk space while trying to install linux-headers-2.6.32-38.  The complaint appears to be totally wrong, but I'm now totally stuck.  Can anyone help?  Is the package perhaps defective?

The machine in question has everything (including /boot) in one partition, which currently has 2.1 GB free.  I verified that I could write all of that by doing "dd if=/dev/zero of=ZERO" and dd reported writing 2.1 GB, and the file was that size.  (I deleted it again, of course.)  Just to be on the safe side, I deleted about 300 meg of other files and also did "apt-get clean"---no change in behavior (except perhaps blowing out at a slightly different place in the directory tree it's trying to create).

Yet I cannot finish updating my packages because both update-manager and synaptic instantly blow up claiming "unable to create `/usr/src/linux-headers-2.6.32-38/arch/arm/mach-ixp23xx/include/mach/uncompress.h.dpkg-new [blah blah]': No space left on device."

I even tried doing "while [ 1 ]; do echo "$(date) $(df / | grep sda)"; sleep .1; done" in another window while the attempted update was running.  Used space went from 79% to 80% for a fraction of a second, right when synaptic blew out.  No way did something write 2.1 GB---it took dd almost 3 minutes to do so (it's a slow disk).  Unless perhaps there's something busted in that rpm that tries to write an enormous sparse file or something---how can I find out?

/usr/src/linux-headers-2.6.32-38-generic exists, but -not- the version without -generic, and the former currently has a zillion broken symlinks pointing to the nongeneric directory, but that never got created.

More to the point, how can I get -out- of this fix?  Right now, synaptic claims that linux-headers-2.6.32-38-generic is broken (probably because it depends on 2.6.32-38, which blew up), and I don't even if the system is safe to reboot!  An initrd was written into /boot and lots of /boot/grub got updated -before- it blew out, and I can't afford to guess wrong on this---this is a server that I cannot get physical access to except in extreme circumstances.

Help?

---

### Post by Blueshell on 2012-02-04
*headdesk*

It suddenly occurred to me to check -inodes-, and sure enough, I only had a few hundred left.  The server would have failed more obviously if it was actually zero, but each time the package installation failed, it backed off and freed what it had tried, so things were never obviously broken.

Root cause is that each linux-headers package uses up almost 20,000 inodes, and for a server that's been up 2-3 years, that means 21 different versions of linux-headers that were not getting automatically cleaned up in any way after being successively installed by update-manager.  Since this is a tiny server with a 10G filesystem, that means 64% of its entire stock of inodes was being eaten just by linux-header copies in /usr/src!

---

