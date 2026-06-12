---
title: "Need to use live CD to backup HD to USB Drive"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by Robotman on 2007-09-01
Due to a recent [problem]("http://ubuntuforums.org/showthread.php?t=540208"), I need to use the live CD to backup hda1 to a USB drive (only 6.8GB, it will fit) before I reinstall Ubuntu on that drive.  I tried to copy&paste from hda1 to the USB drive, but that didn't work because I don't have the permissions set up to do that.  How can I accomplish this?  Is there  set of commands I can enter into a terminal?

---

### Post by merlinus on 2007-09-01
What is the format of hda1, and of the usb drive?

-merlin

---

### Post by Robotman on 2007-09-01
hda1 is ext3 and the USB drive is fat32... but the USB drive can be reformatted if need be.

---

### Post by merlinus on 2007-09-01
I assume you manually mounted hda1?  What are the permissions?

And what are the permissions for the usb drive?

You can look at these via Nautilus (Places/Computer}.

Right-click on the partition, then Properties/Permissions.

-merlin

---

### Post by Robotman on 2007-09-01
Both are mounted to /media/disk.
I have full create/delete permissions for the USB drive (Owner: ubuntu - Live session user), but not for hda1.  The owner is set as root, and I can't change that from the properties panel.

---

### Post by merlinus on 2007-09-01
How can two different drives have the same mountpoint?  Or are they different?

Once again, did you manually mount hda1, or did it occur automatically?

-merlin

---

### Post by Robotman on 2007-09-01
Oops, the USB drive isn't mounted to /media/disk..... it's mounted to /media/Lexar.
I mounted hda1 manually... by going to location "Computer" and right-clicking on it then selecting "Mount Volume".

---

### Post by merlinus on 2007-09-01
Try this:

```

sudo chmod -R 777 /media/disk

```

-merlin

---

### Post by Robotman on 2007-09-01
Ok, I entered that.... what does that do?
EDIT: Ah... I can copy&paste the home folder now.... but I can't seem to get the complete contents of the rest of the drive copied that way.

---

### Post by merlinus on 2007-09-01
The command gave recursive read-write-execute privileges to everyone.  So that should include subfolders and files.

Did you make sure Show Hidden Files is activated?

What else are you trying to copy?

-merlin

---

### Post by Robotman on 2007-09-01
Many thanks for that. ;)
I'm guessing my emails and browser data (Evolution and Firefox) will be somewhere in the /bin folder... am I right?

---

### Post by merlinus on 2007-09-01
No.  They are in hidden files in /home/user.

Make sure you turn on Show Hidden Files (Ctrl-H) in Nautilus.

-merlin

---

### Post by Robotman on 2007-09-01
Ah.... I'll be sure to do that.  Now I'll have to wait for the copying process to finish... 30 min total.  Would the hidden files be copied as well if they weren't showing in Nautilus when I started copying?

---

### Post by merlinus on 2007-09-01
Select-All will not include the hidden files if they are not showing.

-merlin

---

### Post by Robotman on 2007-09-01
ok, thanks!

---

### Post by merlinus on 2007-09-01
You are most welcome. Glad it is working for you.

-merlin

---

### Post by Robotman on 2007-09-01
Big problem now... I can't copy& paste my evolution mail... I get an error message of "Invalid parameters".  This is the most important data I have in that folder, so I need to find another way of backing-up the ".evolution" folder .  How can I do this?

EDIT: hang on a sec.... despite the many error messages... the contents of the ".evolution" folder appear to have been copied without a problem.

---

