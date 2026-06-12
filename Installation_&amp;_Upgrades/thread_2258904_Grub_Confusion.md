---
title: "Grub Confusion"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by SBader on 2014-12-31
Greetings, I have two SATA drives on my desktop PC. On one I have Fedora installed. I used to boot into it using F8, (startup disk selection). On the second hard disk I have WIN7 and it boots automatically as this disk has boot priority.

I have recently installed Ubuntu 13.10 on a separate partition in the disk with WIN7. I have indicated the correct /boot partition to EasyBCD. To my surprise I can boot into WIN7 with no problem but when I try to boot into Ubuntu I get booted into Fedora. I have added Fedora making it triple boot and giving the exact /boot location for both Linux systems but it still boots into Fedora in both cases.

The only way I can boot into Ubuntu is to first disconnect the hard disk containing Fedora. This works but is inconvenient and I think there must be a workaround. I'll be very grateful for suggestions.

---

### Post by oldfred on 2014-12-31
Your 13.10 is not supported anymore, better to update to 14.04 which also is a long term release.

We use grub for dual booting and do not recommend EasyBCD. EasyBCD uses grub4dos which is a very old grub with NTFS compatibility to chain load to another install. If other install in on same drive then that install's boot loader has to be installed into the partition boot sector or PBR. But grub2 is much larger than the old grub legacy and does not properly fit into a PBR. It has to convert to blocklists which are hard coded addresses. Those addresses may change with grub updates, or even a fsck. Then you break booting and have to reinstall grub. 

It would be actually better to use Fedora's grub to directly boot Ubuntu.
Do not know what version of grub Fedora uses, but if grub2, you should be able to run the equivalent in Fedora to  Ubuntu's sudo update-grub and it will add Ubuntu to its menu. 
You can do the the sudo update-grub in Ubuntu to add Fedora to its grub, but may have to add the LVM drivers and mount the Fedora partition for Ubuntu to see the Fedora install.

If you want to continue with EasyBCD, which some do use.
[http://neosmart.net/wiki/easybcd/dual-boot/linux/ubuntu/](http://neosmart.net/wiki/easybcd/dual-boot/linux/ubuntu/)

---

### Post by yancek on 2014-12-31
Since you can boot Fedora and if it is Fedora 16 or newer it should have Grub2, use the grub2-mkconfig command as explained at the Fedora project site below.

[https://fedoraproject.org/wiki/GRUB_2?rd=Grub2](https://fedoraproject.org/wiki/GRUB_2?rd=Grub2)

---

### Post by SBader on 2014-12-31
"grub2-mkconfig will add entries for other operating systems it can find. That will be done based on the output of the os-prober tool. 

That might however not work so well, especially not for booting other Linux operating systems, and especially not on UEFI systems. See [http://www.gnu.org/software/grub/manual/grub.html#Multi_002dboot-manual-config](http://www.gnu.org/software/grub/manual/grub.html#Multi_002dboot-manual-config) ."

---

### Post by yancek on 2014-12-31
If you are using a UEFI system, it would have been useful to post that in your initial post which you did not do.
What exactly have you tried?  Do you have a UEFI system with windows 7.  Which Fedora are you using?
I doubt you will be able to do this with EasyBCD as it is pretty limited and I seriously doubt if it is capable of booting more than one Linux so either option suggested above by oldfred should work if you insist on staying with EasyBCD.

---

### Post by SBader on 2015-01-01
No UEFI, I just copied the complete sentence from the link you kindly provided. My Fedora is 20 and I have no particular preference for EasyBCD.
I used "grub2-install /dev/sda" and "grub2-mkconfig -o /boot/grub2/grub.cfg" as advised in [https://fedoraproject.org/wiki/GRUB_2?rd=Grub2](https://fedoraproject.org/wiki/GRUB_2?rd=Grub2), but the os-prober did not find Ubuntu. The process simply made Fedora's grub the boot loader, showing Fedora and Win 7.
As I explained initially my Ubuntu does boot when I disconnect sdb (the disk containing Fedora 20) so I believe there must be a way to boot into it with no disconnection, but I'm apprehensive about the manual-config outlined in [http://www.gnu.org/software/grub/man...-manual-config](http://www.gnu.org/software/grub/man...-manual-config)

---

### Post by SBader on 2015-01-01
Thanks. Problem solved. I Clean Installed Ubuntu 14.04 where the previous version was installed. Ubuntu's grub has taken over the boot loader and allows booting into all 3 OS's

---

### Post by yancek on 2015-01-01
Probably the best solution as Fedora is basically a test distribution with very short term support.  In the past, when I installed Fedora, it rarely detected other Linux systems properly with Grub but it's been a while since I've tried Fedora.  Glad you got it working.

---

