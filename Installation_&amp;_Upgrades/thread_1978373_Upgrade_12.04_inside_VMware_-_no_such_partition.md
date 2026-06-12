---
title: "Upgrade 12.04 inside VMware - no such partition"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by fboecom on 2012-05-11
[FONT="Arial"]Having a nicely running Ubuntu 11 inside VMWare workstation (on W7), I was invited to upgrade to 12.04. The upgrade went smooth but the reboot brought me 3 times 'error:no such partition' - I can't boot from GRUB. Not the most recent top row, nor any of the older installations. 
In the VM had 1 VMWare logical disk (root) and 2 more physcial partitions mounted into this Ubuntu VM.

I dont mind trashing this VM and rebuild a 12.04 - but it is kinda weird this happened.[/FONT]

---

### Post by tormod on 2012-05-12
Same story by a Kubuntu user: [http://www.kubuntuforums.net/showthread.php?58774-upgrade-to-12-04-from-11-10-results-in-grub-saying-quot-no-such-partition-quot](http://www.kubuntuforums.net/showthread.php?58774-upgrade-to-12-04-from-11-10-results-in-grub-saying-quot-no-such-partition-quot)

And on Xubuntu: [http://forum.ubuntu-fr.org/viewtopic.php?id=903611](http://forum.ubuntu-fr.org/viewtopic.php?id=903611)

I experienced the same on a "real" machine after upgrading from Ubuntu 11.10 to 12.04. In my case it was because I do not install grub on the MBR but use the Windows Boot Manager to choose between Windows 7 and grub on this machine. Which means I copy (with dd) the 512 first bytes of the Linux partition into a file that I copy to the Windows partition and is used by the Windows boot manager. I forgot to update this copy before I rebooted... 

This to say that your problems could be due to a version mismatch between the grub being launched from the hard drive (MBR and first sectors on the virtual machine?) and the modules in /boot/grub on the upgraded system.

Which can be fixed by running grub-install as explained in the links above. grub-install copies the grub primary loader plus a minimal set of modules from /boot/grub to the first sectors of your chosen partition (or to the the MBR and first sectors of the drive, before the first partition, if you choose a drive).

---

### Post by fboecom on 2012-05-16
Thanks for the reply - I really didnt do anything other then accepting the proposed upgrade. I didnt mess up with grub nor did I copy anything. There is very little appetite with me for GRUB editing - I had my share trying to fix the problems with booting from a USB drive installation - it's a real mess - so I have now rebuilt a fresh Ubuntu 12 VM in less than 10 minutes. 
If I was a die hard  I could try upgrading another U11 installation - WITHOUT the attached hard drive partitions, because that is what I suspect being GRUB / upgrade's problem. I suspect that it tries to install or boot from some partition that is not the upgrade root partition but one I had mounted in the VM. Still a bug in my opinion - but not one I find necessry to fix or debug.

---

### Post by fboecom on 2012-05-19
Well I had some spare time to serve the community:) I found a backup of the Ubuntu 11 VMWare, removed the physical partitions 'hard drives' in the VMWare settings and booted it up; launched the update manager and upgraded it to 12 without a problem.
So bug or no bug I dont now - but the upgrade process gets confused by VMWare Hard Disk "Using Partitions".

---

