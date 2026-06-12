---
title: "Need help relocating /var"
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by aajax on 2016-09-21
I'm trying to do what is described [here]("http://unix.stackexchange.com/questions/131311/moving-var-home-to-separate-partition").  In my case the bind mount approach was chosen.  The reason for doing this is to limit writing to a relatively small SSD drive.

The result is that when attempting to start the system (i.e., select the system to start on the boot menu) a completely blank screen appears directly (i.e., nothing else) and it stays like that.

Something I've considered is that if there are any hard links referencing the content of /var then relocation to another drive/partition/filesystem could be problematic.  However, I don't know how to figure out if there are any such hard links.  Can anyone advise about that?

The referenced article is a couple of years old.  Is it possible that what worked then does not now (i.e., Ubuntu 16.04.1)?  If so why?

Any other ideas?

---

### Post by SeijiSensei on 2016-09-21
First, do you have a dedicated partition devoted to /var?  You're not trying to share it with other mount point like the OP in that thread you cited wanted to do.

I'd follow this route.

1) Create an empty Linux partition with (g)parted or fdisk and format it as ext4.

2) Reboot the machine and select "[Recovery Mode]("https://wiki.ubuntu.com/RecoveryMode")".

3) The root filesystem will be mounted read-only.  You need to fix that before continuing with
```
mount -o remount,rw /
```
(In recovery mode you have root privileges already so you don't need sudo.)

4) Mount the newly-created partition temporarily as /mnt.

5) Copy the contents /var to /mnt like this:
```

cd /var
rsync -av . /mnt

```
/mnt should now contain a complete copy of /var.

6) Move the old /var out of the way for the moment with
```
mv /var /var.old
```

7) Now mount the new partition as /var via an entry in /etc/fstab and reboot.  If everything works normally, you can delete var.old with 
```
sudo rm -rf /var.old
```

---

### Post by aajax on 2016-09-22
Many thanks for the advice.

First, I did not use a dedicated partition but rather the bind mount alternative mentioned in the article.  I also have /tmp relocated to the same partition.  My ultimate intention is to operate several different Ubuntu systems on the same computer via multiboot, which would make a separate partition for each problematic.  I expect to share a single separate partition with /home among each of the multiboot systems.  It (/home) has been relocated to a different partition without any problem.

With that said, I'm now in learn mode and as yet am working on the first of those multiboot systems.  However, I'll be happy to try the dedicated partition to see if that makes a difference.

Also, rather than trying to use the target system, as you say in recovery mode, to perform the updates/revisions I've been booting the computer with the Live CD to make the revisions to the target filesystem.  Is there a problem with that method?

Also, my own idea was to leave the original /var directory with all of its' files in place.  At the stage I am now the space being consumed is negligible.  So far this has served me well in the manner of making it easy to undo the changes and restore the system to a bootable/startable state.  Am I missing something? 

Rather than rsync I used cp with the regress option to copy the operable /var to the new location.  Is there a reason that this is a bad idea?

Lastly, is there reason I can be certain that there are no applicable hard links?

---

### Post by oldfred on 2016-09-22
If wanting multiple installs just create as many 25GB / (root) partitions as you want.
I do that, and currently have 2 installs on sda (SSD) with space for more, and 4 (some obsolete) installs on sdb. But I use a large /mnt/data partition for all my user data which I mount & link into /home so every system has same data, including Firefox & Thunderbird emails which I moved & changed profile.ini to new location.

---

### Post by SeijiSensei on 2016-09-22
As oldfred says, create separate partitions for each OS installation.  I've used a common /home for all of them without incident, despite seeing warnings here against that practice.  Even if you have both GNOME and KDE distros, they use separate hidden directories so an installation of Ubuntu and one of Kubuntu won't interfere with each other.

That said, I'm much more partial to virtualization these days compared to multi-boot scenarios.  I run [VirtualBox]("https://virtualbox.org/") and have a variety of VMs with different flavors of Linux and a Windows VM as well.

There's no difference between booting from the CD versus booting into recovery mode as long as you have the disc handy.  I rarely use physical media these days, so booting into recovery mode works better for me.  (VirtualBox can install directly from an ISO image without a physical medium.)

The same is true of rsync vs "cp -r".  I use rsync for all bulk file transfers because of its speed and flexibility.  But for just migrating a filesystem, either is fine.

I've never seen a hard link in /var.  I very much doubt you have any.  You would only have a hard link in /home if you created it yourself.

I maintain a server in my home office to which all the various devices and VMs in my house can connect. That way I can move files around by copying them first to the server then retrieving them from another location.  It also lets me back up everything that matters (mail, documents, etc.) easily by backing up just one device.  I rarely worry about backing up the OS image itself.  It's usually just as easy to reinstall.

---

### Post by aajax on 2016-09-24
Yes, oldfred, is correct.  I have that much working just fine.  The desire to relocate /var has to do with reducing the number of writes to the SSD.

---

### Post by DuckHook on 2016-09-24
> **aajax said:**
> &#8230;The desire to relocate /var has to do with reducing the number of writes to the SSD.You don't have to relocate /var. The two hardest-hit areas in /var are /var/log and /var/tmp. Simply symlink these two subdirectories to your HDD (being careful not to leave orphaned directories behind), and you are good to go.

In general, it is not a good idea to hive too many subdirectories off from under the partition in which you have installed root. It leads to a brittle OS that fractures with even a minor change in config files or hardware. Modern SSDs and recent kernels both are sufficiently well-designed that you shouldn't worry too much about write-fatigue. Lack of space is a different matter, but can be addressed with the technique stated above.

---

### Post by aajax on 2016-09-24
Even when I mount a dedicated partition on hard drive to /var rather than using the bind mount to a subdirectory for /var I get the same result.

However, I have now discovered something that provides a clue.  After moving the contents of /var to the hard drive I renamed (moved) it and created a new empty directory for /var in the root directory (on the SSD).  After attempting to boot the system, with /var mounted via fstab on the secondary hard drive, I can go back to the /var in the root directory and find that some files have been written into the previously empty directory.  The implication being that the process for starting the system was using the /var in the root directory before the mounts performed by fstab came into effect.  Furthermore, those files were stored in a path named /var/cache/fontconfig.  The term cache suggests that there may have been an intent to later read these files but of course they'd no longer be there after /var were mounted to a different drive.  If this speculation is correct it makes me think that /var cannot be entirely relocated, at least, on this version of Ubuntu, which strikes me as a very serious problem in need of correction.  Furthermore, storage being used for cache is at the top of the list for this kind of relocation.

Is there a solution?  Without one I'll be abandoning Ubuntu and looking to see if other distributions can do this better.  The posts I referenced initially indicate what I want to do has worked, at least at some point in the past, on some Linux distributions.

---

### Post by SeijiSensei on 2016-09-24
I've run Linux systems with /var as a separate partition, and everything gets written there.  I always use CentOS as a server distribution, but I'd be surprised if Ubuntu (or Debian) were different in this regard. On the other hand, I have never done that with a system running under systemd like 16.04, so maybe that matters?

---

### Post by aajax on 2016-09-25
I appreciate the insight.  I don't know enough about Linux to know with any certainty the impact of where /var is located on the amount of data that needs to be written to files contained therein.  Therefore, input like that provided by DuckHook is appreciated.  When we look at the names of sub-directories within /var things like spool, mail, cache in addition to log & tmp conjure up notions of data that needs to written whereas the bulk of the software/programs/settings only need to be read.

What is the possibility that my approach is backward?  In that, would I be better off by performing an initial install onto a conventional HDD and then relocating the stuff that doesn't get written very much (programs etc.) to the SSD?

Whichever technique is thought to be best it seems like some basic knowledge I'm lacking is just what is needed to get the system started.  Maybe this could be limited to just what is needed during startup prior to processing the mounts defined in fstab.  Is the startup process documented someplace?

---

### Post by oldfred on 2016-09-25
While early SSDs may have had write issues, you should not have any issues with any newer SSD.
Even hard drives do not last forever.
       SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb)

I do change some settings to reduce writes like noatime in fstab. But otherwise do not worry.
And I use my own trim script not Ubuntu's.


 Info on trim and ext4 without journal, ext2 does not support TRIM, with newer SSDs relatime a reasonalbe alternative to noatime and works with some apps that need timestamps like mutt
[http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/](http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Not-advised:-by-discard](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Not-advised:-by-discard)
[http://askubuntu.com/questions/18903/how-to-enable-trim#19480](http://askubuntu.com/questions/18903/how-to-enable-trim#19480)

---

### Post by aajax on 2016-09-25
Many thanks to SeijiSensei!  The tip about systemd seems to be the answer.  A little research reveals that systemd does not process fstab sequentially as SysV Init did.  In order to allow for parallel processing that had to go.  Apparently there is now a new option, called x-systemd.requires=dir-name, that must be specified to inform systemd about dependencies that exist between different mount instructions.  Adding such along with the bind option seems to result in solving this problem.

With that said I also discovered that while I correctly stated the result being a blank screen which displays nothing what I failed to recognize is that the system did start but without any graphical support.  CTL+ALT+F1 does provide a console from which the system can be examined and with the above correction to fstab the mounts appear to have functioned correctly.

However, the successful relocation of /var still looks like the prime suspect for what now appears to be a problem getting X Windows to start up correctly.  My prior observation about some files written to /var/cache/fontconfig prior to processing the mount appear to fit with the new discoveries.

Therefore, I think this post should be closed as problem solved and after a bit more investigation I'll consider making a new post to discuss the graphics issue.

---

### Post by aajax on 2016-09-25
This input provided by oldfred is good to know.  Thank you.  See my other reply regarding discoveries about systemd.

---

### Post by DuckHook on 2016-09-25
> **aajax said:**
> ...Apparently there is now a new option, called x-systemd.requires=dir-name, that must be specified to inform systemd about dependencies that exist between different mount instructions...Many thanks, aajax. Most of us are still learning all of the new things in systemd. Speaking only for myself, I've been like a blindfolded man groping around in the dark feeling out an elephant. This has made it especially hard to help others for this 16.04 upgrade, since some of us have not upgraded since 14.04, which was still running upstart.

Like oldfred stated, if you have the space, your best bet may in fact be to leave /var on your / partition and avoid the whole mess. If you do find a solution, please post it. It would be very valuable to those like me who are still learning the nuances of systemd.

---

