---
title: "Re-installing Ubuntu on existing dual boot"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by adnafunnyfarm on 2011-08-10
I have an existing vista/ubuntu dual boot and I've crashed Ubuntu and then tried to fix it and buggered it up more. I'm trying to re-install Ubuntu in the same partition it was previously but I'm not sure how it's done.

I've got the install disk booted and I'm at the "prepare partitions" dialog. Just not sure what I'm supposed to do with it...

---

### Post by MG&amp;TL on 2011-08-10
Have you backed up your data?

If so, just choose 'replace Ubuntu XX.XX with Ubuntu XX.XX or manually partition. Hope it helps.

---

### Post by adnafunnyfarm on 2011-08-10
I don't get an option to "replace Ubuntu xx.xxx" and I'm unsure of the commands in the manual partition dialog.

---

### Post by MG&amp;TL on 2011-08-10
Hmm...what options DO you get, how exactly did you muck it up, and what version of Ubuntu are you running? What are you dual-booting with?

If not, see Here for a guide on manually partitioning:

[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/")

Not simple, and may have to google stuff, but hey you're manually partitioning. It's an 'advanced skill'.

If none of the above, last suggestion is does it say 'no OS detected on the system'?

---

### Post by oldfred on 2011-08-10
LInk by MG&TL is pretty good, except I do not agree with the need for a separate /boot for most desktops.

If your existing partitions are the sizes you want, you just choose your existing / (root) as / and format as ext4. If you have swap it will find it automatically and reinstall. If you have a separate /home (recommended) then you have to choose it, but DO NOT FORMAT it.

---

