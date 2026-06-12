---
title: "problems with apt-get upgrade"
date: 2016-04-17
forum: Installation &amp; Upgrades
---

### Post by 2rtmar on 2016-04-17
It tells me to try to run apt-get -f install.  The error says "Unmet dependencies. Try using -f."  When I try "sudo apt-get -f install" I get an error that says


dpkg-deb: error: subprocess paste was killed by signal (Broken Pipe)

Errors were encountered while processing
/var/cache/apt/archives/linux-image-3.16.0-70-generic_3.16.--70.90~14.04.1_i386.deb
/var/cache/apt/archives/linux-image-3.16.0-67-generic_3.16.0-67.87~14.04.1_i.386.deb

E: Sub-process /usr/bin/dpkg returned an error code(1)

---

### Post by oldos2er on 2016-04-17
You could try clearing the cache. ```
sudo apt-get clean; sudo apt-get update; sudo apt-get upgrade
```

---

### Post by 2rtmar on 2016-04-17
I got the same message when i reached apt full-upgrade

---

### Post by oldos2er on 2016-04-17
What version of Ubuntu are you running?

---

### Post by 2rtmar on 2016-04-17
14.04

---

### Post by TheFu on 2016-04-17
Where any .deb files directly installed, not using apt-get or aptitude?  Sometimes those can have specific dependencies that prevent other updates from being possible.

---

### Post by 2rtmar on 2016-04-17
I do not believe so.  I may have done that a while ago, or attempted to do so, but it would've been at least 6 months ago.

---

### Post by TheFu on 2016-04-17
> **2rtmar said:**
> I do not believe so.  I may have done that a while ago, or attempted to do so, but it would've been at least 6 months ago.

It usually isn't an issue immediately, but later, after we forgot we did it .... that's when it bites us.

---

### Post by vasa1 on 2016-04-17
> **oldos2er said:**
> You could try clearing the cache. ```
sudo apt-get clean; sudo apt update; sudo apt full-upgrade
```

> **oldos2er said:**
> What version of Ubuntu are you running?
Some *apt* commands, seen in blogs and elsewhere, may not work in 14.04's version of *apt* unless specified.

I feel it's safer to stay with *apt-get* when trouble-shooting. (And then there are the *aptitude* & *Synaptic* ways too!)

---

### Post by oldos2er on 2016-04-17
Good point vasa1. I'm going to edit my earlier post.

---

### Post by grahammechanical on 2016-04-17
Do you by any chance have a separate /boot partition? I ask because if an update/upgrade includes a kernel upgrade & the partition does not have enough space to take the new kernel, then the new kernel does not get fully installed. From then on any attempt to update/upgrade will trigger another attempt to complete the upgrade to the kernel. Which will keep failing. It acts like a kind of block preventing Update Manager from doing its job.

If that is the problem, then at the Grub boot menu select Advance options for Ubuntu and then load a recovery mode kernel. At the recovery menu select Clean - try to make free space. The Clean option will run two commands clean & autoremove and it is autoremove that will remove at least one no longer required previous kernel. So, you may have to run Clean more than once.

On 16.04 autoremove will remove all previous no longer required kernels except the latest kernel & the first previous kernel. The Resume option will take us out of recovery mode & load to a desktop.

Regards

---

### Post by TheFu on 2016-04-18
Good catch.

/boot being full is a common issue. **df /boot** will show if this is an issue.  The default size of the /boot partition has been ridiculously small for the last few LTS releases.  Not being able to easily control that size during install is also an issue for me.  Just try to do that if you choose to encrypt the entire disk - next to impossible.

---

### Post by vasa1 on 2016-04-18
> **TheFu said:**
> Good catch.

/boot being full is a common issue. **df /boot** will show if this is an issue. ...

That doesn't seem to work for me. Please see this:```
06:38 PM / $ df /boot
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda6      219476804 34740356 173564560  17% /
06:39 PM / $ df /
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda6      219476804 34740692 173564224  17% /
06:40 PM / $ 

```Would this be more informative?```
06:42 PM / $ du -h /boot
2.4M	/boot/grub/i386-pc
2.4M	/boot/grub/fonts
20K	/boot/grub/locale
7.1M	/boot/grub
752K	/boot/extlinux/themes/debian-wheezy
756K	/boot/extlinux/themes
828K	/boot/extlinux
66M	/boot
06:43 PM / $ 
```

---

### Post by TheFu on 2016-04-18
Good thought with du, but this is about a full partition, not how much each directory is using.  Seems the system only has 1 partition, so /boot and / are in the same one - and not full.  That's good news AND bad news.  The bad news is that we don't know the cause if the main issue. 

The good news is that we've eliminated out-of-storage as a possible cause .... Unimportant, but I prefer **df -h** output most of the time. That option was added in the last 5 yrs, sometime.  I also learned that **sort -h** (also added recently) will understand the K/M/G/T suffixes and sort sizes correctly too. ;)

Just to be thorough, what is **df -i** output?  Very unlikely it is out of inodes, but checking is easy.

Also, might be helpful if you posted about 20 lines of the **apt-get upgrade** output, so we can see what's happening around it.  I prefer to use aptitude myself when things get weird. Sometimes aptitude is smarter about resolving issues. They both use the same backend DB and libraries, so there isn't any danger in switching.

---

### Post by TheFu on 2016-04-18
Good thought with du, but this is about a full partition, not how much each directory is using.  Seems the system only has 1 partition, so /boot and / are in the same one - and not full.  That's good news AND bad news.  The bad news is that we don't know the cause if the main issue. 

The good news is that we've eliminated out-of-storage as a possible cause .... Unimportant, but I prefer **df -h** output most of the time. That option was added in the last 5 yrs, sometime.  I also learned that **sort -h** (also added recently) will understand the K/M/G/T suffixes and sort sizes correctly too. ;)

Just to be thorough, what is **df -i** output?  Very unlikely it is out of inodes, but checking is easy.

Also, might be helpful if you posted about 20 lines of the **apt-get upgrade** output, so we can see what's happening around it.  I prefer to use aptitude myself when things get weird. Sometimes aptitude is smarter about resolving issues. They both use the same backend DB and libraries, so there isn't any danger in switching.

Just read that **sudo apt-get check** and **sudo dpkg -C** might help too. The dpkg cmd found some issues on 2 of my systems.

---

### Post by ian-weisser on 2016-04-18
The complete output of apt-get -f install would be more helpful than the synopsis presented so far.
dpkg usually outputs exactly what the problem is.

---

