---
title: "Dell mini 9/Ubuntu-9.10"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by KegHead on 2009-08-24
Hi!

Installed 9.10 today. No problems.

It seems to boot up slowly, loads programs slowly and shows ext3 in system monitor.

Anyone?

KegHead

---

### Post by derrick81787 on 2009-08-24
Did you do a fresh install, or did you upgrade?  I did a fresh install on my Dell mini 9 yesterday, actually, and my bootup time seems fine and I have an ext4 partition (as shown in /etc/fstab.  I haven't looked in System Monitor, and I'm at work so can't at the moment).  I used the daily build image, though.

Also, I've had problems with the netbook-launcher crashing.  Have you not had any issues with that?

---

### Post by KegHead on 2009-08-24
Hi!

I did an upgrade.

No other problems.

KegHead

---

### Post by snowpine on 2009-08-24
Hi KegHead, reinstalling with the ext4 filesystem might give you a little bit of a speed boost.

To what are you comparing 9.10? If you are comparing it with the pre-installed Dell Ubuntu 8.04, that version is optimized for the hardware (lpia kernel) so that might account for the difference in speed.

Also, as I'm sure you know, 9.10 Karmic is still in the testing stages and won't be released until October. Bugs/crashes/freezes/slowdowns all come with the territory if you are using a pre-release operating system.

---

### Post by derrick81787 on 2009-08-24
> **KegHead said:**
> Hi!

I did an upgrade.

No other problems.

KegHead

Also, if you had an ext3 filesystem on Ubuntu Jaunty, then you'll have it on Karmic.  I don't think upgrading the OS automatically updates the partition.  If you want to upgrade your partition to ext4, you can get instructions from here:

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

However, messing with the partitions can be dangerous, so be careful.

- Derrick

---

