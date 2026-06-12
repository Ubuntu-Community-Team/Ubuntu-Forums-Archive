---
title: "Need advice on enlarging Ubuntu partition, all in one partition"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by clay7 on 2013-07-31
I have a laptop that dual boots with Win7 and Ubuntu 12.04 LTS. The Ubuntu partition is 30GB and I want to enlarge it to 100GB. Here is a pic of my partitions from gparted:

[ATTACH=CONFIG]244950[/ATTACH]

I've seen other guides online, but they all seem to involve creating a separate partition for the /home directory. I'd rather not do that...I'd like to have Ubuntu just on the one partition. 

**How should I go about enlarging the Ubuntu partition so that Ubuntu is on one partition?**

Background: I am loosely familiar with creating partitions using gparted and in Win7, but I want to check with you guys just to be safe. It looks like I'm supposed to shrink Windows first, and then add the unallocated space to the Ubuntu partition, but what if the unallocated space is NOT next to the Ubuntu partition?

---

### Post by papibe on 2013-07-31
Hi  clay7.

First you want to avoid as much as possible to touch your Windows partition within Ubuntu.

Boot in Windows7 and defrag your main Windows partition. Then open '[Disk Management]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html")' and shrink the partition. Windows may be not let you shrink too much its own partition, but try to get as close as you can.

You may need to repeat the process by defraging a couple of times, and shrink again.

Then, you need to use your Ubuntu installation media as a Live CD/USB. Once you get to the desktop, open Gparted and do this:
[LIST]
[*]If you were not able to shrink your Windows partition to the desired amount, do it now using Gparted.
[*]Now you'll have an empty space between your Windows partition and the 2 partitions you are using for Ubuntu. Move them to the left so they start next where the Windows ends.
[*]DO NOT touch your HDDRECOVERY partition.
[*]Now you'll have space between your Ubuntu root partition and HDDRECOVERY. Resize the Ubuntu partition to take advantage of the whole space.
[*]Shutdown, take out the CD/USB and turn your computer on.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by clay7 on 2013-07-31
Thanks papibe - that was great! I'll do it tonight and will post back with the results.

---

### Post by clay7 on 2013-07-31
I've shrunk the Windows partition from within Windows to the desired size, and now I have the installation CD in the drive, with gparted running. 

It's like you said: > Now you'll have an empty space between your Windows partition and the 2 partitions you are using for Ubuntu. Move them to the left so they start next where the Windows ends.

How do I move the Ubuntu partitions to the left so they start where Windows ends?

---

### Post by papibe on 2013-07-31
For each Ubuntu partition: Right click on the partition. Select move. Move it as fas as it lets you to the left.

---

### Post by clay7 on 2013-07-31
Ah...does this look correct? (sorry for the pic quality...apparently I couldn't mount a USB drive to transfer the pic while gparted was running)

[ATTACH=CONFIG]244952[/ATTACH]

---

### Post by papibe on 2013-07-31
Yes, it does.

Let us know how it goes.
Regards.

---

### Post by clay7 on 2013-07-31
Great! I just clicked "Apply all operations" and it's working. I have to head out but will post back with the results later tonight.

---

### Post by clay7 on 2013-08-01
This worked perfectly! After the resize operation completed, I booted into Win7, and then into Ubuntu and both are working normally. 

Thanks very much for your help!

---

