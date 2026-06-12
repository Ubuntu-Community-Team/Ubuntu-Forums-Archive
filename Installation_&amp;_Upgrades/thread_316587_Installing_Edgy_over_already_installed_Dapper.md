---
title: "Installing Edgy over already installed Dapper"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by EGE-FB on 2006-12-11
Hi, 

I already have Dapper running on my dual-boot laptop. I wanted to install Ubuntu Edgy but the Live CD doesn't work (an ATI card problem, blank screen) so I gave the alternate CD a go. Everything is fine, I'm passing through the steps and finally I'm at the base installation. Here, it says that the target of installation is unclean (Dapper:rolleyes: ) and it might cause some problems with the install. I click continue and go on with the installation. And it DOES cause problems. It gives an error about a folder and says that I should first clean out the target partitions before installing. 

My question is, how do I clean out the 2 ext3 and 1 swap partitions? I don't want to upgrade to Edgy, but rather install it over my Dapper (I have nothing important on the Dapper anyways). 

Thanks.

---

### Post by IanW on 2006-12-11
You need to delete then re-create & format the partitions during the install.

Make ABSOLUTELY SURE that you back up ANYTHING you wish to keep!

---

### Post by EGE-FB on 2006-12-11
If I delete the partitions, won't I be deleting grub boot loader as well? When I install Edgy after, will I still be able to access Windows through Grub?

---

### Post by aysiu on 2006-12-11
Edgy will reinstall Grub to the MBR, which should automatically add Windows to the boot menu, just as Dapper did.

---

