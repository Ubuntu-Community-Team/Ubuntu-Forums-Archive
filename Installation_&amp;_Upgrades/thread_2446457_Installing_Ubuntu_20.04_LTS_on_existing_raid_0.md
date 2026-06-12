---
title: "Installing Ubuntu 20.04 LTS on existing raid 0"
date: 2020-07-01
forum: Installation &amp; Upgrades
---

### Post by wesley410 on 2020-07-01
About 5 years ago I created my little nas/pihole with 4 hard drives in a mdadm soft raid 0.  It is partitioned into a 100gb partition, 10gb swap, and the rest one giant void of data.

This past weekend was my weekend of project fails.  One of which included murdering, with out reservation, my ubuntu installation.  After trying and failing to install asterisk, freepbx, fusionpbx, and probably some other ones i cant remember, my pi hole stopped working.  Then my webmin stopped working.  Then my plex stopped working.  Then my shares to the media in my plex stopped working.

I did some basic troubleshooting, got the internet working on the box, but still cannot get anything to work.  At one point i decided to upgrade, first to 18 and then to 20.04.  Still nothing is working right.  Installed xfce because I suck at the command line and it is just unstable.

So I would like to reinstall ubuntu,while keeping my raid data intact.  There is no back up.  The data is not valuable.  Just time consuming to replace. I would rather save it if possible.

I have the installer on a USB drive and am at the storage options section. I have chosen Custom storage layout and thats where I am stuck

What do I select as my mount
What do I select as my boot disk.

I have md127 (existing) type software raid 0 size 14tb
ST400XXb with partitions for swap and 100gb partition for previous ubuntu install.

under used devices i have
ST400XXa, part of existing raid 0 md127
ST400XXb, part of existing raid 0 md127, bios_grub partition 97mb
ST400XXc, part of existing raid 0 md127
ST400XXd, part of existing raid 0 md127


Playing with the settings the only things I can really do is 
set ST400XXb as boot device
format md127 existing, keeping current ext4 and mounting at /
but i am afraid to commit this

---

### Post by wesley410 on 2020-07-08
So after some more searching I could not find anything that said what to do if you have an existing raid with your OS installation on it.

So heres what you do:

From the installer enter the shell
using fdisk -l (l for list)
find the names of the drives in your raid
Specifically youre looking for the drive with your OS installation on it as well.
Verify you have the correct drive name
Then get ready to delete the partition with your OS
Verify your drive name (using the main drive name and not the partition name...look for sda and not sda2)
blink
Verify your drive name
hesitate
verify your drive name again
now run fdisk [device location] (for instance fdisk /dev/sda)
follow the on screen help (hint m) for which options to use to delete your partion (hint d)
Not sure if this part was needed but I made a new partion table as well...
save your changes
reboot
restart installation and your ex-os partition should be selectable for mount point, formatable, and the drive should be boot disk-able

happy installing.
sorry for the double post.

---

