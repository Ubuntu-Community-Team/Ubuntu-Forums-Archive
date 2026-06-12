---
title: "cant copy files to external drive with live cd. please help!"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by seth elohim on 2010-03-12
Okay, here goes. Windows screwed up grub when I ran a recovery application. After unsuccessfully trying to fix the MBR, I decided it was a good excuse to buy the 1 TB external drive I have been wanting and simply copy the files I want to keep from the 114 gig file-system using my live CD, and then reinstall karmic from scratch. These files consist of various things, family photos, text docs, compressed archives, ect. All of them crucial to me. After searching through the forums and the wiki quite a bit, I am still at a standstill. Some files copied with no problem, on the other hand, many folders wont give me permission to copy or even view them, saying that I am not the owner. (which of course I am) I cant seem to find a way in the GUI to change permissions, and I cant seem to navigate the terminal to my old home folder at all, I can only get to the empty home folder on the live CD. I just want to put my password in, change the permissions, grab my stuff, and fresh install karmic 9.10 all over again. The closest I get to it in the terminal is to fdisk -l, but that just shows me the partitions, and I cant cd into a partition because it isn't a directory, even if I knew which one I wanted, and I don't. If this is a dumb question I am really sorry, but I have been trying all day to no avail. Somebody please help me!

---

### Post by garvinrick4 on 2010-03-12
Mount your partition in Live Cd then Alt/f2 type in 
gksudo nautilus. Will open computer and say root. Click
in Places on your partition and it will open that file system
in root. Navigate to your home files and drag and drop to external
drive.

---

### Post by soltanis on 2010-03-12
In the terminal you need to mount the disk.

I assume you were able to find out what the partition was...I'll pretend its /dev/sda1 from here.

```

sudo mkdir /media/home
sudo mount /dev/sda1 /media/home

```

Now the drive will be mapped into /media/home. If you plug in the external drive, it will probably get automounted to somewhere also in the /media directory, so

```

cd /media
ls

```
(do it as root if you have permissions issues)

Look for other folders in there. One of them should point to your external drive.

Then from the terminal type

```

sudo nautilus

```

To run the file manager under a root instance (if you are using a Gnome liveCD; if you use KDE that would be dolphin, and xfce would be thunar). Now try to move the files again, this time as root.

If that doesn't work, try to save the files as a tarball, without preserving permissions:

```

sudo tar --create --file=/media/external_disk/save.tar file1 file2 ... filen

```

If you get permission denied even as root, the file system might've been corrupted by Window's rude intervention.

---

### Post by seth elohim on 2010-03-12
thank you so much, that did the trick nicely. you are a life saver!!!:p

---

### Post by seth elohim on 2010-03-12
> **garvinrick4 said:**
> Mount your partition in Live Cd then Alt/f2 type in 
gksudo nautilus. Will open computer and say root. Click
in Places on your partition and it will open that file system
in root. Navigate to your home files and drag and drop to external
drive.

this was what I did.
however I am gonna play around with the other posters way as well, for knowledge sake.
man I hate windoze...if it wasn't for Sony acid pro I would never use it for anything.
Thanks again. this is a great OS, and a great community!

---

