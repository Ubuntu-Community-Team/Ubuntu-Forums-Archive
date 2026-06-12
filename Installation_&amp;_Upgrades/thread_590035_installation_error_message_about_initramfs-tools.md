---
title: "installation error message about initramfs-tools"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by harmlesscat on 2007-10-24
I am installing Kubuntu for the first time on my laptop.  I have existing Windows XP and Gentoo Linux installations, and am trying to add Kubuntu 7.10.

----------------------------------------------------------------------------

For background, here is what I have done so far in the installation, including what may be a non-standard partition setup:

I already have partitions available for the installation.  Without giving a complete partition list, for Kubuntu I have /dev/hda7 to mount as / (with 5 GB free), /dev/hda9 to mount as /home (with 8 GB free), and /dev/hda4 to mount as /boot.  The former partitions are type ext3 and /boot is ext2.  Oh, and I have a swap partition.  I assume that Gentoo and Kubuntu can use the same swap partition since only one OS will be running at a time, but otherwise my other OS's are on other partitions not mentioned herein.

I first tried to install Kubuntu from the Desktop CD.  I setup my partitions manually, but then encountered a problem in that the Installer wants to reformat these partitions.  I don't mind it reformatting / and /home (since these partitions are currently empty), but I already have GRUB installed on /boot, with a menu entry to boot my Gentoo installation.  I was hoping the Installer would be smart enough see that I already have GRUB installed and just write in a new menu entry to boot Kubuntu.  If it wiped out my menu file I have it saved off, but I would prefer that it doesn't reformat the whole /boot partition.  So I aborted the installation at this point and moved to the Alternate CD.

On the Alternate CD, I setup the same partitions as outlined above, and it was okay.  The only partition it wanted to automatically reformat was the swap partition.  I did encounter this warning:

"File system doesn't have expected sizes for Windows to like it.  Cluster size is 2k (1k expected); number of clusters is 20017 (39957 expected); size of FATs is 79 sectors (157 expected)."

The error message doesn't actually say which partition it is talking about, but I assume it was talking about the swap partition since that was the only one the Installer was reformatting.  In any case, I ignored the error; the installer completed its reformatting of swap and moved on.

----------------------------------------------------------------------------

I don't know if any of the above is related to the final error I get, but I mention it all for completeness.

The (Alternate) Installer gets to the point of setting up the base system, and midway through, aborts with this error:


"An error was returned while trying to install the initramfs-tools package onto the target system.  Check /var/log/syslog or see virtual console 4 for the details."


I booted back into Gentoo, manually mounted the partition that Kubuntu was mounting as /, and saw that it got as far as creating a /var/log directory, but the syslog file there is completely empty.  I don't know what "virtual console 4" is.  So at this point I'm clueless as to what the problem is with my installation.

Any suggestions?

---

