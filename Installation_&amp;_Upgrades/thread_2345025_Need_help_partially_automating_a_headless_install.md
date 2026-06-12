---
title: "Need help partially automating a headless install"
date: 2016-11-30
forum: Installation &amp; Upgrades
---

### Post by Superdude_123 on 2016-11-30
I need to install Ubuntu on a headless system remotely, however, as I don't fully know how the system will be built, I'd still like to go through the installation procedure manually (text based or GUI based).

I've been looking online, and my luck has been running dry.

In short, how I envision doing this is inserting a custom Ubuntu image in to a drive, booting from this image, and having the image connect to DHCP and create a SSH server so I can remotely connect to it and begin the installation procedure. I'll be able to see the IP address on the router, and I can also VPN in to the network if required.

Ideas?

---

### Post by 1clue on 2016-11-30
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

There's really not much magical about a linux installer image. You have two systems to worry about:  1 is the operating system which exists on the CD, and 2 is the operating system which is installed onto the regular boot disk.  They need not be the same distro or even the same operating system as long as the CD can create the correct filesystems and install the packages.

---

### Post by 1clue on 2016-11-30
You could also try to make a custom installer from [http://www.system-rescue-cd.org/SystemRescueCd_Homepage](http://www.system-rescue-cd.org/SystemRescueCd_Homepage)

---

### Post by 1clue on 2016-11-30
I've gone so far as to make bash scripts to help installation if I have a bunch of very similar hardware with very similar end-use.  I generally get a minimal system running and then run one or more scripts which consist of ```
apt-get install ...
``` and whatever else I need.

I have a set of handy scripts that I keep on a private git server that give me settings and tools I want everywhere. They're tuned specifically for doing my job, so they're not really useful for someone else, but putting these scripts on git means I can easily bring any system up-to-date with a single command, or modify or create new scripts or special behavior for some vendor (e.g. handle differences between Linux and Mac OS X)

This git project started out as a custom .bashrc and went on from there. It now has its own etc and bin directories and a 'skel' directory so I can use `uname -s` to determine what settings files to copy.  (uname -s returns 'Linux' on ubuntu for example)

This doesn't really directly apply to what you're trying to do, but it might help. Your best bet is to try the modified ubuntu installer I posted a link to above, but keep in mind that some of what you want might be better served by some other tool.

Good luck and have fun.

---

### Post by oldfred on 2016-11-30
I do not have a git server, but just a flash drive or two.
But do something similar to 1clue.

I have one script that creates mount points, edits fstab to add my data partition, edits /etc/exports for my NFS settings, and links all my data folders in my data partition into /home.
Second script installs lots of software, usually the export of installed apps from previous install.
I also have it install fallback/gnome-panel so I do not use Unity.
Scripts cover about 75 to 85% of my configuration, so in less than an hour I can have a fully configured system.

But when I built new system for FL, I had to major edit scripts as new UUIDs, and network was different 10. vs 168.

---

### Post by 1clue on 2016-11-30
Setting up a git server takes about 10 minutes. I highly recommend it.

[https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server](https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server)

---

