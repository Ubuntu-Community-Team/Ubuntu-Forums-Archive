---
title: "Edgy (6.10) to Feisty (7.04) upgrade fixed!"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by john.wheeler on 2007-05-04
I recently tried upgrading from 6.10 to 7.04 only to find that my PC refused to boot - it just got stuck at the splash screen and after a few mintues dropped out to the "BusyBox" shell - not much use.

I had previously upgraded the kernel to 2.6.17-11 from 2.6.17-10, so I tried to start the older kernel. No luck in normal mode, but I could get a command prompt in recovery mode.

Reading through this forum, someone suggested running:

sudo aptitude update && sudo aptitude dist-upgrade

I presume that this would get and install the new distro, even though I had already successfully downloaded all the files.

On running this, I was prompted to run:

dpkg --configure -c

This went thorough a lot of config, with a few prompts to keep or overwrite modified config files.

After this I rebooted, and am now able to start the new kernel. Woo hoo!

Most of my apps still seem to be intact, although some icons are missing. My wireless config tool (WiCD) has disappeared.

This hasn't been quite as painful as I expected, but let's see how I get on....

John.

---

### Post by goodtimetribe on 2007-05-04
ack! being thankful you can get to a recovery mode scares the daylights out of me... I'm not ready to do it. Do you think you could have done anything to prevent the problems? Maybe use those few commands in text mode to begin with? I'm really nervous about breaking my vmware installation.

---

### Post by Sef on 2007-05-04
There are more problems with doing an update than a clean install.  However, with an upgrade your configurations should be kept.

---

