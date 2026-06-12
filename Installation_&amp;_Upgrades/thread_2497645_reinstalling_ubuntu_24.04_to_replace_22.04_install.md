---
title: "reinstalling ubuntu 24.04 to replace 22.04 install"
date: 2024-05-13
forum: Installation &amp; Upgrades
---

### Post by badperson on 2024-05-13
Hi,
I dual boot win/ubuntu, and for awhile I have been meaning to upgrade to 24.04. I tried doing the upgrade from software and updates in ubuntu (also do-release-upgrade) but was running into errors mainly related to ppa packages. 
After lots of googling and trying different things, I somehow managed to kill the grub menu leaving me no option to boot into ubuntu. 

So I decided to reinstall with a bootable usb stick. I made that usb, booted up with it, and the installer gave me the option of installing 24.04 alongside windows and 22.04, but no option to replace 22.04. If I install 24.04 alongside, which will give me two ubuntu installs and one win11 install, will I have the option of removing the older ubuntu install later? 

Or should I just go nuclear with a full windows install followed by a new ubuntu install? 

thanks!
bp

---

### Post by oldfred on 2024-05-13
Do you have good backups? Both Window & Ubuntu?

Can you not do Something Else and choose (change) the existing / (root) partition for new /?
And if separate /home, also choose that during install.

If your backups include /home, list of installed apps, and perhaps some settings in /etc or system files you manually edited, reinstall is relatively easy.

There is also "dirty" install where you do not check format on existing / partition. You never check format on an existing /home partition. That keeps your files that are not part of install.
But that still overwrites any settings changes you manually updated, to defaults, so backup still important.

I keep two / partitions, last LTS and new LTS. But have all data in separate data partition(s) which I mount in all installs. I then only convert to newer install once I am happy with updates that new install includes. I use  Kubuntu with no snaps, so install is a bit smaller. New Ubuntu now uses a lot of snaps that then require a larger / partition.

---

### Post by grahammechanical on 2024-05-13
> the installer gave me the option of installing 24.04 alongside windows and 22.04, but no option to replace 22.04.

That is correct. We have to work our way through the options. Eventually, we get to a screen that offers an Interactive Installation or Automatic Installation. We choose Interactive Installation. We again work our way through the options until we get to a screen that asks How do you want to install Ubuntu? The options are:

Install alongside them
Erase disc and install Ubuntu
Manual Installation

Choose Manual Installation. You should be present with the partition layout of your drive. Select the partition that holds 22.04. It should be listed as 22.04. Click Change and then choose to format that partition and give it a mount point of /.

The installer should by now be selecting the EFI system partition as the default to install the Grub boot loader in. Now select Next. Work your way through the options until you get to Ready to Install. Review the choices made and select Install.

that is what I did a few days ago when I installed 24.04 LTS over 22.04 LTS on a  drive that had three installs of Ubuntu on it.

See the images here.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Regards

---

### Post by guiverc on 2024-05-13
I don't see mention of whether or not you're asking about a Ubuntu 24.04 LTS Desktop or Ubuntu 24.04 LTS Server install, as they use different installers.

What partitioning did you use?  as the *unclean* install I really like is currently *not possible* on 24.04 LTS due to an [*problem*]("https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2058638") appearing in QA (*Quality Assurance testing*), and thus a *format* is forced (*it cannot be unclicked so its no surprise to the user*) though in time, when that issue is fixed, the installer will have the current *forced-format* box clickable again (*as installer is snap package, it can update itself & doesn't require a respin of ISO, but my understanding is its not been changed yet*).  If you have a separate /home partition, your data can remain, but otherwise *unclean* install may not be possible (24.04 only)

---

