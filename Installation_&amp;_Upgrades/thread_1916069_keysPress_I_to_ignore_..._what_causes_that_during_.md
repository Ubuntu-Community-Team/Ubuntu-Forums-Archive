---
title: "keys:Press I to ignore ... what causes that during boot ???"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by WinRiddance on 2012-01-27
Hi. The following problem is not that big of a deal, can live with, but I'm curious to know what causes the error since it prevents me from logging in to the system automatically. Recently I installed a clean 64 bit version of Xubuntu 11.10 but first I removed Mint 11.04 followed be reformatting the same ext4 partition for the new Xubuntu installation. After the installation I created two automount points in mnt & fstab, been doing that for the past couple of years with every clean installation of *buntu, Debian, and Mint..

Well, ever since the installation I receive this message while Xubuntu is booting up:
[COLOR=Indigo]keys: Press I to ignore, S to skip mounting, or M for manual recovery[/COLOR]

See the screen photo too. All three options work as they're supposed to, but I'm trying to figure out **why I have to press I to ignore** in the first place? Without pressing I, that screen will remain there indefinitely which pretty much defeats the purpose of having the auto-login option working. Granted, I do have a couple of other USB drives attached to the system, but they're not auto-mounted so that message shouldn't be caused by them, right? Is there some way to stop that message from coming up, **or to by-pass the I keystroke** altogether?

.

---

### Post by georgemc on 2012-01-27
I am not using Xubuntu, however it looks to me like you have a partition complaining.

I would boot a live CD and run "fsck" on all Linux partitions and let it fix the file systems.

"fsck" can take awhile to complete depending on your partition size, do not interrupt, just let it finish.

Good Luck

George

---

### Post by WinRiddance on 2012-02-04
Thanks georgemc, I managed to figure it out. Okay, the problem had to do specifically with the settings that I placed in the FSTAB file for auto-mounting my 3 external NTFS USB drives.

[COLOR=Navy]**This article here ...**[/COLOR]
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[COLOR=Navy]**More specifically this section of that article ...**[/COLOR]
[https://help.ubuntu.com/community/Fstab#Examples](https://help.ubuntu.com/community/Fstab#Examples)

... Really helped to shed light on what was happening. To test my initial theory (based on the article) that the issue was confined strictly to NTFS related entries, I unplugged those drives and commented out the section for them in the fstab file. Then I rebooted, and voila, the issue was resolved ... no more message for ignore, skip, or manual repair.

My initial fstab entries were based on what I'd learned for auto-mounting partitions from within the **/mnt** folder, partitions with Linux file systems that I didn't want to have showing up on the desktop. I never knew that NTFS drive/partition entries were so different because I had been told a couple of years back that as long as the UUID is correct, that's all that matters. Well, apparently not. So if your NTFS fstab entries look similar to either of these two, then you ought to change them accordingly as per the first two links in this new post.

> UUID=186C6B156C6AED46  /mnt/folderordisklabel  ntfs  group=yourusername,users,umask=000,posix=1,user,owner,uid=yourusername  0  2

UUID=186C6B156C6AED46 /mnt/folderdisklabel  ntfs  defaults   0  2
Again, if you're wanting to auto-mount an NTFS drive or partition, be sure to take a look at those above links for clarification. Once you have the correct entries your startup screen issue with the keys for **I** to ignore, **S** to skip, and so on should disappear. Good luck.

.

---

### Post by ohnonot on 2012-02-05
thanks, that helped!
it also answers the question "how to automount windows/ntfs partitions/drives in xubuntu oneiric?"

---

