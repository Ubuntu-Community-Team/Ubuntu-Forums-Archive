---
title: "create a /home partition"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by borgward on 2013-02-06
How do I create a /home partition on an existing default installation? Ubuntu 10.04

---

### Post by hansdown on 2013-02-06
Hi borgward.

This should help.

[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)

---

### Post by jajodo on 2013-02-06
hansdown's solution is very elegant.  However if you have the home directory backed up already to an external drive reinstalling Ubuntu could be faster / easier.

1.  Use the live disc to partition the hard drive.  OS probably needs 10-15 GIB. I use 4 GIB for my swap and the rest of the drive for /home.
2.  Copy the contents of your /home directory from backup to the new /home partition.
3.  Reinstall Ubuntu and use the GUI to manually select the correct mount points for root, /home, and swap.  All your preferences, settings, and application configuration should be already set for you on first boot.  That is the beauty of a separate home partition.  Do use the same user name and password.

---

### Post by borgward on 2013-02-07
What I want to know is how to create a /home partition on my existing 10.04 default installation.

I do not want to copy contents of home to external drive, wipe the drive, Create new partitions including /home and then move backed up home contents back to /home.

That is indeed a wise thing to do, but not what I want to do. (actually they are backed up for insurance)

Again, How do I create a /home partition on my existing default 10.04 installation?

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by borgward on 2013-02-07
Thanks for answering my question. I will proceed now and see what happens.

---

### Post by Topsiho on 2013-02-07
> **borgward said:**
> Again, How do I create a /home partition on my existing default 10.04 installation?

Ubuntu 10.04 LTS will become obsolete (unsupported) in April ...

Topsiho

---

### Post by grahammechanical on 2013-02-07
Remember, Ubuntu will look for a /home folder as it boots. Ubuntu needs to know that the /home folder is now on a /home partition. That is the importance of editing the /etc/fstab file. Otherwise we boot to a broken Ubuntu.

It happened to me. When I followed instructions in a magazine. I solved it by copying the /home folder to a partition created for that purpose and re-installing and giving my intended /home partition the mount point of /home. With Ubuntu now finding a /home folder I copied the contents of my old /home folder into the /home folder on the new /home partition.

Either way will work. If you intend at some point to use 12.04 you might want to do this when doing a fresh install of 12.04.

Regards.

---

### Post by borgward on 2013-02-07
> **Topsiho said:**
> Ubuntu 10.04 LTS will become obsolete (unsupported) in April ...

Topsiho

Yes, unfortunately I am stuck w/10.04 until Ubuntu comes up w/something better than Unity.

---

### Post by oldfred on 2013-02-07
I went from 10.10 to 12.04 but installed fallback/gnome-panel. While some things have changed or moved location, it was not much more than most updates and otherwise seems pretty close.

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by jajodo on 2013-02-07
> **borgward said:**
> What I want to know is how to create a /home partition on my existing 10.04 default installation.

I do not want to copy contents of home to external drive, wipe the drive, Create new partitions including /home and then move backed up home contents back to /home.

That is indeed a wise thing to do, but not what I want to do. (actually they are backed up for insurance)

Again, How do I create a /home partition on my existing default 10.04 installation?

It is clear what you are asking and the first response (hansdown's) explains exactly what you are looking to do.  However it is not trivial to say the least... hence response #2.

---

