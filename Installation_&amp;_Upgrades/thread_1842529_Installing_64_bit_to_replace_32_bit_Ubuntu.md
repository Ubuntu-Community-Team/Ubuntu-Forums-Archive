---
title: "Installing 64 bit to replace 32 bit Ubuntu"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by Paul0nc on 2011-09-11
If I attempt to install 64 bit Ubuntu when I have the 32 bit version already installed, will I lose my personal data?  That is, will it scrub the disk partition to install the new version?  

I am running on a dual boot machine with Windows 7 installed in a second partition.

Thanks,
Paul.

---

### Post by Paddy Landau on 2011-09-11
If you had originally created a separate partition for your home partition, then you won't lose your data as long as you don't format that partition. (If you don't know what that means, then you have *not* created a separate home partition.)

However, if it's not on a separate partition, you probably will lose all your Ubuntu data.

In any case, I strongly recommend that you **back up all your important data** -- both Windows and Ubuntu. That way, should anything go wrong (e.g. you accidentally choose the wrong option; there is a hard disk crash), you have all your data available.

The easiest way to back up your Ubuntu data is to copy your entire /home directory to a backup drive, whether it be a DVD, USB stick or USB external drive. Backing up Windows is a bit more complicated.

---

### Post by Joebewan on 2011-09-11
32 to 64 bit is not an upgrade.  You'll have to do a clean install.  Back up all your data as mentioned before and choose carefully which partition you install to.

---

### Post by foresthill on 2011-09-11
Agree with previous posters. 

I have been running 64 bit 10.10 for the past few days and have been pleasantly surprised by the complete lack of any bugs whatsoever, compared to running 32 bit 10.10.

The last 64 bit OS I tried running a few years ago (Open Suse) was an absolute nightmare filled with programs and features that didn't work quite right. Evidently, 64 bit Linux is finally ready for prime time.

---

### Post by IWantFroyo on 2011-09-11
You will lose your personal data if you don't have a separate /home partition. If you do have one, then you'll still have to manually tell it not to format, and to mount as /home.

Edit- I am talking about what you do while reinstalling. You can't simply upgrade to 64 bit. You have to do a clean install.

---

