---
title: "Error message when installing updates using Update Manager"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by alviash on 2010-08-11
I am very new to Ubuntu and IT guy just left the company, so help!
I started the Update Manager, clicked on "Install Updates" and the following error message appears:

[B]Not enough free disk space

The upgrade needs a total of 31.5M free space on disk '/boot'. Please free at least an additional 24.8M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/B]

Here's what I've done so far:

[LIST=1]
[*]Empty trash, still not enough space
[*]Ran 'sudo apt-get clean', still not enough space
[*]Ran GParted and found the following configuration:
[LIST=1]
[*]at /dev/sda:
[LIST=1]
[*]/dev/sda1, File system: linux-swap, size: 7.45 GiB, flags: RAID
[*]/dev/sda2, File system: ext3, size: 117.66 MiB, used: 105.39 MiB, flags: boot, raid
[*]/dev/sda3, File system: ext3, size: 458.19 GiB, used: 11.93 GiB, flags: raid
[/LIST]
[*]at /dev/sdb, same as /dev/sda, seems to me that it is configured as a RAID backup to /dev/sda
[/LIST]
[*]So it looks to me that the /dev/sda2 partition is already full and thus causing the error message during installation. My questions are:
[LIST=1]
[*]What I should do at this point?
[*]I thought of increasing the partition size of /dev/sda2. Is this the right course of action? How do I go about doing this? What is the recommended partition size for boot partition?
[/LIST]
[/LIST]
Thank you in advance!

---

