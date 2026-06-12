---
title: "Have Xp/10.04LTS Desktop want Xp/10.04Lts Netbook remix"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by jdougmoore on 2010-06-19
Noobie here, I have a dual boot of Xp with 10.04LTS desktop.  10.04 loaded grub, did the resizing of my HD into multiple partitions.  

In my haste I installed Desktop ver of 10.04. I want to install the 10.04 Netbook Remix onto this laptop.  

How do I do that?  Will running the install process again with Netbook remix do the trick if I tell Netbook to install/use the existing linux partitions on the HD?

I have tried to make Desktop "look" like Netbook Remix, with zero results of downloading various theme switcher, etc, etc. So I guess my only solution is to install the actual product, which probably runs less services and uses less memory.  Laptop is a fijui lifebook with 2gigs ram and Pentium M processor and 10" screen.  Desktop runs great on it, so hope that Netbook will run even better with less services and love how Netbook maximizes the screen.

Please feel free to point me to any link or Faq.

---

### Post by oldfred on 2010-06-19
When ever reinstalling be sure you have backed up anything your want to save. Did you install a lot of programs, if so you can also back up a list. Any special system settings. Copy those from /etc files. Your /home has all your settings and files, but I do not know if any are different for the Netbook remix.

For any reinstall just use manual and choose the partition(s) you want to use, choose / (root) and type of format ext3 or ext4. Be sure you know, I had a lot of partitions on sdc and choose the wrong one, but did not lose any data. It will find swap and use it. If /home is separate partition choose it but do not format it unless you want to erase all data.

---

### Post by jdougmoore on 2010-06-19
> **oldfred said:**
> When ever reinstalling be sure you have backed up anything your want to save. Did you install a lot of programs, if so you can also back up a list. Any special system settings. Copy those from /etc files. Your /home has all your settings and files, but I do not know if any are different for the Netbook remix.

For any reinstall just use manual and choose the partition(s) you want to use, choose / (root) and type of format ext3 or ext4. Be sure you know, I had a lot of partitions on sdc and choose the wrong one, but did not lose any data. It will find swap and use it. If /home is separate partition choose it but do not format it unless you want to erase all data.

Nothing in the old desktop LTS worth saving.  The partitions I have are the ones Desktop created by default during its install. Will this re-install still detect XP and give me a Grub boot menu with XP?

---

