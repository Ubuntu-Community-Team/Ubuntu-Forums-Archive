---
title: "Karmic: Partitioner won't do anything during clean install..."
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by uncleV on 2009-10-24
...and so the installation fails. [COLOR=Blue]Edit:[/COLOR] At the other hand Jaunty 9.04 installs without problems.

What did I do:
- Downloaded a week ago <ubuntu-9.10-beta-desktop-i386.iso> from ubuntu.com. Md5sum - OK, burned the .iso at the lowest speed.
- Booted from Karmic LiveCD, checked disk for defects - OK, launched LiveCD session and deleted all partitions of the hard disk so it became *unallocated*.
- Restarted computer and started *Install Ubuntu*.
Went normally to the point of choosing how and where to install the system. Tried all three options - two guided and the manual. A window comes saying *Starting Partitioner* but soon it disappears, the CD starts to work and, as it seems, the installation gives up and the LiveCD session starts and ends normally. When I look with GParted the hard disk is still unallocated.
- Created ext4 partition with Jaunty LiveCD and then pointed Karmic to install there - the result is as above.

1.3 GHz CPU, 512+256 MB RAM and 80 GB HD.

I'll be able to give required specifications on this computer (if any) later, in Monday, as far as it is in my work office. Now I have 9.04 successfully installed on it.

---

### Post by mapes12 on 2009-10-24
I would nuke the HDD with [http://www.dban.org/](http://www.dban.org/) then start again.

---

### Post by uncleV on 2009-10-24
> **mapes12 said:**
> I would nuke the HDD with [http://www.dban.org/](http://www.dban.org/) then start again.

Thank you, may be I'll try it.
But I never had problems with that HD and, moreover, Jaunty installed on it without any complaints, flawlessly.
?

---

### Post by mike555 on 2009-10-24
You should run gparted and format the partitions , then install .

 sometimes a restart to the cd helps

---

### Post by ranch hand on 2009-10-24
That is a very old CD.  A week in testing is a long time.  I would download a new ISO.  We are in RC now.  Much more stable and i believe the installer is more reliable.

Be sure to check the md5sum.

Be sure that all partitions are not mounted or they will not be seen by the partitioner in the install process.

---

### Post by uncleV on 2009-10-26
The same issue:

[https://answers.launchpad.net/ubuntu/+source/gparted/+question/86967](https://answers.launchpad.net/ubuntu/+source/gparted/+question/86967)

---

### Post by uncleV on 2009-10-27
> **ranch hand said:**
> That is a very old CD.  A week in testing is a long time.  I would download a new ISO.  We are in RC now.  Much more stable and i believe the installer is more reliable.
The RC made it successfully. Thank you.

> **ranch hand said:**
> Be sure that all partitions are not mounted or they will not be seen by the partitioner in the install process.
I leaved them mounted and there were no problems.

---

### Post by ranch hand on 2009-10-27
This is great.  Mark the thread solved so people can see what you did (top of page under "thread tools").

---

