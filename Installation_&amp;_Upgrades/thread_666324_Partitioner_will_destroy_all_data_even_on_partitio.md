---
title: "Partitioner will destroy all data even on partitions not marked for formatting?"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by kingpotnoodle on 2008-01-13
I have a Debian Etch install on a machine I have been using purely as a server, I now want to use it more for a desktop machine and want to put Gutsy on it...

Linux sees my RAIDed drives as a single massive ATA volume which I have partitioned with:

hda1 = 100MB /boot
hda2 = 2048MB swap
hda3 = ~50GB /
hda4 = ~700GB /srv (on here is all my movies, music, docs, etc)

I select hda1 to be formatted and mount as /boot, hda2 to be swap again, hda3 to be formatted as mounted as / and then hda4 to just be mounted as /srv and not formatted...

Then it tells me:

"Warning this will destroy all data on any partitions you have removed as well as on the partitions which are going to be formatted"...

I don't want to lose anything on /srv, that would be really annoying!! How can I make sure it doesn't destroy that?

Do I just not select to do anything with it and mount it later?

Better to use the alternate CD?

---

### Post by edm1 on 2008-01-13
i dont think it'll touch hda4 but you should be backing up your drive before partitioning anyway (yes 700GB is not so easy to backup).

---

### Post by kingpotnoodle on 2008-01-13
> **edm1 said:**
> i dont think it'll touch hda4 but you should be backing up your drive before partitioning anyway (yes 700GB is not so easy to backup).

It's got about 320GB used, mostly iso images and stuff... I have backed all the important stuff up of course!

But it would just be far less annoying not to have to copy it all back across the network if possible!


I just want to do similar to a Windows format of C and leave D all alone during install and then it's there when you boot :)

---

### Post by edm1 on 2008-01-13
All the warning is saying is that you will lose any data on the partitions you are removing or having formatted. So if you have not removed or flagged to format hda4 then it wont be touched.

---

### Post by kingpotnoodle on 2008-01-13
I follow now, the key is in the wording... I interpreted it the wrong way to mean it would destroy data on partitions I had not selected to format... but now I see what it means! (Homer -ish doh! moment)

---

### Post by AL888 on 2008-02-25
> **kingpotnoodle said:**
> I follow now, the key is in the wording...
[**_[COLOR="Blue"]The wording is f*cked up so much you can't make it any dumber![/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=707038")

The point is: 
There is NOTHING to "remove"! There is no option at all to remove anything! 
There is only one option to select the installation hard drive or partition. 
So, I automatically must assume, this ubu thing recognizes all other partitions as "removed" and so is going to delete "destroy all data"!

---

