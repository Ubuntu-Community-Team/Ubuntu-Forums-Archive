---
title: "Copy Ubuntu installation to another machine"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by sabrehagen on 2010-03-19
Hi,

I have just spent two days configuring my Ubuntu 9.10 installation on my netbook and tweaking it to get it just right. I don't want to go through this whole process again on my desktop, so is there a way I can copy my entire installation (programs, configurations, all settings, EVERYTHING) to another existing Ubuntu installation. I say existing, because I've looked into methods like dd but they're not suitable. I'm running Ubuntu in a virtual machine on my desktop so I can't dd it because of changed drivers etc.

All help is much appreciated. Thanks!


sabrehagen

---

### Post by srs5694 on 2010-03-19
There are several ways to do this. One that seems to be popular these days is [Clonezilla.](http://clonezilla.org/) You'll probably need to run it from an emergency disc on the target system, though. Also, the hardware differences could cause problems, particularly for things like the boot loader and /etc/fstab configurations.

A less drastic approach is to copy your user configuration files by copying over the contents of /home/{user} (where {user} is your username) and/or your system configuration files by copying over all of /etc (except for /etc/fstab and perhaps /etc/X11/xorg.conf). Doing this will replicate your settings, but won't copy over installed programs; you'll need to use apt-get, Synaptic, or whatever to add/delete packages to your satisfaction.

---

### Post by oldfred on 2010-03-20
You can make a list of all your installed apps:

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

or using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

I had been using my portable while in FL and want to copy all my additions back to my desktop so I did this to read them back in after exporting on the portable:
  431  dpkg --set-selections < ubuntu-filesport2010Mar
  432  sudo dpkg --set-selections < ubuntu-filesport2010Mar
  434  sudo apt-get -y update
  435  sudo apt-get update
  436  sudo apt-get dselect-upgrade
  437  history

---

