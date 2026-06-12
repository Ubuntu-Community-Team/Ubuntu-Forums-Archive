---
title: "new laptop partition sizes and 64 bit advice"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by EmuAlert on 2011-06-15
I just got a new laptop and I'm trying to find out how to balance my partitions. I was planning on making a relatively small Ubuntu partition while storing all my person, big files on my NTFS partition and connect it back to Ubuntu with links.

Is this a bad idea?
What's a comfortable size for an Ubuntu partition?

Everything seems to run fine on 64 bit Ubuntu, and though I might get more RAM, I only have 4 GB of RAM for now. Should I install 64 or 32 bit?

---

### Post by oldfred on 2011-06-16
Install 64 bit. There are new threads every other day discussing this if you want all the pros & cons do a  forum search. All the cons are old info.

If you are going to have most of your data in the NTFS shared partition then I would just install to a 20 to 30GB / (root) partition with /home inside the / and swap which is the default install. I normally suggest a separate /home to keep data in another partition. If you have little or no data in /home it is very small (about 250MB) and easily backed up for a new clean install if you want.

Do not use your main windows NTFS partition as windows does not like others writing into it, but create a shared NTFS partition (D: in windows). Some windows users also suggest a separate partition so when you have to reinstall windows your data is separate (backups still required). I would set your C: drive in Ubuntu as read only when you mount it to avoid issues.

---

