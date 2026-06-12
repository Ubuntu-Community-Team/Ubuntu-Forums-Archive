---
title: "Ubuntu Upgradation"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by tamalbasak on 2012-02-28
Hi,

I am using Ubuntu 10.10 currently. My system has dual boot with Ubuntu and Windows 7. Now I want to upgrade linuxOS to Ubuntu 11.04 through Update Manager. Will this direct up gradation effect the already installed software packages in 10.10 ? Will it disturb the dual boot process ? 

My friends are requested to help me.

---

### Post by grahammechanical on 2012-02-28
The upgrade process will pull in new libraries and new versions of the programs that are installed. If you have software installed through a PPA, then uncheck that PPA from Software Sources and after the upgrade replace it with the latest 11.04 PPA for that program. And then you can upgrade that program as well.

At the end of the upgrade the Grub configuration file will be updated. This process will identify the operating systems on the hard disk including Windows 7 and you will get a Grub menu just as you do now. It will not included the Ubuntu 10.10 kernel boot options. That will all be cleared out as part of the upgrade.

As the download takes place you can click on Details and actually see what is being done as it is being done.

The operating system is being replaced bit by bit while still working. The final replacement takes place when you reboot. This is very clever when you think about it.

Both 10.10 and 11.04 are built on Gnome 2. So they are not too different from each other. But 11.10 and onwards are built on Gnome 3. So, a lot more stuff has to be replaced. It seems to be that this replacement is only now being finished or perhaps almost completed with the release of 12.04.

Regards.

---

### Post by snowpine on 2012-02-28
Check out the official documentation, it is very easy to follow:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by LinuxFan999 on 2012-02-28
The best way to upgrade Ubuntu is to back up your data and do a clean install (from CD) of the version of Ubuntu you want to upgrade to (11.04 in this case). Upgrading through the update manager may break Ubuntu, and require reinstallation of Ubuntu.

---

### Post by gordintoronto on 2012-02-28
"I want to upgrade linuxOS to Ubuntu 11.04"

Why?

In two months, Ubuntu 12.04 will be available. If you don't like it, you can consider Kubntu 12.04, Xubuntu 12.04, Lubuntu 12.04 or Linux Mint 13.

Every one of them is a better option than 11.04.

---

### Post by Mark Phelps on 2012-02-29
Linux distros are infamous in their NOT supporting roll-back to a previous version.  If you do the upgrade in-place and something goes wrong, you could easily end up with a "broken" system -- and no easy way to go back to a "working" one.

So, BEFORE you do that, look into using Clonezilla to image off your current "working" setup to an external drive.  At least that way, if the worst happens, you will have a way to easily revert back to a "working" system.

---

