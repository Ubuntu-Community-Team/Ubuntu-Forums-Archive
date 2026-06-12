---
title: "Ubuntu Install: Swap Space Error"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by shigidab0p on 2008-01-05
Hi Everyone!

I'm trying to install Ubuntu 7.10 on my (5 year old) laptop.  I've had it installed previously, but it was playing up.  So I decided to re-install.  Everything went smoothly with the Live CD, except for the actual installing bit.  Using the manual or automatic partitioner, it always comes down to:  "Failed to create a swap space:  The creation of a swap space in partition #whatever of SCSI1 (0,0,0) (sda) failed."

It could very well be that my laptop's hard drive has had it, but I don't want to give up on it just yet!  Thanks for your time and knowledge.

---

### Post by Partyboi2 on 2008-01-05
What happens if you try and create the /swap with gparted before the install?

---

### Post by shigidab0p on 2008-01-05
> **Partyboi2 said:**
> What happens if you try and create the /swap with gparted before the install?
I'm sorry, but I'm not quite Ubuntu savvy enough to do such a thing.  Can you give me a quick guide?  I have a 20 gig hard drive and I don't really care how it's partitioned as long as Ubuntu installs;  I keep most stuff on an external hard drive.

---

### Post by taurus on 2008-01-05
From the LiveCD, run gparted, System -> Administration, and delete all the partitions on your harddrive.  Format it to ext3.  Then, click the install icon on your desktop and tell the installer to use the whole harddrive.  It will create / and swap partitions for you automatically.

---

