---
title: "Installation Partition help please?"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by *Kat* on 2011-01-27
Sorry to post again!! I got to the installation stage...woop, but now when I try and install it asks me to do it manually, here is a picture of my current partitions...

[http://i55.tinypic.com/2q0jbb6.png](http://i55.tinypic.com/2q0jbb6.png)

Can anyone give me a hand please?

---

### Post by kansasnoob on 2011-01-27
Clues:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Check the internal links.

---

### Post by sikander3786 on 2011-01-28
I am a strong recommender of manual partition even if the installer doesn't ask you to. There are many reason most importantly, it doesn't mess up your system whereas Install side by side option in 10.10 is know to do some damage. See the excellent post linked above by **kansasnoob**.

For a regular Ubuntu install, you basically need 2 partitions. "/" Ubuntu system partition which holds the base files + you home directory (which holds your personal files + configurations) and a Swap partition.

You can use gparted to create partitions for installation. Delete your sda4 and create an Extended partition in that space. An extended partition itself is a primary partition and you can only have 4 primary partitions basically.

As you have large space available, I would recommend to create a separate /home partition. It would save all your personal files and settings for other programs e.g, Firefox bookmarks in case of a re-install. So, my partition setup would look like this.

1. "/" partition, ext4, 25 GB.
2. "/home" partition, ext4, size = Total available space minus (size of "/" + Swap"/")
3. Swap partition size = or double than your RAM if you plan to hibernate.

Then choose manual partitioning in the installer and edit your / partition. Choose its mount point "/". Then edit "/home" partition and choose its mount point "/home". Swap should automatically detected and mounted. Edit it and re-confirm its mount point.

On the manual partitioning page, you'll also get a choice for the location of Grub. If you've got only once HDD, you don't need to change the location. If there are more than one HDDs, make sure it is going to be installed to the proper HDDs MBR from which you plan to boot Ubuntu.

If you've got any doubts/queries, feel free to ask.

---

### Post by *Kat* on 2011-01-28
thank you!! I've just gone through the partitioning etc, now I'm at install, so I just leave "device for boot loader' at ATA HD and dont change it at all?

Also, when I click Install now it says "the file system on /dev/sda5 assigned to / has not been marked for formatting. Directories containing system files  that already exist under any defined mountpoint will be deleted during install" isthat what I want to happen? lol

---

### Post by sikander3786 on 2011-01-28
> ***Kat* said:**
> thank you!! I've just gone through the partitioning etc, now I'm at install, so I just leave "device for boot loader' at ATA HD and dont change it at all?

Also, when I click Install now it says "the file system on /dev/sda5 assigned to / has not been marked for formatting. Directories containing system files  that already exist under any defined mountpoint will be deleted during install" isthat what I want to happen? lol
Yes you can leave the device for bootloader to ATA HD.

When you edit the partitions, mark them for a format and the other error message should go away as well.

---

### Post by *Kat* on 2011-01-28
*le sigh* Finally get to the install/name/location pages and then it says "Input/output error" going to check my copy for any errors and try again see if that helps

Woop! Formatted my USB and re-downloaded the iso torrent instead, worked a charm :D 

Thanks everyone!! :) x

---

