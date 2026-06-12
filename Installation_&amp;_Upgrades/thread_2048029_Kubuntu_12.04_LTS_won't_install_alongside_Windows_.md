---
title: "Kubuntu 12.04 LTS won't install alongside Windows 7 for dual boot, but Ubuntu 12 will"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by geekymaestro on 2012-08-26
After checking out some distros, I decided that the Kubuntu variant was the one for me.  I've had Ubuntu 12.04 and Linux Mint 13 install alongside my Windows 7 installation (same disk, I shrunk my windows partition by 100GB) without issue.

I downloaded the 64-bit ISO from kubuntu.org, burned it, booted it, and low and behold, it won't recognize that I already have a Windows 7 OS and would like to install along side it for dual booting.

Just to make sure it wasn't a partition problem I fired up my Ubuntu 12.04 disk that I had made and had no issue, the option to install alongside my Windows 7 installation (which WAS detected) was there.
:confused:
At this point I'm wondering if I have to abandon Kubuntu since it just seems doggedly determined to thwart a hopeful user.  I'm not wiping out my Windows 7 install, I still need it.  I'm also afraid to just partition the empty space as EXT4 and SWAP and install Kubuntu, because I have a feeling it won't put GRUB on for me since it can't tell I already have an existing OS.

Can anyone out there shed some light on this or perhaps provide a solution?  Thanks.

---

### Post by SeijiSensei on 2012-08-26
The standard installation CD for Kubuntu is this one:  [http://cdimage.ubuntu.com/kubuntu/releases/12.04.1/release/](http://cdimage.ubuntu.com/kubuntu/releases/12.04.1/release/)

Give that a try.  I've never had a problem with Kubuntu not recognizing the existing Windows partition.  In fact, as far as I know, the installer is identical to the one in vanilla Ubuntu.  If you still have problems, choose the manual disk partitioning option when offered and configure the filesystems yourself.

---

### Post by geekymaestro on 2012-08-26
> **SeijiSensei said:**
> The standard installation CD for Kubuntu is this one:  [http://cdimage.ubuntu.com/kubuntu/releases/12.04.1/release/](http://cdimage.ubuntu.com/kubuntu/releases/12.04.1/release/)

Give that a try.  I've never had a problem with Kubuntu not recognizing the existing Windows partition.  In fact, as far as I know, the installer is identical to the one in vanilla Ubuntu.  If you still have problems, choose the manual disk partitioning option when offered and configure the filesystems yourself.

I'm downloading that image now and will report back with my results.

EDIT:
Still no "Install Alongside Windows" option with that image either.  I'll look for a how to on setting up the proper partitions.  I only hope that GRUB is installed with it, otherwise I'm going to be repairing my MBR.

---

### Post by geekymaestro on 2012-08-26
I'm fairly certain if I try to install Kubuntu from the disk, even if I manually set up the EXT and SWAP partitions, that GRUB2 will not be installed, and I'll end up trying to work around that.

I'm not sure what the problem is between Kubuntu and Ubuntu, but the Ubuntu installer works, the Kubuntu installer does not.  This is highly disappointing.

I suppose I could install Ubuntu and then just add the KDE desktop.  Any advice here guys and gals?

---

### Post by oldfred on 2012-08-26
What partitions did you use. Perhaps you now have all 4 primary used?

Are you using auto install or manual install so you can install Kubuntu over the Ubuntu install? Otherwise it may not be able to add another partition.

Post this:

sudo fdisk -lu

---

### Post by geekymaestro on 2012-08-27
> **oldfred said:**
> What partitions did you use. Perhaps you now have all 4 primary used?

Are you using auto install or manual install so you can install Kubuntu over the Ubuntu install? Otherwise it may not be able to add another partition.

Post this:

sudo fdisk -lu

I actually fixed this before I got a chance to fulfill your request.  Here's the workaround I used to solve the problem.

I grabbed my Ubuntu (64) disk and installed it alongside Windows 7 (which went off without a hitch again).  I used the auto-install to do this. I did not manually change any partitions during install.  The installer partitioned the free space on my drive and set everything in order.

After Ubuntu was up and running I typed the following into the command line and selected kdm as my dm:
```
sudo apt-get install kubuntu-desktop
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove
```

I chose KDE as my desktop and voila, I'm running Kubuntu (64).  I honestly don't know why the Kubuntu installer wouldn't work for me.  It's odd because the Ubuntu installer worked with no issues whatsoever.  I would think that if Windows 7 (64) had already taken up 4 partitions on the drive, then the Ubuntu installer wouldn't have been able to handle it either, but that wasn't the case.

If you'd like I can still run the command and post the results.

---

### Post by oldfred on 2012-08-27
If it is working it should be fine. 

But I also believe the installer are really the same as only the desktop environment is different. Maybe a bug in the way they assembled the packages for different CDs??

---

### Post by geekymaestro on 2012-08-27
> **oldfred said:**
> If it is working it should be fine. 

But I also believe the installer are really the same as only the desktop environment is different. Maybe a bug in the way they assembled the packages for different CDs??

I was thinking something along those lines. It really is odd.  In any case, I'm marking this thread solved.

At least I'll know how to help someone if they run into the same problem from here on out.

---

### Post by jchharvey on 2012-08-31
I discovered that if you Download the wubi installer, and the ISO package that you're trying to install, and place them in the same folder, then run WUBI, It will install successfully for you.

---

### Post by Karlchen on 2012-08-31
> **jchharvey said:**
> I discovered that if you Download the wubi installer, and the ISO package that you're trying to install, and place them in the same folder, then run WUBI, It will install successfully for you.Wubi is not the solution in this case. Wubi is about installing Ubuntu in a virtual filessystem (root.disk) on an NTFS partition. 

The thread starter had got a dedicated disk partition where the installer should have installed Kubuntu to, but seems to have failed to do so.

Karl

---

