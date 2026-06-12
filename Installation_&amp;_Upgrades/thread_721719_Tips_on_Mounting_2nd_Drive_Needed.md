---
title: "Tips on Mounting 2nd Drive Needed"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by markekeller on 2008-03-11
I've got a two-drive system; Windows XP and Linux are installed on the first one, and I want to use the second for my /home directory and /usr/local.  So, I'm wondering - what's the best way to do that?

I'd like to mount the directories in their respective places, rather than using symbolic links.  But I also want to have them both stored in the same partition, because I'm not sure how much space they'll eventually need in comparison to each other.  Is it possible to mount just a folder somewhere, instead of a whole partition?

---

### Post by patrickaupperle on 2008-03-11
You could probably put them on seperate partitions then resize the partitions as needed. Ask around for filesystem recomendations.

---

### Post by Pumalite on 2008-03-11
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by markekeller on 2008-03-11
Possibly . . . though according to someone in this [thread on LinuxForums]("http://www.linuxforums.org/forum/linux-newbie/38524-mounting-usr-home-same-partition-2.html"), changing the starting point of an ext3 partition can mess things up (which is what'd happen when I resize them).  Is that true?

Also, the person who started that thread was trying to do the same thing as I am, pretty much, and he tried doing it with symbolic links, but it didn't work right.  Some of that could be because the folders in question already had stuff in them, whereas I'm starting with empty directories - but what do you think?

EDIT: The above was in reply to patrickaupperle.

---

### Post by Pumalite on 2008-03-11
You have to follow the instructions to the letter and be careful with your commands ( you could copy and paste just to be sure). You have to backup everything every time you adjust partitions. That link works.

---

### Post by markekeller on 2008-03-11
Thanks!  Very handy stuff there!  Do you know if it's possible to somehow have both of the folders I want to move in the same partition?

---

### Post by Pumalite on 2008-03-11
Don't bother with /usr/local.

---

### Post by markekeller on 2008-03-11
Because it isn't used much, right?  I'm planning on starting a Linux software-review blog, which will entail my compiling/installing a great lot of stuff.  And most programs compile into /usr/local, so there's a good chance that the contents of it will exceed the relatively small partition that I have the main / directory in.  Which is why I want to do what I want to do. :)  Unless you have a better idea?

---

### Post by markekeller on 2008-03-11
Okay, now I've messed things up.  I decided to, after all, have the folders I want to move in seperate partitions.  So I created two xfs partitions on the second drive, and followed the tutorial that Pumalite linked to, only changing what was necessary to reflect my partition names, and the fact that I'm using xfs instead of ext3.

But, apparently, something didn't work right.  When I rebooted and tried to log in, it said that my .dmrc file had incorrect permissions, and logged me right back out.  From searching around online I eventually figured out that the permissions weren't retained across the copy, for some reason, and everything belonged to root.  Then I accidentally did a "chown -R mark *" in the / directory, and after I changed it back, I couldn't sudo anymore, and . . .

Anyways, I really messed things up.  I hadn't really created any data yet, so I'm just going to reinstall; and try to get this cross-partition mounting working tomorrow! :D

---

### Post by Pumalite on 2008-03-12
Sorry to hear that. Good luck with your installation.

---

### Post by patrickaupperle on 2008-03-12
> **markekeller said:**
> Okay, now I've messed things up.  I decided to, after all, have the folders I want to move in seperate partitions.  So I created two xfs partitions on the second drive, and followed the tutorial that Pumalite linked to, only changing what was necessary to reflect my partition names, and the fact that I'm using xfs instead of ext3.

But, apparently, something didn't work right.  When I rebooted and tried to log in, it said that my .dmrc file had incorrect permissions, and logged me right back out.  From searching around online I eventually figured out that the permissions weren't retained across the copy, for some reason, and everything belonged to root.  Then I accidentally did a "chown -R mark *" in the / directory, and after I changed it back, I couldn't sudo anymore, and . . .

Anyways, I really messed things up.  I hadn't really created any data yet, so I'm just going to reinstall; and try to get this cross-partition mounting working tomorrow! :D

It would be good to put home on the second partition during install.

---

### Post by markekeller on 2008-03-15
Yes!  That's exactly what I did!  I was able to set up the mounting very intuatively during the installation, and it was all very easy and quick.  Now things are set up just the way I like them. ;)

One question yet, I guess - I set the NTFS partition that I have Windows on, to be mounted as /media/windows.  The thing is, I'd kind of like it if it wasn't mounted every time I boot, and would only do so if I click on it in the GNOME 'Computer' window - the way it does when you don't set anything up yourself, and it just detects everything - only *then* it would go to /media/windows, rather than media/disk1 or something.

Not hugely important, but I'm just kind of wondering: how would I go about doing that?

---

### Post by Pumalite on 2008-03-15
Edit your /etc/fstab and remove the line that belongs to Windows (ntfs)

---

### Post by markekeller on 2008-03-15
I figured that would do it.  But is there any way to make it go to /media/windows rather than /media/disk1 or whatever it picks automatically?  Without manually mounting it from a terminal, of course - I'm talking about when clicked on in Nautilus.

---

