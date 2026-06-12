---
title: "Installer not resizing FAT32 partition"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by Quest-Master on 2005-10-30
I've installed Hoary and Warty before and the installers have worked perfectly and are able to resize my FAT32 media/Windows partition.. I'm currently on a computer networked to the computer I am installing Breezy on. I told the installer to set up a simple server with the install logs on it, and am viewing them right now.

The problem is, I tell the partitioner a new size for the partition. It is above the minimum and below the maximum, just enough for a new 5GB partition for Breezy. No problems; except, it just goes back to the partitioner every time with the same size, over and over again.

Here are the logs.

Partman logs - [http://pastebin.com/411254](http://pastebin.com/411254)
syslog - [http://pastebin.com/411260](http://pastebin.com/411260)
messages - [http://pastebin.com/411264](http://pastebin.com/411264)
hardware-summary - [http://pastebin.com/411265](http://pastebin.com/411265)

Anyone know why it's not working?

---

### Post by aysiu on 2005-10-30
I don't know why it's not working, but you could use a live CD to resize the partition instead (Knoppix, for example, using QTParted). Mandriva's DiskDrake is also an excellent resizing tool. You don't have to go through with the Mandriva install--you can do just the partitioning with DiskDrake.

---

