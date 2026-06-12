---
title: "Issues with Ubuntu install - 19 hrs and counting"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by soluphobe on 2007-07-11
I hope this isn't a common question or the wrong place to post, but I'm having serious issues with installing 7.04 on my Laptop (new to Linux, so apologies if I sound dumb).

Specs:
256 RAM (operating at 224)
Celeron Processor 2.20 Ghz
Currently running (and planning on dual-booting) XP
DVD reader/CD burner (not sure of the speed, 8-32x ?)
Dell Inspiron 1000 (purchased years ago, so not shipped with Linux)

When I boot from the liveCD, I get to the desktop (sometimes missing panels, sometimes without icons or background, but sometimes fine) after anywhere from 20 mins to 2-3 hrs of booting (it's been getting faster the more I boot).  I open Install.  My machine sits for about 45 mins, then shows a blank window with no text labeled 'Install' and has a flurry of CD activity.  Occasionally, it wants me to log in to Ubuntu (as default user).  Other times it goes into screen saver and sits for 5+ hrs.  Once it went for 19 hrs before I turned it off - just sitting with a blank screen doing nothing.

I get an error every time I boot to the CD about (IIRC) Gnome Display Setting Daemon.  Occasionally I get something about deleting a trash applet too.   

...And there goes my laptop into screen save as I type this.  I'm starting to get irritated with my hardware, as I'd like to install Ubuntu on this machine.  

Is this hopeless, or am I ignoring something obvious?

---

### Post by checho on 2007-07-11
Did you tried with another instalation cd or run it on other computer? It seems to me that this one is somehow corrupted. Also remember to create a new partition for linux because otherwise it going to be installed over windows (too obvious but worth to remember).

---

### Post by merlinus on 2007-07-11
Try the text-based Alternate Desktop install cd.

-merlin

---

### Post by Pumalite on 2007-07-11
256MB RAM or less>Alternate Xubuntu CD:

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by soluphobe on 2007-07-12
Unfortunately, I can't test whether the liveCD is good or not because I don't have access to another computer that I can mess around in the BIOS of (Sorry, as I know that is probably a very good test).

Where is this Text-based CD?  Never mind, I'm looking for it on Google.

I was afraid of 'You have no RAM' issues, so I guess I'll have to give Xubuntu a try.  It's a pity I have Dial-Up - it will be a few days - weeks - whatever before I get the image (I have problems with getting a CD shipped to me)

Thanks for the help, though.

---

### Post by Bartender on 2007-07-12
Is there no way of borrowing some broadband long enuf to get the Xubuntu .iso?
I bring my 1GB thumbdrive in to work with me for big dowloads  :)

---

### Post by dbhunt on 2007-10-11
I had the same "Gnome Settings Daemon" problem during a 7.0.4 install and the "Alternate CD" solved the problem.  Memory was only 256MB - not enough for install using Live CD.

See my post: [http://ubuntuforums.org/showpost.php?p=3516374&postcount=11](http://ubuntuforums.org/showpost.php?p=3516374&postcount=11)

---

### Post by everah on 2007-10-12
Sorry for butting in on this thread, but what are the chances of memory being the cause of the issue in this thread:
[http://ubuntuforums.org/showthread.php?t=572939&highlight=Xubuntu+7.04](http://ubuntuforums.org/showthread.php?t=572939&highlight=Xubuntu+7.04)

I only ask because I have had some major problems getting any linux distro installed on my brothers HP Pavilion ze5730 and the most recent issue was akin to the one mentioned in the linked to post.

I swear this machine has the specs to handle a Xubuntu install, but it gets to the point where it is 15% into the filesystem search, the kicks me out of install and opens the /boot directory.

I am downloading the alternate installer at the moment, but I couldn't help but think that the install issues I having might be caused by a memory issue, though I have 192MB of RAM on it.

---

### Post by travm on 2007-10-12
dont forget about your shared video ram, it will be in there eating away at your "useable" ram.  Assuming you have onboard vga

---

### Post by everah on 2007-10-12
I ended up installing from the text installer (alternate) and it loaded fine. In fact, it loaded very fast on the first run with no issue at all.

The actuall software in the OS is a little scant, but it is workable.

---

### Post by Pumalite on 2007-10-12
If you want a fast system, try post # 4

---

### Post by everah on 2007-10-12
Yep, that is the version I used.

---

### Post by Pumalite on 2007-10-12
You are fine then. I bet is fast!

---

### Post by everah on 2007-10-12
Yes, it is extremely fast now. I wish the features were a little more robust (seeing as it had XP Home on it before) but I think I can live with it the way it is.

---

