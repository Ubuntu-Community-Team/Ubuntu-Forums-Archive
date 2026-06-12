---
title: "upgrade from 20.04 to 20.10 cannot write problem"
date: 2020-11-10
forum: Installation &amp; Upgrades
---

### Post by Claus7 on 2020-11-10
Hello,

the other day I tried to upgrade from 20.04 to 20.10.

Upgrading was going fine until I was notified that internet connection was disconnected. This had happened to other upgrades as well, yet at a moment later I was able to see a message that was like that: no write permissions...

I do not remember exactly the message, which disappeared from screen, and then a new message informed me that the upgrade did take place with some errors and that I had to issue the command:
dpkg --configure -a.

I was not able to open any application at that time from panel. So I decided to drop to command line and restart my system. (Maybe it would have been a nice idea to issue the command proposed). The system did not proceed to boot normally so it was forced to restart.

Then I came across BIOS. I did not change anything and proceeded to boot, yet errors appeared on screen with a distinct one being:
[ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0, 0) ] ...something like that.

I typed: fsck /dev/sda1 -y
and saw many errors getting fixed. 

Then I think that I typed reboot to initramfs prompt, and was greeted with grub.

I chose just the previous kernel I was using prior to the upgrade at recovery mode and typed:
dpkg --configure -a

which continued the upgrade.

When finished I opened a terminal and typed:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

with the last command getting rid many files.

My system now seems to be fine.

Just for anyone that will encounter the same behavior.

Regards!

---

