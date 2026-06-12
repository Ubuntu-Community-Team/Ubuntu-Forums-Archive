---
title: "How much for / partition and how much for /home partition? Media stored elsewhere."
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2011-05-09
Tomorrow I will be reinstalling Xubuntu with the intention of continuing to store all media and documents on a separate 'DUMP' partition.

200MB for /boot

1GB for /opt

I think if /home and / were on the same partition 15GB would cover it, but as they are not what I am asking is how much for /home and how much / ?

Please consider that even for things like the .wine dir I will set up a symlink to /media/DUMP/.wine

---

### Post by oldfred on 2011-05-09
I have all my data including Firefox & Thunderbird profiles in /data. My /home is 1GB but 3/4 of that is .wine for Picasa which I have not moved to /data (yet).

My root partition is 25GB with about 7GB used and lots of programs installed. Some recommend only about 25% utilization.

Why separate /boot & /opt?

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by Dáire Fagan on 2011-05-11
> **oldfred said:**
> I have all my data including Firefox & Thunderbird profiles in /data. My /home is 1GB but 3/4 of that is .wine for Picasa which I have not moved to /data (yet).

My root partition is 25GB with about 7GB used and lots of programs installed. Some recommend only about 25% utilization.

Why separate /boot & /opt?

I went with 500mb for /boot, 2GB for /opt, 10GB for /home and 15 gb for /.

I keep boot separate so that when re/installing other operating systems, say WIN XP or WIN 7 which are already there or even when reinstalling Xubuntu / which I will be doing I can hang onto programs I have downloaded without synaptic and possible leave /boot untouched. 

There was a lot of messing around getting Windows XP and Windows 7 running alongside Xubuntu with clear choices on boot from Grub.



> **oldfred said:**
> Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Interesting reading.

---

### Post by malspa on 2011-05-11
It depends on how you're gonna do things, but I've been going with 7 GB for / and 5 GB for /home, with separate data partitions for other stuff.

None of the distros installed here are using as much as 5 GB on the / partition; none are using even 2 GB on /home.

For a couple of distros, I did things differently, using a / partition and a /boot partition. In those cases, I used 10 GB for / and 500 MB for /boot.

---

### Post by oldfred on 2011-05-11
You cannot reuse a /boot and should not share a /boot with other installs as files may overlap. Programs are in your root partition and parts are in different places. If you have high speed internet you can make a list of installed apps and just reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

---

### Post by Dáire Fagan on 2011-05-18
> **oldfred said:**
> You cannot reuse a /boot and should not share a /boot with other installs as files may overlap.


Why is there an option to separate /boot at all then?

> **oldfred said:**
> Programs are in your  root partition and parts are in different places. If you have high speed  internet you can make a list of installed apps and just reinstall.


I am talking about programs I manually install, configure and make etc. If I manually install a program that isn't in the repos into /opt it will stay in /opt.

---

### Post by oldfred on 2011-05-18
In the old days you did install every folder in a separate partition, but that was mostly server configurations used for desktops. Servers may still need a separate /boot and perhaps other separate partitions depending on what is being served. Also RAID & LVM may need a separate /boot. Very old computers that can only boot from the first 137GB may also need a separate /boot. 

But standard desktops really only need / & swap. Most of us suggest a separate /home for most users to separate system from data and allow easier clean reinstalls. More advanced users may move /home back into the / partition and use data partitions or shared NTFS data partitions with windows, but that is not a standard Linux configuration.

---

### Post by malspa on 2011-05-18
Well, I used a separate /boot partition for a couple of distros, but I don't think my reasons for doing so apply to the OP's situation. In short, I needed the /boot directories for two distros to be on ext3 partitions instead of on ext4 with the rest of the directories.

---

### Post by m_duck on 2011-05-18
/boot needs its own partition if you have an encrypted root partition since the bootloader needs access to the kernel/ramdisk for the tools etc to decrypt the root partition. It can also be separated for 'security' reasons, though I forget what those reasons are - i.e. you would typically mount the /boot partition 'ro' unless you are performing a kernel upgrade or suchlike. I think /boot also needs to reside on its own partition if your root partition is of a certain filesystem type as GRUB doesn't (didn't?) have the ability to boot btrfs partitions for example.

Your / size will depend on how many/what size programs you will be running - if you have a minimal system with Openbox, Midori etc you will need far less space than if you are running KDE and Firefox.

As for /home, take into account things like downloads when sizing it if they default to there - you don't want to get 90% through the download of the latest Slackware ISO for example, to find that you have then run out of space!

If you have a current install, you can see the how much space you are using in each of your current 'folders' with the **du** command, e.g.```
du -sh /home
```

---

### Post by malspa on 2011-05-18
> **m_duck said:**
> I think /boot also needs to reside on its own partition if your root partition is of a certain filesystem type as GRUB doesn't (didn't?) have the ability to boot

That was my situation.

---

