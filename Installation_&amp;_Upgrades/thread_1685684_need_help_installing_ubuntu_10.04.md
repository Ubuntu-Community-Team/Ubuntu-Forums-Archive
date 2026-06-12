---
title: "need help installing ubuntu 10.04"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by naj690 on 2011-02-11
recently i used wubi and decided to install ubuntu properly now, so i uninstalled the wubi. my windows drive used to be only two (C: and D: ) but yesterday i made a new partition (N:, size 20GB) to install ubuntu in.
when i run through the setup i got to this page:

[IMG]http://i150.photobucket.com/albums/s95/naj690/Screenshot-1.png[/IMG]

now i dunno which to select. when i select the "install them side by side" option, this warning pop out:

                               [IMG]http://i150.photobucket.com/albums/s95/naj690/Screenshot-1-1.png[/IMG]

i didnt know whether this is the right option or not so i go back and selected "specify partition manually". then it show this window:

[IMG]http://i150.photobucket.com/albums/s95/naj690/Screenshot-2.png[/IMG]

i want to install it in the N: drive which i think is sda6, so i double click it and it shows this window:

[IMG]http://i150.photobucket.com/albums/s95/naj690/Screenshot-3.png[/IMG]

i dunno what to change so i just leave it and click ok. when i click forward it shows this warning:

[IMG]http://i150.photobucket.com/albums/s95/naj690/Screenshot-4.png[/IMG]

now i dunno what to do. help anyone?

p/s: i run the setup in ubuntu just to take screenshots. if i run it during boot it still show the same thing

---

### Post by P4man on 2011-02-11
For some reason the option to install in to unpartitioned space is no longer in the installer. Either you have to let the installer resize your windows partition, or you have to manually configure partitions. So do it manually.

Ill await the screenshots, then Ill provide more details.

---

### Post by naj690 on 2011-02-11
uploaded the screenshots

---

### Post by P4man on 2011-02-11
Slight problem. You can only have 4 primary partition on a drive. Thats a bios limitation. If you need more partitions, you have to create an extended partition (which counts as one primary), and inside that extended, you can create as many logical ones as you like. You cant put windows on a logical partition, but linux has no such problems.

Can you talk me through the partitions?

sda1 is a windows recovery partition, leave it
sda2 is where windows is installed?
sda5 is your data partition?
sda6 is where you want to install ubuntu?
sda4 is ?

---

### Post by naj690 on 2011-02-11
sda2 is where my windows is installed ( C: )
sda5 is my data partition ( D: )
sda6 is where i want to install ubuntu ( N: )
i dunno where did sda4 come from. it doesnt show in My Computer. but in the window in my first screenshot it says that sda4 is Windows Vista (loader). but i never installed vista though...

---

### Post by P4man on 2011-02-11
Before deleting any of them, can you check what is on sda4 ? 10 gigs are in use it says, so there must be something.  In the places menu, select "15.8 GB filesystem" or something along those lines. You may have to close the installer first.

---

### Post by naj690 on 2011-02-11
oh, its a backup drive that Lenovo manufacturer made. its for a software called One Key Recovery

---

### Post by P4man on 2011-02-11
Eck. And you want to keep it?
Now i *think*, but Im not entirely sure, that hidden partitions dont count towards the limit of 4 primary partitions. The fact you already have 5 seems to prove that. Going by that assumption and the assumption you want to keep that lenovo partition..

Delete sda6.

Then create a new partition of type "extended". Make it use all the free space.

Then inside this extended partition, create 2 more logical partitions.

First one, you use Ext4 as file system, the mount point is "/" (pronounced *root,* thats where the OS goes), and make it use all the available space, minus what you will use as swap. I dont know how much RAM you have, but you dont have a lot of diskspace, lets put swap at 2 GB, we can change that later. So the size of the / partition would be ~20 GB. Mark it for formatting.

Then create another logical partition inside the extended partition as type linux-swap that uses the remaining ~2GB

That should do it, I hope.

---

### Post by naj690 on 2011-02-11
should i do all this while booting or can i just install it while ubuntu running? btw i have 2GB ram

---

### Post by P4man on 2011-02-11
> **naj690 said:**
> should i do all this while booting or can i just install it while ubuntu running? btw i have 2GB ram

Not sure I understand the question. You can do that from the live cd installer,  just like how you made the screenshots.

2GB Ram + 2GB swap should be plenty, but if you want to hibernate, you might want to increase the swap space to 4GB or there might not be enough space to hibernate. Wouldnt worry too much about it though.

---

### Post by naj690 on 2011-02-11
thx man. it worked. u really helped me. one question, can i change the boot order during the boot? i mean now when i start the laptop it shows something like this:

> Boot on:
ubuntu 10.04
ubuntu 10.04 (recovery)
memory bla..bla..bla...
windows 7 (loader)

can i change windows 7 to the top so that after 10 sec my laptop will automatically load windows 7?

---

### Post by P4man on 2011-02-11
sure, easiest way installing "startup manager"
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Dont forget to mark this thread as [solved] (in thread tools) but dont hesitate to ask any further questions :)

---

