---
title: "Upgrading to 8.04 from 7.10 did not complete - unable to update"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Aloir on 2008-05-06
Hello

I have just upgraded from 7.10 to 8.04 via the update manager.

All went well until the end of the install when the process did not seem to finish correctly. All the installation of packages was completed, then I got a message saying there was a problem upgrading VirtualBox, which could be resolved later.

I closed the error box, and the update window then closed without 'Cleaning Up' or prompting me to restart.

So I restarted as there was nothing else I could do, and Ubuntu booted up ok.

However, I am unable to update, as I get this error message in both the Update Manager and Terminal (after sudo apt-get update):


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


I tried running dpkg --configure -a as suggested, but got this:

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

Can anyone out there help me out on this issue, or will I have to do a fresh install?

Also, at the Grub boot-up the old kernel is still there as a choice. I presume this should have been removed after the upgrade?

Thanks for any advice.

---

### Post by xardas on 2008-05-08
Man, I'm kind of stuck with the same problem. My package manager is not working either. No body seems to know what to do here about it.

---

### Post by briandu on 2008-05-08
Your message tells you "no space on device" - i.e. you have run out of disk space and so you now have problems. You need to clear up your disk.

Also more info on your config would help you postings btw - it is different if you have 2 disks or several partitions or dual booting etc. Just a suggestion

---

### Post by st0n3cutt3r on 2008-05-08
I got this same error message upgrading on ubuntu studio on my laptop.  Simple solution: Download an 8.04 CD, and start fresh.

---

### Post by briandu on 2008-05-08
Use the LiveCD - you have a copy right? and examine the hard drive and clear out some space.  mount /dev/hda1 or 2  or....    or /dev/sda1....2....or

---

### Post by st0n3cutt3r on 2008-05-08
I had plenty of spare disk space when I upgraded (at least 30GB), so I know it wasn't a lack of space that was the problem. If you've got a live CD(even for an older version), but don't have your files backed up, stick the live CD in, find some spare disk space (if you can, make a new partition big enough to move your stuff to), back your stuff up, and then start fresh. It will be a lot easier and faster in the long run, and you won't have to worry about waiting for some CLI-handy person to walk by and decide that they care enough to help. Worst case scenario if you don't have somewhere to back your stuff up to, go find yourself an external hard drive or a nice big flash disk, and copy your mission-critical files over to there. Probably shouldn't cost more than about $60, and you'll have somewhere that you can keep important files backed up from then on.

---

