---
title: "Split Ubuntu 11.04 from 2T to SSD and 3T"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by mbogevik on 2012-04-15
I run Ubuntu 11.04 (desk/64) on a 2T HDD as a server with shared folders in my "home" folder.  But things get filled up and a new 3T is ready to use.  I planned to copy the 2T HDD over to the 3T HDD, but that gave me lot of 
problems, long copy time is one thing, but after I was done I got problem 
changing the partition size to 3T, long convert time with error before finished (gparted and others)

So I decided to split Ubuntu and the archive on two disk making things more easy in the future and buy a OCZ 64G SSD.  My question then is, is there any tool that can copy my Ubuntu on the 2T HDD over to the SSD disk without my large share folder ?
I have searched a lot for answer without an exact identical case found so hopefully I am not annoying people with a stupid question asked lots of times before.

---

### Post by oldfred on 2012-04-15
Is 2TB drive MBR? 

Your 3TB drive has to be gpt, and some recommend gpt for SSDs (Arch see link below).

As such I recommend a new install. You can copy settings if need be. There are several threads where users copied, but had to change fstab, grub and several other locations where UUIDs are. With gpt you cannot dd partitions from MBR.

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Are you booting with BIOS or UEFI?

When you say shared folders in /home is /home a separate partition. Are the shared folders separate partitions?

You can move /home to the 3TB drive and do a new install on the SSD mounting the /home on the 3TB drive.

But I like each hard drive to be fully bootable without any other drive and have an operating system on every drive.

So I kept /home with just its hidden settings on my SSD, but have all my data on a rotating drive with links from the data partitions into /home.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by mbogevik on 2012-04-15
My 2TB disk has a boot MBR with Grub and has a single Ubuntu ext4 partition + 5.7G swap, one HDD, one OS in a Gigabyte D525TUD ATOM D525 MINI-ITX system.  Yes, moving the shared archives to the new 3TB disk may do the trick, then Ubuntu will fit into the 64G SSD.

Of course, since the OS now will be on a SSD I originally planned a fresh Ubuntu install to make sure the SSD is set up optimally, but with a lot of programs running that have its configuration "inside" the Ubuntu folders (like teamspeak 2 server) instead of home folder, it may get quite a puzzle to get it all identical.
Also the Bios setting for SATA set to IDE, not AHCI points to a fresh install.

Thanks for sugegstions, with my job waiting tomorrow I will have to sleep on it :)

---

### Post by oldfred on 2012-04-15
The only issue I had changing IDE to AHCI was my XP does not boot. So the promise I had made for several years of not booting XP now is true. (kinda, another computer still dual boots occasionally) :)

You can export a list of install applications but if they do not store data in /home you will have some effort to figure all that out. By keeping your old install still working in the 2TB drive you can always boot back and check settings.

 
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

I do not have a server, just desktop, but have tried to get all data in data partitions not even /home. I have moved some folders like Thunderbird profile, Firefox profile, kmymoney and a few others to data folders in my /mnt/data.

---

### Post by mbogevik on 2012-07-13
Thanks for interesting and important help and inspiration, oldfred.  The 2T limit for MBR explains my problem changing the 3T disk with backup of old 2T setup to MBR.
And as I assume a moderator also contributes to Linux community, thanks for that too.

To any who is interested :
I have used a long time now thinking what to do, how on what level to copy from old system and what Linux version to use.  I finally ended up with a fresh installation of XUbuntu 12.04 64b on the SSD.  As my headless server did not like Unity, and VNC did not update menu's very well (even trying Ubuntu classic), I let Ubuntu 12.04 go.  I then moved /home folders to new 3T HDD following this description [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) as one of your recommendations.

Copy of old data is in progress, but so far it seems that XUbuntu is great as a home server, it is fast with a light GUI and good samba fileshare response.  Only "problem" is that many programs have been replaced with others, like Gedit now is Leafpad, as many suggestions you will find on the web uses Gedit, this was the only issue that got irritating.  Only a problem as a out-of-the-box system since installing Gedit is easy.

So my only other concerns is getting up working the other programs I had on old HDD.  I am leaving Teamspeak server 2 for version 3 (if I get it working), then getting noip2 and hamachi into the system is left.

So far I am very optimistic, it looks really great, and I have a system that will be more easy to update in the future since /home and samba shares are on seperate HDD :cool:

---

### Post by oldfred on 2012-07-14
Glad you got it working. :)

And good luck on the remaining bits, sometimes they are the most difficult.

---

