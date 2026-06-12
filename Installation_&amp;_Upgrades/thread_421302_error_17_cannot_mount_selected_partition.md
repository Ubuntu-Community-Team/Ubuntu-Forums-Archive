---
title: "error 17: cannot mount selected partition"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by nala on 2007-04-24
I am running a dual-boot XP/Ubuntu box. I attempted to upgrade from Edgy to Feisty. I upgraded using the method recommended in the sticky. However, the upgrade did not complete successfully. This was not an issue at the time, because my computer was still functioning normally. I shut it off last night, and when I turned it on this morning I discovered that Ubuntu simply will not boot. XP still works fine, but when I attempt to boot Ubuntu I get the following errors:

apologies for typos, as i am typing this in by hand.

[INDENT]booting 'ubuntu, kernel 2.6.17-11-386'

root (hd0,0)
filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.17-11-386 root=UUID=8776ced9-9f1b-4c14-a692-740c7c670
92d ro quiet splash

error 17: cannot mount selected partition[/INDENT]

I have ntfs-3g installed on this machine, and when I attempted to recover my files from the linux partition via windows I got an error message informing me that the linux partition is not formatted!

Help would be greatly appreciated. Thank you all for your time.

---

### Post by nala on 2007-04-24
If anyone could help or at least point me to a helpful resource that would be awesome.

---

### Post by marx2k on 2007-04-24
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Check that out

Super Grub Rescue Disc

---

