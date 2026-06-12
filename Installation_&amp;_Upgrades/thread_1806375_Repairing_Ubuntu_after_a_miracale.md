---
title: "Repairing Ubuntu after a miracale"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by silveringking on 2011-07-17
Ok, a miracle just happen...

I was partioning my disk with gparted, since I couldn't do it in windows or ubuntu, I run the cd at the startup...

The problem is I got to sleep while the computer divided the disk (I wanted to divide the disk since I have wubi and I wanted to do a full instalation). The problem is when I woke up the computer was frozen, I could move the mouse but the rest didn't work. So I got to sleep again, when I woke up the computer was still frozen, I got do to do some things and one hour later I came back and by miracle the computer was unfrozen... But for some reason the partition was not made! When I tried to run ubuntu I couldn't, when I tried to run windows 7 I couldn't too... I had to repair windows, now I am on windows but my wubi tells me that needs the windows cd to repair, I can't get it repaired...

This is a miracle indeed, no data seems lost, the computer is frozen more or less since 4am to 8pm...

Now I want to repair wubi, partion my disk and move to a full ubuntu install all safely! What can I do?

Edit: My computer is an Asus X51L...

---

### Post by Bucky Ball on 2011-07-17
I would try installing from a CD. Installing from Wubi can be a little flaky. You can make the partitions you need during install.

---

### Post by silveringking on 2011-07-17
How do I backup my data on the ubuntu environment?

---

### Post by Bucky Ball on 2011-07-17
What are you backing it up to?

---

### Post by silveringking on 2011-07-17
Like I had a few documents there, what I have to backup is nothing more than 500mb that is for sure... Just some documents and the favourites on mozilla. I have the habit of sepparating my disks by different disks...

---

### Post by Bucky Ball on 2011-07-17
I'd drop it on an external device, if you have one. You can do this from the desktop by drag and dropping or via the LiveCD the same way.

---

### Post by silveringking on 2011-07-17
You're not understanding... How do I reach out my things? I don't have access to the home folder...

---

### Post by silveringking on 2011-07-17
Also I told ya, I can't login in ubuntu, it gives me that windows error repair thing... There's a temporary fix?

---

### Post by ManualSparrow on 2011-07-17
You should boot a LiveUSB or CD and use that (independent) Ubuntu environment to move your things onto the external device.

---

### Post by Blasphemist on 2011-07-17
I'm no wubi expert but I believe he is right that you should be able to see the windows partition from nautilus (the ubuntu file manager) while booted to the live cd. That partition will show up as a directory in the windows partition I believe. You can then copy the files to other storage.

Then you can go about the installation. Do you have any questions about the installation?

---

### Post by silveringking on 2011-07-17
No thank you! Sorry I am young to ubuntu...

---

### Post by Blasphemist on 2011-07-17
No problem! Glad to have you in the group!

You might want to look at this site that does a great job of providing information on setting up a dual boot of ubuntu and windows. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by bcbc on 2011-07-17
You can view your wubi install from windows by using this: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)
Just download, run, and point it at C:\ubuntu\disks\root.disk (or change drive letter if it was installed on a different drive)

You can also mount it from a live CD/USB environment if you prefer. 

You can in fact migrate your wubi just from just the root.disk: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
You'd first create the partitions, then migrate from a live CD.

---

### Post by Bucky Ball on 2011-07-18
> **ManualSparrow said:**
> You should boot a LiveUSB or CD and use that (independent) Ubuntu environment to move your things onto the external device.

+1. Exactly. ;)

You'll be able to access the /home folder with that.

---

