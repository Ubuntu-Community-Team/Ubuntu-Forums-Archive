---
title: "How do I reinstall Ubuntu without affecting my data"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by charlescarroll1 on 2012-01-23
I was recently told that uninstalling Gnome Essential Components (gnome-core) that it wouldn't adversely affect how Ubuntu starts. Unfortunately, after I uninstalled "gnome-core", my system restarted and won't load ubuntu. After grub, it just sits at the ubuntu screen and won't actually load up the os. 

[http://ubuntuforums.org/showthread.php?p=11630986#post11630986](http://ubuntuforums.org/showthread.php?p=11630986#post11630986)

Is there a way to reinstall Ubuntu without losing any of my data? Is it as simple as popping in an install disc?

---

### Post by carl4926 on 2012-01-23
Unless you use the custom partitioner and manually setup a separate /home
Not really.

If you have a external HD you could backup your /home/username* to it
Or
You could boot a live CD and shrink some space off, create a partition to backup to
Reinstall
Copy your files back
Blah...blah..

I can walk you through it, but I'm kind of busy today

---

### Post by charlescarroll1 on 2012-01-23
I've already put a different HDD in my laptop and put my 750gb (the one with the issue) in an enclosure. I have access to all my data but it's such a pain having to transfer it to a backup and then blah blah blah.

How difficult is it to use the custom partitioner?

---

### Post by carl4926 on 2012-01-23
The custom partitioner is a little more complicated than GParted
But they both essentially do the same thing.
I actually use Parted Magic to partition everything before I install, but you can use GParted from the live cd.
Unfortunately ubuntu still defaults to a single partition for the system and user files.
Most distros make /home separate from / (root)

Try and explain what it is you need to do exactly, are you planning to install Ubuntu to this new bigger HD?
Then copy your user files over?
Will the old HD become a backup?

---

### Post by carl4926 on 2012-01-23
Here I did a video of Partitioning in Parted magic
They are small because it's a VM

Typically swap wil be at least = to your RAM
/ (root) ext4 should be about 20GB
/home ext4 (I put this in logical partition inside the extended space) make it as big as you like

If you have a 750GB HD you might want to make a couple of ext4 logicals inside the extended. One for /home, the other as a STORE

[http://dl.dropbox.com/u/10573557/standard_linux_partitions.mkv](http://dl.dropbox.com/u/10573557/standard_linux_partitions.mkv)

Save the video
It should play in vlc or smplayer etc..

---

### Post by charlescarroll1 on 2012-01-23
> **carl4926 said:**
> Try and explain what it is you need to do exactly, are you planning to install Ubuntu to this new bigger HD?
Then copy your user files over?
Will the old HD become a backup?

The 750gb HDD is what I originally had Ubuntu with Gnome 3 (and Windows 7) installed on. This is the drive that is having the issue (the Ubuntu partition has all my music, movies, etc on it).

I put a 320gb HDD in as a temporary solution and put the 750gb HDD in an enclosure for now so I can access all my files.

I'd like to be able to fix Ubuntu on the 750gb drive to avoid transferring all my data to another drive and then reinstall Ubuntu.

---

### Post by carl4926 on 2012-01-23
Just choose this route
[http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/4_install_custom.jpeg](http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/4_install_custom.jpeg)

And point the installer to your partitions

---

### Post by carl4926 on 2012-01-23
It may be possible to use the live cd, boot to the live desktop
Then use a terminal to chroot to your system
Then use apt to re-install what you deleted

I have to run
There are others than can explain chroot to you

Post this from the live cd

```
sudo fdisk -l
```Tell us which partitions are which

---

