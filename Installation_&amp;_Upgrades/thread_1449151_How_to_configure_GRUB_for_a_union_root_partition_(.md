---
title: "How to configure GRUB for a union root partition (aufs)"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by GeoMX on 2010-04-07
As recommended, I'm creating a new thread for my configuring GRUB problems commented first [here]("http://ubuntuforums.org/showthread.php?t=1443398")

We are setting up a new version of a custom system, we are migrating to Ubuntu Karmic from another distribution (Slackware). Besides small differences between these systems (most of them from the most recent versions of software used by the latest Ubuntu, such as GRUB 2), it has been decided that the new system will run an union root partition using aufs and tempfs, basically, we are following the steps provided here:
[http://www.logicsupply.com/blog/2009/01/27/how-to-build-a-read-only-linux-system/](http://www.logicsupply.com/blog/2009/01/27/how-to-build-a-read-only-linux-system/)
for our setup.

We install the system to a new hard drive from an already running Ubuntu Karmic system, using debootstrap/chroot, we move the disk to another sytem, so we have to correct disk references, we are able to run this system and it behaves correctly the first time it boots, it bypasses the GRUB menu since there are no other systems detected. However, after halting the system and booting it, the GRUB menu appears with a new "recovery" option, we've managed to remove this recovery option using
GRUB_DISABLE_LINUX_RECOVERY=true

But then, the GRUB menu appears again, this time with only one option to boot: our system installation. But when this GRUB menu appears, it has no default timeout and so it stays forever unless ENTER is pressed to boot into the selected entry.

The main problem is that we are unable to configure GRUB inside the new installation because it always returns this message:

grub-probe error cannot find a device for /

If we boot the system "normally" (mounting root to a normal partition), we are able to configure GRUB properly, but it does not behave the same when using the union file system as /.

We are only looking for a way to bypass the GRUB menu and boot our system, do you have any advice on how to properly configure the GRUB menu for our system? 

Any help is appreciated, thank you.

---

### Post by GeoMX on 2010-04-08
I was trying to solve it by running the GRUB 2 associated scripts (I'm new to this GRUB version) but could not solve it.

I managed to do what I wanted by "manually" editing grub.cfg.

---

### Post by Chav on 2010-04-08
Your problem sounds similar to mine and here
[http://ubuntuforums.org/showthread.php?p=9054666](http://ubuntuforums.org/showthread.php?p=9054666) (see post 20)

---

### Post by GeoMX on 2010-04-16
Thanks a lot for your reply, my problem was related to grubenv too :).

---

