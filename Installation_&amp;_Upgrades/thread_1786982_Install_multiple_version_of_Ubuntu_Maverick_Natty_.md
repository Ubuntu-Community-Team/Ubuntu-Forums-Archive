---
title: "Install multiple version of Ubuntu: Maverick Natty and Win XP"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by airolds on 2011-06-20
Hi everybody,

I installed (about 2 months ago) Ubuntu Natty and Windows XP in my computer at work. Everything was working fine until I had to install Flight Gear (I work for an Aerospace company and we use it to visualise some simulations). Unfortunately it seems as FG is quite buggy if used under Ubuntu Natty. I was therefore thinking of installing Maverick in my work computer...however I don't really know how to proceed.

How can I put in a new Ubuntu version without erasing the grub loader? How should I partition the disk? Does any of you have (or know where I can find) some specific guide lines?

Thank you folks!

-simone

---

### Post by sanderd17 on 2011-06-20
There is nothing wrong with erasing grub. When you install Maverick, you will get the option to install it next to Natty and Windows. That will overwrite the current GRUB but the grub will still be OK.

If you want the old grub back, go in Natty and run the grub-install script.

---

### Post by oldfred on 2011-06-20
+1 on sanderd17 comments.

I have multiple copies of Ubuntu, but I do have 3 drives. One is XP only. My somewhat (now) newer drive has several Ubuntus, but my current working one is on sdb. I prefer clean installs but keep old install and only use 20-23GB for each / (root). But keep all data separate.

You want to keep track of which grub you have in the MBR and that will be the one that boots to its install and lists that Ubuntu first. Other installs will be listed at the bottom of the menu.  Whichever install you want to boot most often should be the one you have in the MBR.

With multiple copies of  Ubuntu, you should not share /home. You can if in a /home partition, but then need to use different user names & passwords which keeps them separate. I prefer a separate /data that lets you have all data folders like Documents, Music etc  that you can access from all installs.

One of the ways to know what is installed where & to document lots of details of booting is this script. I make sure I include in my backups a copy of a current results.txt so I know my current configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by airolds on 2011-06-21
Thank you for your answer guys! I will go on and follow your advice. I will let you know what the end results will be!

---

### Post by airolds on 2011-06-21
Awesome, it worked exactly as you guys said!

Thank you!!

-simone

---

