---
title: "Upgrade Trouble"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by Dug Fin on 2008-06-20
I had 7.10 running well and decided to upgrade to 8.04. I started the download process and fell asleep. When I woke up nothing seemed to be working. I restarted the system.

The boot manager still showed 7.10. There is also windows 98 and a FAT32 data partition on the machine.

The system took a long time booting and showed me the command line login for a short time before the gui log in screen came up. After logging in all I now get is the cursor and blue screen background.

Can someone please tell me how to restore this system to normal function? I really want to avoid a full re-install.


Thank You

---

### Post by Dug Fin on 2008-06-20
I've been working on it and have some new information.

After I get to the GUI login, if I go to options and tell it to boot to Failsafe GNOME I get an almost normal looking desktop. It doesn't do much and if I try to open a window to view a drive all the icons disappear, but I do have some options.

I get an error message "Internal Error- failed to Initialize HAL!"

I had a update available message pop up. Trying to start the update program did not do anything.

If I told the system to run the x-server script I would end up with the orange screen and a cursor and nothing more.

I could play and listen some mp3 files on the desktop.

I could open firefox but not connect to the web.

Anyone have any ideas how I can straighten this out?

---

### Post by AndThenWhat on 2008-06-20
Can you get access to a terminal on the Failsafe GNOME?

If so, you could try to stop and restart things like nautilus and seahorse and see if that yields any better results. Try running gnome-system-settings if you can as that is easier than managing processes via the command line.

---

