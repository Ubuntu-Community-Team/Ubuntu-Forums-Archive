---
title: "Share /home on dual boot system?"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by hsweet on 2010-11-05
I'm getting ready to install Ubuntu Studio along side my regular Ubuntu on some extra space on my hard drive and it seems to make sense to share /home with both Ubuntu systems.  All ext4.   /home is on it's own partition so all I should have to do is point the installer at it and don't format.

Anybody think of a problem this would cause?

thanks

---

### Post by leclerc65 on 2010-11-05
I once dual boot Ubuntu 9.04 and Crunchbang 9.04 , sharing the same Swap and Home partitions.
That works, except that when switching, one or the other going into Checkdisk and I find that very annoying. Never again.

---

### Post by ajgreeny on 2010-11-05
It is safer and just as convenient to keep the two OS homes separate from one another, either within each OS root partition, or even as a separate /home for each, and use another main partition mounted at boot time by both OSs for all the data files.

---

### Post by kansasnoob on 2010-11-05
Sharing /home doesn't work unless you use different usernames and that's a pain in itself.

I multi-boot a lot performing testing and I discussed what I do here:

[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)

It's hardly easy and there are pit-falls.

---

### Post by srs5694 on 2010-11-06
First, I'd like to make sure that an important distinction is clear: The /home directory (or /home partition, if it's a separate partition) is not the same as a user's home directory. User home directories usually reside in /home and are named after the user; so the user hsweet might have a home directory of /home/hsweet. Linux is a multi-user OS, so a single Linux computer can have several home directories, such as /home/hsweet, /home/jjones, /home/pstewart, etc. These all normally reside in the /home directory. (The root user's home directory, /root, is an exception, and it should be noted that this is different from the system's root directory (/).)

That said, a single /home partition shared between distributions works fine. When using OSes that are closely enough related to each other, you can share user home directories, too, but this practice can cause problems if the OSes vary too much, since settings in user programs appropriate for one OS can be inappropriate in another, leading to malfunctioning programs, missing icons, etc. In these cases, the user home directories must differ between distributions. This does *not* mean that the user*names* must differ, as kansasnoob asserts, although the default setup uses a home directory name based on the username, so it requires some knowledge to set up one or more distributions to use a different home directory name than is the default. (It can be done after the fact with usermod or by editing /etc/passwd by hand; or by specifying the correct home directory with the -d option to useradd when creating an account.)

I don't know why leclerc65 had problems with fsck (I assume that's what was meant by "Checkdisk") being forced when rebooting, but it was not because of sharing /home per se. Chances are there was a shutdown problem of some sort with one or both of the distributions, causing an unclean unmount of one or more partitions.

IMHO, it's better to share a /home partition than to not do so and create a separate data partition, as ajgreeny suggests. There are several subtle reasons for this. The first is that /home is where user data traditionally reside, and moving them elsewhere will make it (very slightly) harder for somebody else who's experienced with Linux to offer good advice or take over administration of the computer, should that become necessary. Another issue is that using a separate data partition will become ugly and awkward if/when you start adding accounts; you'll have to figure out how to handle each user's data, and you'll end up having to create many more symbolic links between /home/*username* directories and their equivalents in your data partition. (Note that you might want to create multiple accounts even on a single-user computer so that you can experiment with account settings, create a temporary account to study a problem, etc.) There's also the fact that a separate data partition is basically just re-inventing the wheel, the wheel in this case being /home. That said, a separate data partition does work; I just view it as a needless and ugly complication that feels like a Microsoft-style hack grafted onto Linux with Frankenstein-style scars.

---

