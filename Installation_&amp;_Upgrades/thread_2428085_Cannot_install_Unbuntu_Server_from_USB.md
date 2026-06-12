---
title: "Cannot install Unbuntu Server from USB"
date: 2019-09-30
forum: Installation &amp; Upgrades
---

### Post by m4xen on 2019-09-30
Hi

Im totaly new to Linux and would like to give it a try on our new server we have at work (small server for 5 ppl).

I've decided to install Ubuntu Server but it seems not go so well. I've made a bootable USB according to this tutorial: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)
I've chose to boot from USB first, SSD as second in BIOS.

This is what happends when I power up the computer, tons of fail msg:

[ATTACH=CONFIG]284108[/ATTACH]

Any idea what I'm doing wrong?

The OS im trying to install is: "Ubuntu Server 19.04"

---

### Post by SeijiSensei on 2019-09-30
Is that what you see while booting from the USB stick, or booting the system after an attempted installation?

If this is your first time out, I suggest installing from a [desktop version]("http://cdimage.ubuntu.com/bionic/daily-live/current/") and choosing all the obvious defaults. Don't choose to encrypt the filesystem your first time through. Keep things simple for starters.

The only difference between the server and desktop versions is that the latter have a GUI and a different set of default packages.  The server version expects you to know how to use the command shell from the terminal. You don't sound ready for that so stick to a version with a GUI.You can run all the server programs from a desktop version, though you'll need to install them separately afterwards. If you're doing file sharing you'll need Samba for Windows clients and NFS for *nix clients.  Beyond that, what else are you intending to do?

---

### Post by Autodave on 2019-09-30
I would also be trying 18.04 on that.  18.04 is a long term service release (LTS).  It is supported for at least 5 years.  Your 19.04 is a short term release and only supported for 9 months, so stick with the LTS releases.

---

### Post by TheFu on 2019-09-30
+1 on using 18.04.  19.04 support ends in January.  "Servers" used by real people (not just for 1 week testing) need to be LTS releases.  You'll need to move to 19.10 in Nov/Dec and then to 20.04 in May/June.  LTS releases are April of even years. Every other release is not an LTS.

+1 on using a desktop if you are new to Unix/Linux.  Use it a few hours every day for 6 months to learn some basics, like file and directory permissions.

---

