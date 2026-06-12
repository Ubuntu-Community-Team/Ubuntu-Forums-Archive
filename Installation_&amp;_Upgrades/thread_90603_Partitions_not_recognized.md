---
title: "Partitions not recognized"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by dark_templar on 2005-11-15
Hi

I’ve tried to install Ubuntu in my computer, but it seems the installer cannot see the partitions I created, displaying just the entire hard drive with no partitions.

Before I had installed debian on the same system, so the partitions are there already, and if I try to install back debian, it shows all partitions created.

What could be the problem? I am almost giving up because of this.

---

### Post by az on 2005-11-15
When you select "manualy edit partition table" it does not show the partitions?

Sounds like a bug.

You can always install debian, change all your apt sources to ubuntu (including the install cd) and then install ubuntu-desktop.

to add the cd as a repository, type
apt-cdrom add

---

### Post by dark_templar on 2005-11-15
[QUOTE=azz]When you select "manualy edit partition table" it does not show the partitions?
[/QUOTE]

Yes, it doesn't show the partitions even when I do that. Maybe I'll install back debian after all...

---

### Post by az on 2005-11-15
If you ctrl-alt-f3, do you see any wierd error messages?   And can you go into the ctrl-alt-f2 terminal and copy the logs to a usb stick or something so that you can file a bug report about this?

---

