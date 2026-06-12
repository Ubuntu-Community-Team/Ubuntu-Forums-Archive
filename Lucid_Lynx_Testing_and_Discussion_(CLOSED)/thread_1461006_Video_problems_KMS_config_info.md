---
title: "Video problems? KMS config info"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BrokeMahPC on 2010-04-23
Just found this and thought it may help some who have video driver problems. There are some reports on launchpad that the nomodeset option has stopped working with the release candidate - there are alternative commands.
This is an ubuntu wiki page about configuring KMS on Lucid and Karmic:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by psyke83 on 2010-04-23
> **BrokeMahPC said:**
> Just found this and thought it may help some who have video driver problems. There are some reports on launchpad that the nomodeset option has stopped working with the release candidate - there are alternative commands.
This is an ubuntu wiki page about configuring KMS on Lucid and Karmic:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

First of all, check if the file /etc/modprobe.d/radeom-kms.conf exists. If so, delete the file as it will override anything on your GRUB boot line.

Secondly, the "nomodeset" parameter is now called "radeon.modeset=0" (I assume you're using the radeon driver, as it's the only driver with optional KMS at the moment).

---

### Post by BrokeMahPC on 2010-04-23
Interesting what you say - that means we don't have to edit grub anymore - we can just put the commands in /etc/modprobe.d/radeon-kms.conf? Might be a better way of doing things?
That seems to be what the page I found suggests?
I have that file but it's blank - I'm using fglrx till a fresh install of Lucid after final release as it does not cause any problems for me at present..

(as an aside, from Ubuntu 10.10 xorg is moving to /usr/share/xorg.conf.d, looks like things are changing!)

---

### Post by psyke83 on 2010-04-23
> **BrokeMahPC said:**
> Interesting what you say - that means we don't have to edit grub anymore - we can just put the commands in /etc/modprobe.d/radeon-kms.conf? Might be a better way of doing things?
That seems to be what the page I found suggests?
I have that file but it's blank - I'm using fglrx till a fresh install of Lucid after final release as it does not cause any problems for me at present..

(as an aside, from Ubuntu 10.10 xorg is moving to /usr/share/xorg.conf.d, looks like things are changing!)

You can edit the radeon-kms.conf file instead, yes. However, I read in a changelog that the radeon-kms.conf file would to be removed from newer packages by default, as it overrides any configuration in /etc/default/grub, which can confuse users. People who have been testing the development release will have this configuration file on their computer, but not those who install from the final release (I think). It's cleaner to remove the file.

I don't have a recent ATI card, so I've never had to use the fglrx driver - however, if you already installed and activated the fglrx driver, then I'm pretty sure that there should be absolutely no modesetting happening. Modesetting is controlled by the "radeon" kernel module which is not loaded when fglrx is on your system (and the fglrx driver doesn't support modesetting).

---

### Post by BrokeMahPC on 2010-04-23
Ahhh back to editing Grub then. Yes I went to fglrx to get away from the KMS issues until things had settled down. Will have another look at radeon after the 29th.

---

