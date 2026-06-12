---
title: "Ubuntu Server 7.10 installer - brain dead?"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by whit on 2008-02-26
I'm trying to install Ubuntu Server 7.10 on a VIA C7-based system. I got up to the "Select and install software" point, where it froze up at 14% for an hour. So I rebooted, and have been trying to complete the basic installation. I've confirmed that the base system is installed. So I'd like to install LILO and get on with booting into it - leaving the optional software installations to after. But whether I select "Install the LILO boot loader on a hard disk" or "Install the GRUB boot loader ..." the Ubuntu installer goes immediately to the Partition Disks menu. Well, the disks are partitioned. If I select "Finish partitioning and write changes to disk" the damn thing starts trying to write changes to _other_ partitions that have nothing to do with this install. (Didn't have the problem the first time around!) I don't want to do that, because it's claiming its finding problems with a couple of them, and  I've no interest in it "fixing" stuff outside of where I'm trying to install Ubuntu. The partitioning was completed fine the first time around, without this problem. 

This is a very broken installer not to either recognize that or accept my command to install the boot loader and get on with things. I realize that Ubuntu has inherited this fairly brain-dead installer from Debian. But how do I work around it? I'm not wanting to do a GUI install on this box at all - just trying to set up a low-traffic mail server and DNS.

---

### Post by Pumalite on 2008-02-26
Do md5sum on your iso, burn at 4x or less in good quality CD-R media, check for CD integrity before install.

---

### Post by whit on 2008-02-26
I did the built-in test on the CD-R before the installation (i.e. "Check CD for defects"). It passed. So presumably that's not the problem at all. Why would you think it was, considering the problem I've described? (I also ran a long term memory test - it also passed.)

---

### Post by Pumalite on 2008-02-26
Did you do md5sum on the iso?

---

### Post by whit on 2008-02-26
Here's the problem I'm pointing at: The installer is brain dead because it insists on going back to the partitioning, even though the partition for the installation is already there, formatted, and populated. Then it offers no way to tell it to simply accept things as they are without "writing changes to disk" - even when there are no changes to write to disk. Then, on going ahead to "write changes to disk" it tries to write things to disks and partitions that haven't been changed, and aren't assigned any roles in the installation (i.e. aren't "/" or anything below it). 

I did solve it in this case, by yanking all the cabling from the drives it wasn't to be using anyway, and then going through the "write changes to disk" step, and proceeding with reinstallation. This time I didn't choose any extra server packages to install, and it worked fine. However, that doesn't in any way get around the observation that there are serious bugs in the installation routine that Ubuntu Server uses. Forget that it froze up midway my first time through. Maybe the ISO was flawed as you suggest, despite that it passed its own test! That would in no way account for the idiotic behavior of the partitioning part of the installation routine - both that it insisted in going through that when it was already done, and that that routine wants to mess with disk territory that's really outside of its legitimate mission.

There's no way, logically, those fairly serious bugs have anything to do with whether the ISO's checksum may have been off. I didn't check that, but you're saying that the "check disk" option of Ubuntu's main menu doesn't include that test? If not, that's another serious shortcoming.

---

