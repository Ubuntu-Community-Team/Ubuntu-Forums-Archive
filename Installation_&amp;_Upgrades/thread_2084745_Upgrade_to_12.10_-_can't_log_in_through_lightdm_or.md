---
title: "Upgrade to 12.10 - can't log in through lightdm or gdm"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by elsewares on 2012-11-16
I've already been through a number of threads, so I'll summarize my situation and my attempts so far:

I upgraded from 12.04 to 12.10 - apparently without error.  When I get to lightdm or gdm, I enter my information then get returned to lightdm or gdm. I use gnome-shell as my environment.

I have already done:

Moved .Xauthority to .Xauthority.backup
Changed from lightdm to gdm (and back)
I've gotten to tty1 and done:

sudo apt-get install --fix-broken
sudo apt-get update && sudo apt-get upgrade
sudo dpkg --configure -a

None of which have helped - there were no prompts for either process, although apt-get update upgraded linux-headers-generic and linux-image-generic. I've looked through dmesg, and there are no warnings or critical messages.

I feel like from the other messages that I'm a victim of a partial upgrade, but searching on that gets me the same information. I'm out of ideas. Help!

---

### Post by elsewares on 2012-11-16
Update - found this error in /var/log/gdm/:0-greeter.log

gnome-shell: Fatal IO error 11 (Resource temporarily unavailable) on X server

---

### Post by bogan on 2012-11-16
Hi!, ** elsewares**,

As your ' linux-headers-generic' was updated, try Purging and Re-installing your video driver.

There is a lot of trouble about with 12.10 updates not properly installing that file and the video driver - both AMD & NVIDIA-  failing to create the needed kernal module as a result.

Chao!, **bogan**.

---

### Post by greenwrangler on 2012-11-20
yeah it's deinitely a partial upgrade you're encountering....gnome-shell is not a part fo the upgrade....

ctl-alt-f1 and do 'sudo apt-get install gnome-shell"....

hth

---

