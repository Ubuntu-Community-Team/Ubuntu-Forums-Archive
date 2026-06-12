---
title: "[SOLVED] 2.6.24-18-generic No windows partitions"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by Sale on 2008-06-04
Hi I have just installed the latest kernel upgrade: 2.6.24-18-generic and after this I don't see my windows partitions links on the desktop. They ares shown in the nautilus menu but when I click on one of those, I get the message: "cannot mount volume. you are not privileged to mount the volume 'data'"

Windows partitions are shown in /etc/fstab as they vere before, but now it looks that the root is their owner now.

Another problem is that now I can't mount the windows partitions when I boot the 2.6.24-17-generic kernel as well.

TIA

---

### Post by housam on 2008-06-04
Try to use this [[COLOR="Red"]_guide_[/COLOR]]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-62bb8324b93c2b77797bbd3e45493f08ad90a52c")

---

### Post by Sale on 2008-06-04
I'd mark this topic [SOLVED] but I'm not sure if I should.

After my first post I've restarted the computer and worked in windows. Actually, I reformated the system partition and reinstalled XP on it. When I rebooted to ubuntu, it mounted the two non system partitions and shown the links to them on the desktop (those two partitions are called "data" and "media" -  the system partition was and still is called "system"). Then I tried to mount the "system" by clicking Places -> system. I got prompted for the sudo password and the system partition was mounted as well.

I guess maybe the new kernel reckognizes the windows system partition and prevents non-sudo access to it. This would make sense, but why ubuntu didn't mount any of the windows partitions in the first place?

---

