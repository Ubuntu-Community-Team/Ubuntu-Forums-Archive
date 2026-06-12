---
title: "Dual boot with Mandriva"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by tarahmarie on 2010-08-31
Does anyone have any experience installing Mandriva to a dedicated partition, and configuring it for use with Grub2?

---

### Post by tommcd on 2010-08-31
Do you have a separate /home directory?
If you do, then you should choose a different user name when installing Mandriva, so all the hidden config files and folders in your /home directory don't get mixed up between Ubuntu and Mandriva. Since I am always running several distros on my computers, I keep all my personal files on a /data directory to avoid this problem.

Anyway, the easiest option would be to install Mandriva to an empty partition. Then when you get to the part where Mandriva wants to install grub, opt to install grub to Mandriva's root partition. (It has been a while since I booted both Ubuntu and Mandriva. I am not sure if the current version of Mandriva gives you the option of where you want grub installed).  
Then just boot Ubuntu and run:
```
sudo update-grub
```
And it should pick up your Mandriva install and add it to Ubuntu's grub2 menu so you can boot both Mandriva and Ubuntu.

If Mandriva does not give you the option of where you want to install grub, then Mandriva's grub will overwrite Ubuntu's grub on the MBR. In that case it should pick up your Ubuntu install. Then Mandriva's grub will controll booting both OSs.
If you then want to put Ubuntu back in control of the MBR, then just reinstall grub2 from the Ubuntu live CD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by tarahmarie on 2010-08-31
> **tommcd said:**
> Do you have a separate /home directory?
If you do, then you should choose a different user name when installing Mandriva, so all the hidden config files and folders in your /home directory don't get mixed up between Ubuntu and Mandriva. Since I am always running several distros on my computers, I keep all my personal files on a /data directory to avoid this problem.

Anyway, the easiest option would be to install Mandriva to an empty partition. Then when you get to the part where Mandriva wants to install grub, opt to install grub to Mandriva's root partition. (It has been a while since I booted both Ubuntu and Mandriva. I am not sure if the current version of Mandriva gives you the option of where you want grub installed).  
Then just boot Ubuntu and run:
```
sudo update-grub
```
And it should pick up your Mandriva install and add it to Ubuntu's grub2 menu so you can boot both Mandriva and Ubuntu.

If Mandriva does not give you the option of where you want to install grub, then Mandriva's grub will overwrite Ubuntu's grub on the MBR. In that case it should pick up your Ubuntu install. Then Mandriva's grub will controll booting both OSs.
If you then want to put Ubuntu back in control of the MBR, then just reinstall grub2 from the Ubuntu live CD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

(1) With separate /home and /data partitions, is it that the /home partition should be 20GB or so to retain data in the config folders like .kde and .mozilla, and the /data partition is where I store vids, music, docs, etc?

(2) I want to be absolutely sure I don't nuke my bootability; I just went through a whole saga dealing with a new 2TB drive and the loss of the BIOS boot partition. In fact, I almost don't even want to deal with a distro that isn't using grub2, simply because I don't particularly feel like dealing with chainloading (I basically know what chainloading is, but I've never set it up or done it).  Can Mandriva nuke anything if it installs grub legacy to its root partition?

---

### Post by tarahmarie on 2010-09-01
And also: would you all recommend separate /home partitions for each / partition (say, if I was to dual boot Kubuntu and opensuse or whatever)?  Like this:

sda1 / (kubuntu root partition, not mounted at boot by opensuse)
sda2 /home (kubuntu home with .kde etc, not mounted at boot by opensuse)
sda3 / (opensuse root partition, not mounted at boot by kubuntu)
sda4 /home (opensuse home with .enlightenment, etc, not mounted at boot by kubuntu)
sda5 swap
sda6 /data (all my documents and pix and vids and crap, mounted by both OSes)
sdb1 /secondDrive (my ext3 backup drive, mounted by both OSes)

Is this the right way to use my same username with both installs, and hence to not have to deal with permissions issues in my /data and /secondDrive partitions?

---

### Post by tommcd on 2010-09-01
> **tarahmarie said:**
> (1) With separate /home and /data partitions, is it that the /home partition should be 20GB or so to retain data in the config folders like .kde and .mozilla, and the /data partition is where I store vids, music, docs, etc?
I do it like this. I have a separate root partition for each distro that I use. The root partitions on my laptop are 10GB. On my desktop the root partitions are 14GB. You could go with as much as 20GB for each root partition; but I have never needed anywhere near that much space.
 The home directory for each distro lives inside that distro's root partition. The home directory only serves to store all the hidden config files. So it does not need a separate partition.
I then have a /data partition that contains all my data. You must use manual partitioning to set the system up like this.
> **tarahmarie said:**
> 
(2) I want to be absolutely sure I don't nuke my bootability; ... Can Mandriva nuke anything if it installs grub legacy to its root partition?
I am not sure which grub the current version of Mandriva uses. Anyway, according to figure 13 of this tutorial:
[http://howtoforge.com/the-perfect-desktop-mandriva-one-2010.1-spring-with-gnome](http://howtoforge.com/the-perfect-desktop-mandriva-one-2010.1-spring-with-gnome)
If you click the "advanced" button it should allow you to install Mandriva's grub to it's root partition. Then you can just boot Ubuntu and run"*sudo update-grub*" and it should add Mandriva to Ubuntu's boot menu.

---

### Post by tarahmarie on 2010-09-01
> **tommcd said:**
> I do it like this. I have a separate root partition for each distro that I use. The root partitions on my laptop are 10GB. On my desktop the root partitions are 14GB. You could go with as much as 20GB for each root partition; but I have never needed anywhere near that much space.
 The home directory for each distro lives inside that distro's root partition. The home directory only serves to store all the hidden config files. So it does not need a separate partition.
I then have a /data partition that contains all my data. You must use manual partitioning to set the system up like this.

I am not sure which grub the current version of Mandriva uses. Anyway, according to figure 13 of this tutorial:
[http://howtoforge.com/the-perfect-desktop-mandriva-one-2010.1-spring-with-gnome](http://howtoforge.com/the-perfect-desktop-mandriva-one-2010.1-spring-with-gnome)
If you click the "advanced" button it should allow you to install Mandriva's grub to it's root partition. Then you can just boot Ubuntu and run"*sudo update-grub*" and it should add Mandriva to Ubuntu's boot menu.

Ok, then, for now, can I use the 10GB partition that I have free, install Mandriva or whatever to it while letting it put its home directory inside that partition, mounting my usual /home partition in Mandriva as a /data partition, and try it out that way?

---

### Post by tommcd on 2010-09-01
> **tarahmarie said:**
> Ok, then, for now, can I use the 10GB partition that I have free, install Mandriva or whatever to it while letting it put its home directory inside that partition, mounting my usual /home partition in Mandriva as a /data partition, and try it out that way?
That should work as far as I know. Mandriva will look to it's own home directory for config files, so the config files present in Ubuntu's /home partition (mountd as /data in Mandriva) should not be a problem.

You do have Ubuntu's home directory on a  *separate partition*. Is that correct?

---

### Post by tarahmarie on 2010-09-01
> **tommcd said:**
> 
You do have Ubuntu's home directory on a  *separate partition*. Is that correct?

Yes, of course.

I like this option; it means I can try out distros all willy-nilly without upsetting my *buntu ecology.

I'll let you all know how it turns out!  Thanks, tommcd!! ):P):P

---

### Post by tarahmarie on 2010-09-01
Yeah, didn't turn out so good.

I'm starting a new thread to deal with this.

---

### Post by tommcd on 2010-09-01
> **tarahmarie said:**
> Yeah, didn't turn out so good.
I'm starting a new thread to deal with this.
Well, exactly what went wrong??

Please provide a link to your new thread if you need to create one so I can follow it.

---

### Post by tarahmarie on 2010-09-01
[http://ubuntuforums.org/showthread.php?p=9795403#post9795403](http://ubuntuforums.org/showthread.php?p=9795403#post9795403)

Hi, tommcd!  Thanks :popcorn:

---

### Post by confused57 on 2010-09-01
One thing to keep in mind if you decide to install Mandriva is that it uses UID:500, whereas Ubuntu uses UID:1000.  You can do a Google search to see the possible permission problems with this.

---

### Post by tarahmarie on 2010-09-06
For my multiboot solution, see here:

[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

---

