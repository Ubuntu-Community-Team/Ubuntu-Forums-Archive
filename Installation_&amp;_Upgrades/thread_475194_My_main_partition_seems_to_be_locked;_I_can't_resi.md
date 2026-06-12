---
title: "My main partition seems to be locked; I can't resize it."
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by thatcrazycommie on 2007-06-15
I'm currently running Feisty Fawn by booting from the Live CD. I've tried running the installer, and when I get to the point where I have to choose a partition to resize (I'm using the "manual" option, because I want to dual boot Windows XP), I double-click my main partition, and there is no "resize" option. I then tried to do it using the GNOME Partition Editor, and the problem seems to be that the main partition is somehow "locked":

[img]http://img.photobucket.com/albums/v330/thatcrazycommie/Screenshot--dev-sda-GParted.png[/img]

As you can see, there is a "lock" icon right to the left of "ntfs." Does anyone know why this is, and/or how to fix it?

Incidentally, and far less importantly, I have no idea where those 7 MB and 38 MB partitions came from, or what's on them (I've never seen them in Windows), and if anyone knows how I can figure that out, that would be cool, too.

---

### Post by merlinus on 2007-06-15
First of all, I do not think you have sufficient free space for Feisty, especially after you add many of the wonderful apps that are available.

You may wish to free up space in your ntfs partition first, delete temp files, and defrag it several times.

Also, doesn't XP have its own disk manager that can be used for resizing?

-merlin

---

### Post by thatcrazycommie on 2007-06-15
I was going to worry about freeing up more space once I got Feisty installed and working. However, I think I've solved the problem: I accidentally mounted that partition earlier when I was trying to access the files on my hard drive. I've unmounted it, and hopefully that will fix it. If it doesn't, I will post here again.

---

