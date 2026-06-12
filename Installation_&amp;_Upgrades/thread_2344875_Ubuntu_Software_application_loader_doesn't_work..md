---
title: "Ubuntu Software application loader doesn't work."
date: 2016-11-28
forum: Installation &amp; Upgrades
---

### Post by KytheraKid on 2016-11-28
Ubuntu Software application loader doesn't work.

I have two computers running Ubuntu.  I upgraded one from 14.04 to 16.04 LTS with no issues; a clean install from a bootable USB drive (image from Ubuntu), installed extra software apps (c.10 in all) using the Ubuntu Software Centre, restored backed up data, all done in about 30 mins no issues;  working just great.

So I've also upgraded my old laptop to 16.04 LTS using the same bootable USB drive, all looks ok except that the Ubuntu Software Centre doesn't load up at all.  First time it started to come up (unpopulated) then disappeared.  Now it doesn't even load - the icon flashes for a while + hourglass, the nothing.
Invoking gnome-software from the terminal doesn't work either.

I've looked at this forum and the Ask Ubuntu forum for ideas.

So far I've tried:
sudo apt-get autoremove gnome-software [it does]
sudo apt-get purge gnome-software ubuntu-software
sudo apt autoremove
suto apt install gnome-software ubuntu-software
sudo apt update
> then rebooted PC

I've tried sudo appstreamcli refresh --force --verbose [don't know what that is supposed to do;  doesn't make a difference]

Can someone please help this non-techie out please. Would be appreciated.  Thanks.

---

### Post by mörgæs on 2016-11-29
Have you tried ```
sudo apt-get update
``` followed by ```
sudo apt-get dist-upgrade
```?

---

### Post by KytheraKid on 2016-11-29
Thanks for the reply.  I had tried the first command but not the  second.  I have now solved the problem with help on the Ubuntu LaunchPad  forum.
See [https://answers.launchpad.net/ubuntu/+question/404472](https://answers.launchpad.net/ubuntu/+question/404472)

---

### Post by shag00 on 2016-11-30
Had the same issue and followed the link and copied the steps taken to correct the problem below:

1/ Deleted files in ~/.local/share/gnome-software/
2/ sudo apt-get autoremove gnome-software (takes about 5 minutes)
3/ sudo apt-get purge gnome-software ubuntu-software
4/ sudo apt autoremove
5/ sudo apt install gnome-software ubuntu-software
6/ Restart PC

This will generate a bunch of updates that need to be downloaded. Software update now works.

---

