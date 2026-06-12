---
title: "I need to start from scratch"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by keri13 on 2007-06-17
I am currently running Windows XP and am trying to install Ubuntu.  I can't get into my setup menu to install the disk because the person I got the computer from somehow put a password on it so it won't let me do anything.  Is there a way to bypass the password or completely uninstall Windows XP and start from scratch with no OS at all?

---

### Post by Majorix on 2007-06-17
I don't know how you can bypass the password. And you better don't ask it away here, as it is considered hacking.

You can download Ubuntu off the net. It is easy if you have a fast enough connection.

And no you can't run without an OS. It is the bridge between the hardware of your computer and yourself, so without it you can't do anything.

---

### Post by az on 2007-06-17
> **keri13 said:**
> I am currently running Windows XP and am trying to install Ubuntu.  I can't get into my setup menu to install the disk because the person I got the computer from somehow put a password on it so it won't let me do anything.  Is there a way to bypass the password or completely uninstall Windows XP and start from scratch with no OS at all?

You can open the case and usually dissable the bios password, or reset the bios settings.  Alternatively, you can remove the hard drive, install ubuntu on it using another box, and then reconnect it to that computer.

You will need to reconfigure the xserver when you put the drive back.  You do that by booting into recovery mode and by running

dpkg-reconfigure -phigh xserver-xorg

---

### Post by raul_ on 2007-06-17
I think it's just easier to open your computer, remove the BIOS battery (it's a little battery, kinda looks like a watch battery, only bigger) , wait for about 5 or 10 min to be sure, put it again, and reboot. This resets your BIOS, and you'll lose stuff like time or special BIOS configurations you may have (nothing serious though). This also resets the password so you won't need one.

Off Topic: Darn Majorix!! Everytime you post, i feel like i blacked out and posted, and don't remember it!!

---

