---
title: "Can't install Ubuntu on my new SSD, help..."
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by GrdLock02 on 2010-10-07
I just bought a new OCZ Vertex 2 40GB SSD to use as my primary drive.

At first I tried copying over my linux install onto the new drive, reinstalling grub, but that didn't work. I got all my system files copied just fine, but grub was giving me all kinds of weird issues about not being able to find the drive.

So I decided it would just be easier to reinstall Ubuntu 10.04 x64 from scratch.

The installation goes fine until it finishes the file copying process, around 79%... then it comes to a screeching halt. To finish up the installation it takes a good hour, it hangs on running dpkg, instaling user, and just takes forever. If I wait it out and it finishes, it reboots when the installation is complete, and when I try to boot the installation I get lots of ATA errors, flush cache error mainly.

Once I hard reset the machine when it was hanging at 95%, and actually got the system to boot up into the new installation. It then made me run a partial distribution upgrade to fix the packages. However, when it was installing the packages, just like in the installation, it started going really slow. I mean REALLY slow. Each package would take almost a minute to unpack and install, even the tiny ones.

So to me it seems like whenever the drive was doing simultaneous read/writes, it couldn't handle it. I thought maybe it was an issue with Ubuntu. So I tried Fedora 13, same problem. Tried Ubuntu 10.04 x86, same problem. So I thought it might be the drive, so I dug up a Windows 7 cd. Windows 7 installed just fine, and ran perfectly when it booted up. I tried copying large amounts of data back and forth to see if it had simultaneous read/write issues, but nope, it went very fast, as would be expected.

I was running out of ideas, so I tried downloading the Ubuntu 10.10 x64 RC, hoping that maybe the new .35 kernel would make it work fine. Well, the installation in 10.10 doesn't even see the drive.

I'm at a halt here, and I need to get my computer back up ASAP as I'm falling behind on work. I don't know what to do... I want to think that there's something wrong with the drive itself, but Windows worked just fine on it?? I'm getting close to sending this drive back and ordering a Crucial C300 SSD drive and hoping it works ok, but if I can get this one working that would be preferable as I wouldn't have to wait a few days to get the new one.

Can someone please shed some light on what is going on here?

---

### Post by GrdLock02 on 2010-10-07
No one has any ideas?

---

### Post by dabl on 2010-10-07
I don't know for a fact how to fix it, but I'm burning with curiosity as I have the same Vertex 2 40GB SDD arriving tomorrow, for my netbook.  So I'd like to know what's up with yours.

Here are some things I found -- it looks like you might as well start over with a new partition table, and do the cylinder alignment per this:  [http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226)

I assume that once you have made a new partition table, and a single partition as per that guide, you can then use GParted and shrink the one partition in order to make room for a second and/or third one, if you want.

Other potentially relevant links:

[http://www.ocztechnologyforum.com/wiki/index.php?title=How_to_set_up_Mac_OS_X_on_a_VERTEX](http://www.ocztechnologyforum.com/wiki/index.php?title=How_to_set_up_Mac_OS_X_on_a_VERTEX)  (for the firmware link)

[http://www.ocztechnologyforum.com/wiki/index.php?title=How_to_set_up_Mac_OS_X_on_a_VERTEX](http://www.ocztechnologyforum.com/wiki/index.php?title=How_to_set_up_Mac_OS_X_on_a_VERTEX) (regarding SMART utilization)

---

