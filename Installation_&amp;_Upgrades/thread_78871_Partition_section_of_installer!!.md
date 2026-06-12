---
title: "Partition section of installer?!?!"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by andrewsawyer on 2005-10-19
This is slightly different to the usual 'should I dist-upgrade' or will it kill my system questions.

I tried that on my laptop, and it did kill my system :-( however it had lots of extra programs installed.

I have a media server running that has a pretty much clean install of Hoary on it.  All media is in a different partition (or drive) to that which Hoary is installed on.

I have the full Ubuntu install with Gnome at the mo, however I want to go to Breezy but just the server install - no Gnome, as I will be putting MythTV onto it.  It sits under the tv, so I will be using ssh to do all the installs after I have got the basic Breezy on it.  I'm pretty much figuring that it will be one hell of a lot cleaner to do a full install again from scratch, however I'm confused by the partition section of the installer.

You see, I want to keep my /home partition as home in Breezy, but I also want to keep the data on it.  As standard it looks like the partitioning tool will wipe any partitions that you set first.  How do I specify that my /home partition gets auto mounted as /home while keeping the info on it?  Also, how do I get the other two drives (call one video and the other music) to auto mount on boot from within the partition tool on install?  Is it possible?

Probably makes no difference, however currently all partitions/drives are ReiserFS with the exception of the /root pertition which is ext3.

Any help would be much appreciated.

---

### Post by manicka on 2005-10-19
[QUOTE=andrewsawyer] How do I specify that my /home partition gets auto mounted as /home while keeping the info on it?  Also, how do I get the other two drives (call one video and the other music) to auto mount on boot from within the partition tool on install?  Is it possible?
[/QUOTE]
You'll need to enter the expert mode in the partitioner. 
Just configure the partion to be mounted at whatever mount point you like e.g /video, /music, /home, but most importantly choose_ not_ to partition it

---

### Post by andrewsawyer on 2005-10-19
Expert hey?  I wish!!!!

Thanks for the advise.  I'll give it a go.  Just wish I had enough DVD's to back up the 800Gb first!

---

### Post by manicka on 2005-10-19
[QUOTE=andrewsawyer]Expert hey?  I wish!!!!

Thanks for the advise.  I'll give it a go.  Just wish I had enough DVD's to back up the 800Gb first![/QUOTE]

Then my only advise would be not to finalise the install until you're absolutely comfortable that you have it right

---

### Post by andrewsawyer on 2005-10-19
Hiya,

tried it last night.  First the Expert mode, but it was a little too expert for me, so I tried the server mode.  This went fine.  I now have a bash prompt, 3 mounts, and ssh installed.  Thank you for your help.

---

