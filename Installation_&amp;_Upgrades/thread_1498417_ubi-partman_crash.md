---
title: "ubi-partman crash"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by ibates on 2010-05-31
I have been struggling with Ubuntu 9.10 for some months now with an unpredictable (but very regular) hang.  Despite many posts on this forum and elsewhere, no effective hints as to what the problem may have been were found.

So it was decided to do a fresh install - but as 10.04 was in the wind, it was further decided to wait for its release and do the new install then.

After eventually updating 9.1 to the "Your system is up-to-date" status, an upgrade was attempted using the alternative CD downloaded from the Ubuntu site (check-sum is good).

Immediately following the keyboard selection page, the following dialogue was presented:

"Ubi-partman crashed.

Ubi-partman failed with exit code 10.  Further information may be found in /var/log/syslog.  Do you want to try running this step again before continuint?  If you do not, your installation may fail entirely or may be broken."

Naturally enouogh, installation was discontinued after that advice.

Then it was decided to attempt an on-line upgrade.

After running for about 3 hours and seemingly going well, the system once again hung.  Now of course, there is no Ubuntu installation whatsoever.

The "smart thing" to do then was to attempt a clean re-install of 9.10.  But alas!  The same "ubi-partman" message.

Re-reading the release notes for 10.04 revealed the non-interactive boot interface.

So installation was again attempted using the now known interactive "advanced" boot options.

Guess what?  Same "ubi-partman" message.

Thank God for Windows or I would really be in deep trouble.

I am using an ASUS P5VD2-X motherboard with standard BIOS and Intel Core Duo processor.  Windows XP is installed on an IDE HDD while Ubuntu was installed on a separate SATA HDD (which is where I want it in future as well).

Is there a solution to this or am I doomed to revert to Windows?

---

### Post by ibates on 2010-06-01
Update to my first call for help above.

I have attempted just about every conceivable and imaginable combination of attempting to re-install 9.10 or to install 10.04.  All attempts have been totally unsuccessful resulting in the same message "ubi-partman crash".

As a last resort, I have reformatted and repartitioned the SATA HDD on which I want to install Ubuntu (as distinct from the IDE HDD on which Windows is still operating (thus this post).  No need for a partitioning manager now is there???

But alas!  Again, the same "ubi-partman crash" dialogue.

The long and the short of it is that I am now really up the creek without a paddle.  I seem to be completely unable to install Ubuntu (any version) at all.

Unless someone can come up with a solution to this mess, my serious attempts over the last year to become a dedicated Ubuntu user look like having been to no avail.  I am now back to having to use Windows again - much to my disgust.  But if I cannot install Ubuntu to a clean newly formatted HDD using the Ubuntu Live CD, I can see no real option.

Any ideas, anyone?

---

### Post by ibates on 2010-06-01
This problem is now solved.

After much careful studying of /var/logs/syslog it was found that the ubi-partman was attempting to define the partition of a couple of Windows based JMicron RAID HDDs.  These of course are irrelevant to the Ubuntu installation but Ubuntu was attempting to incorporate them into the disks inventory.

By changing the F6 Other ... at the initial screen, to nodmraid the problem was overcome.

A real trap for the unwary.

Thanks to anyone who took to puzzling about this one.  Without the knowledge of the Windows RAID HDDs a logical solution would have been very difficult indeed.

---

### Post by pragya on 2010-12-25
How did you find the solution to it???

Please tell me. I did not understood your last comment properly.
I am facing the same problem abd I dont even have windows to save me :(

Thanks,
pragya

---

### Post by ibates on 2010-12-26
I am afraid I might not be able to help you much because in my case, I had several hard disk drives in my computer available to another OS and not intended to be part of the Ubuntu installation.  When the Ubuntu installation was looking for partitions for installing itself, it found partitions on disks which were not available for the Ubuntu installation.  They were RAID array disks.  So, in order for the Ubuntu installation to continue, I had to disable access to the RAID disks at installation.

At the initial screen in the installation process, pressing F6 allowed me to define no RAID disks (nodmraid).  After doing that, Ubuntu simply bypassed those RAID disks and found available partitions, one of which I was able to choose for the installation.

What OS have you been running until now?  Did you have RAID activated in that system.  It would have been done at BIOS level.  Once it is activated, it is "remembered" by the BIOS, and thus if you are not using another OS which requires RAID to be available, it should be deselected both in the BIOS and probably by the "nodmraid" option using F6 as described above.

If that doesn't work, I suggest a new thread detailing your problem for more experienced help.

---

