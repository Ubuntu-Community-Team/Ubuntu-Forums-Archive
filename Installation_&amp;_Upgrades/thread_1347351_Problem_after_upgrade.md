---
title: "Problem after upgrade"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by ckuecker on 2009-12-06
Hello from Beloit,

I am not exactly new to computers, but I've only been using Ubuntu for a few months. So far, it's been working well. I had to replace my old Mandrake 7 machine when it died last summer. I use Linux to run my web server and email, and recently have started work on an embedded Linux application for a customer.

This morning, Ubuntu announced there were upgrades available, so I clicked 'OK" and let the upgrade proceed. When it finished, I was prompted to restart, which I did.

During the restart, the power got interrupted. After the power came back, I restarted the computer. The login screen came up, and I logged in.

A few seconds later, I got an error message box that the session lasted less than 10 seconds. I did a search and found several possible causes and fixes. 

The .xsession-errors file has complaints that the /dev/null file cannot be created. I tried setting permissions on the /etc directory to 777, but no joy.

I was running gnome, as that was the default when I installed Ubuntu. I tried installing kde. Rebooting now gives a kde screen with a login box - when I try to log in, the screen blanks and returns to the login screen again, with no error message. Switching back to gnome brings up the error box as before.

I tried the 'failsafe' session - it puts up the desktop, then puts up two error boxes with no text which go away quickly, then the screen resets. It will loop like that until I switch to a terminal mode.

Anyone have any idea which way I should go next? The email and web servers are working fine yet, but I am not real skilled at doing code development from the command line any more - spoiled by GUIs...

Chuck Kuecker

---

### Post by phillw on 2009-12-06
Hi,

It's possible your xorg.conf file has been corrupted. Whilst this is by no means certain, it may be worth while looking at it. [http://ubuntuforums.org/showthread.php?t=258186](http://ubuntuforums.org/showthread.php?t=258186)  Has how to use your backup xorg.conf file to replace your, possibly, corrupt xorg.conf file.
As it takes a backup - if it makes no difference, or makes things worse - you can always revert back to your current one !

/edit  to re-create /dev/null you can issue 

```
mknod -m 666 /dev/null c 1 3
```
you *may* have to issue ```
sudo !!
``` if it reports back that you don't have permissions

Regards,

Phill.

---

### Post by ckuecker on 2009-12-06
I managed to blow it up further. I tried upgrading to grub2. 

I tried reverting back to legacy grub, but no joy. So, naively, I tried reinstalling Ubuntu, telling the partitioner to set up the new install alongside the old one. It did that.

Now, when it boots, I see grub error 18 - my BIOS cannot see the files on my 275 GB hard drive.

How can I return the system to it's original boot configuration? I've looked into using the live CD to restore legacy grub, but it does not seem to work as it should.

I can see both the new Ubuntu partition and the original, with all my data, in the live CD desktop. So close, yet so far...

---

### Post by darkod on 2009-12-06
> **ckuecker said:**
> I managed to blow it up further. I tried upgrading to grub2. 

I tried reverting back to legacy grub, but no joy. So, naively, I tried reinstalling Ubuntu, telling the partitioner to set up the new install alongside the old one. It did that.

Now, when it boots, I see grub error 18 - my BIOS cannot see the files on my 275 GB hard drive.

How can I return the system to it's original boot configuration? I've looked into using the live CD to restore legacy grub, but it does not seem to work as it should.

I can see both the new Ubuntu partition and the original, with all my data, in the live CD desktop. So close, yet so far...

At this point use the 9.10 cd to boot with Try Ubuntu and copy your data to external hdd. Then install Ubuntu 9.10 on the whole drive, or create specific partitions manually, what ever you like. I think there is too much mess to sort it out now. Unless you really have some important setup settings to save the installation, not just videos/music/docs. Those can be easily copied.
And for the record, 9.10 liveCD can't restore grub legacy, if that's what you were trying to do. It comes with grub2. You have to use 9.04 CD or earlier.

PS. Your BIOS might not be able to boot from after 137GB on the hdd. Have this in mind if installing OS all the back on your hdd. In that case consider 100MB partition at front or similar solution.

---

### Post by ckuecker on 2009-12-06
OK. I tried saving the home and other directories, like my bind setups to a USB stick, then reinstalling 9.04, which is what I started with back when. I let it use the whole disk, which I expect would destroy the old file system.

Now, when it boots, I get grub error 18. I tried reloading twice with the same result.

When I originally loaded Ubuntu from this disk, there was no problem. It's acting like something sticky is left on the disk even though I am reloading the partitions to the Ubuntu defaults for my drive.

In my travels through the forums, I see it's probably a good idea to set up a boot partition so there's room for upgrades - but I am unsure how to do that. The custom partition selection in the Ubuntu install is a bit daunting after all the problems I've had today.

Chuck Kuecker

---

### Post by ckuecker on 2009-12-06
Attempting to repartition the hard drive with /boot, /, swap, /home, and /opt directories, and then I will try again.

Can't receive email until I get back up - and my business website is down!

Chuck Kuecker

---

### Post by darkod on 2009-12-06
> **ckuecker said:**
> OK. I tried saving the home and other directories, like my bind setups to a USB stick, then reinstalling 9.04, which is what I started with back when. I let it use the whole disk, which I expect would destroy the old file system.

Now, when it boots, I get grub error 18. I tried reloading twice with the same result.

When I originally loaded Ubuntu from this disk, there was no problem. It's acting like something sticky is left on the disk even though I am reloading the partitions to the Ubuntu defaults for my drive.

In my travels through the forums, I see it's probably a good idea to set up a boot partition so there's room for upgrades - but I am unsure how to do that. The custom partition selection in the Ubuntu install is a bit daunting after all the problems I've had today.

Chuck Kuecker

Did you check the boot drive order in BIOS? It seems you are having the same error 18 as before. Remember with multiple drives it's not enough to reinstall an OS to one of the drives, you have to check where is BIOS trying to boot from.
But I see you continued with even one more install...

---

### Post by ckuecker on 2009-12-06
Just one drive in the box - 250 gig.

The BIOS boot order is CD-ROM, hard drive, floppy.

Having trouble with GParted - I wanted to format the drive with a dedicated /boot partition at the bottom of the disk space, followed by /, swap, and an extended partition with /home and /opt in it.

The partition app fails on the extended partition, with no useful information in the

---

### Post by darkod on 2009-12-06
Be careful with putting /boot at the back, some BIOSes can't see bootable partition beyong 137GB. Although any newer BIOS should be fine I don't know what the year limit is.
Anyway, you can always start creating partition from the front, plan them in advance and create them starting from the front depending which partition is planned for what.

PS. Also I wouldn't waste time using Gparted in advance. This is not like windows. When you start the installer you still have to reconfirm the mount points and filesystem for every ubuntu partition so it's double the job. Otherwise it considers all existing partition as unavailable space. So unless you really have a taks to do with Gparted, do not create them in advance. Do it in the install process in step 4, manual partitioning.

---

### Post by ckuecker on 2009-12-06
Ah - big-endian / little endian - definitions...

I put /boot first, then /, then the swap, then /home, /opt, and /usr. So far, it looks like it's going to install OK. I did have to resize some of the partitions - the installer wouldn't take any smaller than 20 GB.

94% right now - waiting for it...rebooted..

Now, I've got grub error 15. At least that's a change from error 18.

---

### Post by ckuecker on 2009-12-06
OK. I've got it back. It was all in the partitioning.

Now, to restore my web pages and bind settings...

Chuck Kuecker

---

