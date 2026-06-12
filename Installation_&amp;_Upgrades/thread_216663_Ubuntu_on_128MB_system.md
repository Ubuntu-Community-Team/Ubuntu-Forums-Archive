---
title: "Ubuntu on 128MB system?"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by goatflyer on 2006-07-15
I'm going to try to install Ubuntu on an older computer with plenty of diskspace, but only 128MB ram.  It will be a dual boot (Win98).

Has anyone succeeded at this? Or should I stick to a simpler distro like Feather?

I will be using the alternate-i386 iso.  What boot: options should I use?

---

### Post by aysiu on 2006-07-16
Install Xubuntu. I have that installed on my 766 MHz 128 MB RAM computer, and it runs just fine.

The Alternate CD is a good one to use, as the Desktop CD will require too much RAM. If you don't have the Xubuntu Alternate (i.e., you have the Kubuntu or Ubuntu Alternate), do a "server install" and then ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
sudo /etc/init.d/gdm start
``` Otherwise, if you do have the Xubuntu Alternate CD, just do a regular installation.

---

### Post by Herman on 2006-07-16
:D simutaneous post with aysiu. Post deleted,

---

### Post by sabredog on 2006-07-16
Ok

Regarding CPU speed then. I have two options here.

A P3-450 with 384Mb dual boot with either WinXP or 98SE

or

a P2-650 64Mb current (should be able to update to 128Mb)

I want to give my youngest daughter a dual boot PC as she loves Linux games,

For both I would imagine Xubuntu would be appropriate?

What are minimum system requirements?

cheers and thanks

---

### Post by aysiu on 2006-07-16
384 MB of RAM is plenty for Ubuntu or Kubuntu, but it would run like lightning with Xubuntu.

Truthfully, though, you can have all three installed and run whatever you feel like. I do. The total disk space for all three is less than 3.5 GB.

---

### Post by sabredog on 2006-07-16
Might be the way to go then.

Her current PC is the P2 with 64mb running Win98SE but she does like Ubuntu. I would like a dual boot as the educational games she plays are Win98SE specific. But would need to get the RAM up to 128Mb for Xubuntu.

The other path would be to upgrade my 16 year olds PC (P3-450) to a P4 and then pass that down.

Would a P2-650 run Xubuntu?

---

### Post by aysiu on 2006-07-16
I don't really know much about P2s, but I know 128 MB of RAM is sufficient for Xubuntu. What processing speed does it have?

---

### Post by sabredog on 2006-07-16
Just booted it up. It is a P2 400MHz PC with 96Mb

So much for my memory!

---

