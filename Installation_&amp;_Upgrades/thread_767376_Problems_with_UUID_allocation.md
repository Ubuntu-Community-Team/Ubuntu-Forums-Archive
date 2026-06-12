---
title: "Problems with UUID allocation"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by meanburrito920 on 2008-04-25
Has anyone besides myself noticed problems with resolving UUIDs between installs of multiple distros (on seperate partitions)? I have experimented with multiple distros and have noticed that upon install the distro reallocates a new UUID to the partition it is installed upon, which causes fsck errors on the other distros when they boot up (because the old UUID won't resolve). I am thinking of just writing a script that will patch it up every time I install another distro, but it is a serious annoyance, and takes up a bit of time to fix. Are there any plans to fix this? I know I could probably resolve the issue by creating a seperate /boot partition, but the problem there is the fact that I cant have more than 4 partitions per disk, which would be /boot, /home, /, and swap. If I formatted the disk to have more I would get my data wiped, and I dont have an extra disk to back it up to (my regular backup disk is for my main computer).

---

### Post by kidders on 2008-04-26
Hi there,

> **meanburrito920 said:**
> Are there any plans to fix this?There isn't really anything to fix. Most operating systems like to format the filesystems they install onto, as a matter of good practice, which changes their UUIDs by design ( ... unless of course you manually defeat the UUID mechanism yourself). I'm assuming that's the cause of your problem.

The use of UUIDs in /etc/fstab and other places is *designed* to work the way you've described. Essentially, when a filesystem's UUID changes, its purpose is deemed to have changed. Consider, for instance, what might happen if you installed Fedora into a filesystem being mounted to /tmp by Ubuntu.

Anyhow, if you'd rather your Linux distros didn't work this way, don't reference filesystems by UUID. There's a variety of alternatives (eg filesystem label, bus path, etc.) that work well in many situations, but perhaps the most straightforward thing to do might be to refer to them by /dev node name. My computer, for instance, used a mixture of UUID-based and /dev path-based naming.

---

### Post by Rumpty on 2008-05-16
I've got this problem after installing the latest Ubuntu on the same drive, different partition, as my existing Ubuntu 7.10. I can't boot 7.10 any more. The error is "fsck can't resolve UUID such and such".

I've used Linux in various forms for a few years, but I'm a bit lost sorting this one out. Appreciate some help here please.

---

### Post by Rumpty on 2008-05-17
Ok, sorted it out by changing the UUID entries in fstab to the good old hdax etc etc, where necessary.

---

### Post by scradock on 2008-05-17
The way I use is to "sudo blkid" to get the UUID values, then Copy and Paste into /etc/fstab and /boot/grub/menu.lst in gedit......

I just cloned a partition, to get a fresh Hardy install to upgrade to Intrepid; the partimage backup worked fine, but the new partition had the same UUID as the original, which would probably have caused some real problems if I hadn't noticed it before trying to reboot.

I used > tune2fs -U random /dev/hda4 to reset the UUID to a random value, before copying it into all the fstabs and menu.lst.....

---

### Post by vanadium on 2008-05-17
You might consider redesigning your multi-boot systems. There is no big point in automatically loading every single partition in every system you boot. A much more sound approach would probably be to create one data partition to store user data you want to make accessible to every system you boot. All the other partitions should not be mounted, and if you ever need, you still can manually.

---

