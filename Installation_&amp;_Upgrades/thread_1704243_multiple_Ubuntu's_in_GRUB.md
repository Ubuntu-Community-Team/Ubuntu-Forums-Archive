---
title: "multiple Ubuntu's in GRUB"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by bk60544 on 2011-03-10
>>Newbie here. Did a multi-boot with clean install of Win7 and Ubuntu 10.10. At startup GRUB (1.98+20100804-5ubuntu3) presents THREE sets [regular & recovery] of Ubuntu [kernel 2.6.35-27, -25, -22] even though it was only installed once.
>>found a file "Grub.cfg" *somewhere* and when opened, it starts by warning "DO NOT EDIT', but contains references to all three installs.
>>getting HELP in the Forum has been tedius.  Example: entereing "edit GRUB" in the search results in lots of info that is either irrelevant, uses geek-speak, or is beyond the grasp of a newbie.
Thanks.

---

### Post by teward on 2011-03-10
The issue with Ubuntu is that the kernel updates get added to the system and the old ones dont get removed.  For the newbie, they dont expect to see this.  If you keep using the latest kernel (2.6.35-27), you should be fine.  As a somewhat experienced user, i always keep at least 3 kernels available in case something causes the latest one to die.

It's normal to see more than one set of kernels there in GRUB (FYI, the items you see listed in GRUB are indeed the kernels).

However, if you want to purge the list of the older ones, like the -25 and -22 kernels, you can remove their corresponding packages in Synaptic.  Note that since I run an older release of Ubuntu than you I don't know the exact kernel packages you'd need to remove.  You'd have to wait for someone who runs 10.10 to come along.

---

### Post by uRock on 2011-03-10
You should have two listings for each kernel and a memtest option. Old kernels can be removed using Synaptic Package Manager.

Follow the screenshots to remove older kernels. There are three entries per kernel and all three are needed in order to operational.

If you are using Ubuntu 10.04, then you want to keep kernel 2.6.32-29

If you are using Ubuntu 10.10, then you want to keep kernel 2.6.35-27

**Make sure you have all three entries for the one kernel or your system may become unusable.**

---

### Post by bk60544 on 2011-03-10
thanks to Evil & U Rock.  I was able to "read between your lines" and removed the annoyance.  On to the next challenge.

---

### Post by bk60544 on 2011-03-10
how do I mark/label that my question/problem was SOLVED.

---

### Post by Zimmer on 2011-03-10
> **bk60544 said:**
> how do I mark/label that my question/problem was SOLVED.

See the Thread Tools drop down list....

---

### Post by bk60544 on 2011-03-10
thanks, Zimmer!

---

