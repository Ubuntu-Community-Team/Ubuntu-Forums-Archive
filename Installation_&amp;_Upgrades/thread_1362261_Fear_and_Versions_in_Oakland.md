---
title: "Fear and Versions in Oakland"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by saturnine fei on 2009-12-22
A while back I tried upgrading from Hardy to Intrepid and it caused me trouble.  My printer stopped working and could not be fixed and bluetooth was broken and that too was never solved so I reinstalled Hardy and life has been good.  Now I'm beginning to notice the faintest echoes of problems to come.  It seems the latest versions of software are not available to me (gpodder and the recently touted kmymoney) and I suspect it is the falling away of my version of ubuntu to the pit of history.  The question: Dare I "upgrade" to Karmic?  Thoughts and opinions welcome?

---

### Post by starcraft.man on 2009-12-22
If your uncertain, I'd download the Karmic install disk of your choice and then make a second root partition. Install to that separate partition and see if all works. If it does, delete the first. Ideally you'd have a separate /home mountable to both. For partitioning see gparted and use whatever installer. You can partition within the installer if ya like. If you need more detailed instructions reply.

They will both be available from the GRUB menu, should be.

---

### Post by saturnine fei on 2009-12-23
hmmm... something strange happened... my reply did not post...  one more try.

Thank you.  I hadn't thought of that as I've never done a duel install/boot system.  I did (a few weeks back) install a second HD for my home partition.  I suppose I should back-up my root partition.  Time to learn the very basics of clonezilla...

Thank you for the help.

---

### Post by saturnine fei on 2009-12-25
Thanks again, that all worked pretty well.  I had to disconnect my second drive before it would let me install karmic on the same drive as hardy (it insisted on installing karmic on the second drive for side by side boot and then grub failed), and when I did disconnect drive 2 I lost the option to migrate users over to the new installation (I'm guessing because there were then no home directories for them once the home drive was disconnected).

I'm having the same problem I had with intrepid though.  My printer is not supported under karmic and the fix that worked for hardy does not work for karmic.  Sigh... If I can't upgrade to new versions of Ubuntu to get the latest versions of applications how do I justify using Linux?

---

