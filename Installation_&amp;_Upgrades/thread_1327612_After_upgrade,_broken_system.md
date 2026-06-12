---
title: "After upgrade, broken system"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by teasum on 2009-11-15
Greetings all,

In short, after upgrading my Acer Aspire One (A110 - 8GB SSD version) from 9.04 (Jaunty) to 9.10 (Karmic) I have an unusable system.  (Note: I have the standard Ubuntu desktop, not the netbook remix.)

The first problem I have has to do with the UUID of the partitions.  It seems as though GRUB has the wrong UUID for the drive and thus cannot boot.  If I boot from GRUB without modification, what I get is a glowing Ubuntu logo, and then nothing--no error message, no shell, no nothing--just a backlit screen.  

If, however, I edit GRUB to replace "root=UUID=xxx" with "root=/dev/sda2" it will start to boot, but then I get an error message stating:
> One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/: waiting for /dev/sda2
/tmp: waiting for (null) 
Press ESC to enter a recovery shell


Sometimes it will pass this error and then boot to the desktop, where I find no icons and nautilus will not open.  Other times, however, it just hangs at that error message.

I have done a little bit of searching, which is how I came to understand the UUID issue, but I still can't figure out how to get this issue resolved. I suspect there is a way to somehow provide the correct UUID to GRUB; however, one method I found online said to use the command "blkid" to find the correct UUID didn't work, as blkid gave only the UUID for the SWAP partition, and not my root partition (/dev/sda2).

Any ideas or help here?  Many thanks in advance.

---

### Post by TheHimself on 2009-11-16
You may find this post useful.

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+messed](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+messed)

Just note that 9.10 uses GRUB 2 but 9.04 and the older use Grub "legacy".

---

### Post by teasum on 2009-11-16
Thanks for the advice, but I'm not sure if GRUB is the problem.  As I said, I can edit the GRUB entry to replace the UUID with /dev/sda2, it boots.  I restored GRUB already from the recovery option, but the result is the same.  I might try to restore GRUB the way you suggest to see if it would help, but since this is a netbook, I don't have an easy way to run Ubuntu live.  Also, that post is from 2005--is that still the preferred way to restore GRUB?

---

### Post by allanmills on 2009-11-17
I am also getting a similar error when trying to boot after a network upgrade to Kubuntu 9.10 (from 9.04) failed to complete.

I was using Kubuntu 9.04 and began a network upgrade to Kubuntu 9.10 (using command line "sudo apt-get dist-upgrade" instead of graphical updater).  All packages downloaded okay and install proceeded okay for a while.  At one point, the install aborted back to the command line for some failed dependencies and it suggested using the -f flag to continue upgrade.  I did that and it churned away for a little while longer and aborted again back to the command line.  

I think it was for failed dependencies again, but I didn't have time to copy before everything just froze up.  I tried to reboot and since then, I get a message similar to the one noted by the OP of this thread.  The suggestion to edit GRUB as instructed in the linked thread yields no change.

As I write, I'm downloading the alternate 9.10 CD to perhaps repair the upgrade.  Failing that, are there any other suggestions short of doing a clean 9.10 install?

Thanks for any help.

---

### Post by allanmills on 2009-11-17
I am happy to report that after posting about having a similar problem as the OP earlier, I booted from the alternative CD, went into rescue mode, had it boot me into my broken system (it was one of the options, and I guess it was some kind of "chroot" equivalent), and I was able to run:

sudo dpkg --configure -a

followed by:

sudo aptitude -f install

which solved the problem I was having.  Don't know if this would work for the OP.

Also, on the Kubuntu-specific forums, I found a lengthy thread on this problem also which might prove helpful:

[http://kubuntuforums.net/forums/index.php?topic=3107563.15](http://kubuntuforums.net/forums/index.php?topic=3107563.15)

Reading that gave me some ideas and was also a learning experience.

---

### Post by teasum on 2009-11-24
I tried the suggestion mentioned above, but no change.  Let me clarify--I did not have a problem with the upgrade process itself; rather, after the upgrade completed without any errors, I now have this problem booting into a normal system,  

The newest 'symptom' is nautilus.  If I boot into the system by changing the GRUB line to find /dev/sda2 (rather than by UUID), it boots, but nautilus won't run.  If I open a terminal and enter 'nautilus', I get a 'bus error'.  If, however, I run sudo nautilus, it opens and manages the desktop.  Any ideas on why this might be?

---

### Post by teasum on 2009-11-27
Normally, I hate bumping, but <bump>.

I really need some advice here.  To summarize: after upgrading from 9.04 to 9.10, I started having problems booting my system from grub.  Changing the defaults in grub's menu.lst file to find disks by /dev instead of by UUID fixed that, but I'm still having trouble mounting disks at boot.  Often it just fails to boot altogether, though when I do manage to get in, I cannot get nautilus to run. Also, my email accounts in evolution are gone.  The wierdest thing is that although I can't run nautilus as user, if I run "sudo nautilus", it comes up.  As of today, the only way I can use my aspire one is to manually edit the grub command line, hope it boots, and then manually run 'sudo nautilus' to see my files.  

I have seen other threads on problems with the SSD, and other threads on the install/upgrade process not identifying drives by UUID correctly.  Honestly, I can't figure this out on my own.  

Help??

---

### Post by presence1960 on 2009-11-28
I am not experienced at troubleshooting dist upgrades gone awry- because I never do a dist upgrade opting for clean installs instead. But if you can share more about your setup & boot process we may be able to help you.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

