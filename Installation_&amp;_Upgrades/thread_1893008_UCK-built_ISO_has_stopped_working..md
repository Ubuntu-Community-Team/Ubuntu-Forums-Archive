---
title: "UCK-built ISO has stopped working."
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by bythescruff on 2011-12-09
I've been working with the UCK tools for a few weeks now to customise the Ubuntu 11.04 desktop ISO, and I've built several ISOs which run through an installation completely automatically - insert the CD, turn on the machine, and the installation proceeds right through to the "installation is complete - click this button to reboot" step.  My edit-build-test cycle was working fine until today; the installed machines booted to Gnome just fine.  

Today, however, I find that the installed system only gets as far as the GRUB prompt.  Examining the logs (by booting the failed system from a LiveCD) I find lots of errors in /var/log/installer/casper.log like this:

(gconftool-2:515): GConf-WARNING **: Failed to load source "xml:readwrite:/home/username/.gconf": Failed: Could not make directory `/home/username/.gconf': No such file or directory

...which suggests that the user's directory didn't get created by the time gconf was setting up the user's configuration from the mandatory defaults.  I'm adding that user in my preseed file, which hasn't been modified in several weeks, which suggests the problem is elsewhere.  The user's home directory does get created at some point; it contains the following:

/home/username/.cache
/home/username/.cache/wallpaper

The last thing I can remember doing to the unpacked file system - mounted using the UCK tools - was adding an entry in /etc/gconf/gconf.xml.mandatory/%gconf-tree.xml to turn on accessibility.  I then built the ISO as usual, and I didn't notice any errors during its automated installation; nothing seemed to go wrong until it failed to boot.

I'm at a loss as to how to diagnose the problem; can anyone help?  Thanks in advance...

---

### Post by bythescruff on 2011-12-14
...tumbleweed...

Just in case the mystery was keeping anyone up at night, I got back up and running by rolling back by one ISO image and trying my changes again.  I have no idea why the ISO became unbootable, but it's working now, and it has the same gconf errors in the installer logs, so they were apparently a red herring.

---

