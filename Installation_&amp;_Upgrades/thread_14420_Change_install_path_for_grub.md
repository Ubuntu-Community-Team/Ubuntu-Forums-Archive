---
title: "Change install path for grub"
date: 2005-02-07
forum: Installation &amp; Upgrades
---

### Post by Slainte on 2005-02-07
Is there a way to install GRUB to my hd1 instead of hd0.

When it installs to hd0, my XP isn't picked up in the grub menu, so i want to try it installed to hd1 and then use GAG as my boot manager.  Is there any easy way around this?

I am a linux newbie, but confidant enough to try workarounds if given a HowTo

Also, I'm installing the 64bit version of warty.  I know there is no native 64bit support for the ati cards in warty, but is there any way i can get them of the live hoary disc?
Everything installed fine except getting a message about X server not starting - no gui, so i'm assuming it's to do with my graphic card drivers?

thanks in advance

---

### Post by Xian on 2005-02-07
su to root
# grub

grub> root (hd0,1)
grub> setup (hd0)
grub> quit

* Change the partitions to match your needs. Above are only examples.

Here's a little how-to: [Restore Grub](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by Slainte on 2005-02-08
thanks for that - will give it a go tonight cheers :)

---

