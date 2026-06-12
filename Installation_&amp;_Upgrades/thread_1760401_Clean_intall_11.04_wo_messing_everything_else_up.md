---
title: "Clean intall 11.04 w/o messing everything else up"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by awildthingy on 2011-05-16
I have followed the instructions at this Lifehacker link to dual-boot Win7 and Ubuntu 10.10:

[]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

I've used it to good effect for a while but all the sudden I cant boot into the Ubuntu side (too rigorous of testing i guess). What is the best way to cleanly install 11.04 over the top of the ubuntu partition w/o messing up the MBR or the windows partition? The reason I ask is because I haven't tried this yet and I don't own another HDD that is big enough to ghost the current one I'm using anymore.

---

### Post by jerrycal on 2011-05-17
> **awildthingy said:**
> I have followed the instructions at this Lifehacker link to dual-boot Win7 and Ubuntu 10.10:

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

I've used it to good effect for a while but all the sudden I cant boot into the Ubuntu side (too rigorous of testing i guess). What is the best way to cleanly install 11.04 over the top of the ubuntu partition w/o messing up the MBR or the windows partition? The reason I ask is because I haven't tried this yet and I don't own another HDD that is big enough to ghost the current one I'm using anymore.


You can remove the Ubuntu partitions, and then you'll have to do "repair installation".
Check these:
[http://www.makeuseof.com/answers/uninstall-ubuntu-gain-access-windows-7-dual-boot-system/](http://www.makeuseof.com/answers/uninstall-ubuntu-gain-access-windows-7-dual-boot-system/)

and:  [http://answers.microsoft.com/en-us/windows/forum/windows_7-system/how-do-you-remove-ubuntu-and-grub/42d3f550-bf5f-459d-94ed-4cbadd7c933c](http://answers.microsoft.com/en-us/windows/forum/windows_7-system/how-do-you-remove-ubuntu-and-grub/42d3f550-bf5f-459d-94ed-4cbadd7c933c)

I dual boot MacBook Pro, and when reinstalling Ubuntu, using gparted I remove Ubuntu partitions except for SWAP, and start from there with new installation. But to be on the safe side, you may wanna use the directions from the sites above.

---

### Post by SS10house on 2011-05-17
just go ahead and delete the ubuntu partitions 

and natty will give you option to install in the unallocated space

---

