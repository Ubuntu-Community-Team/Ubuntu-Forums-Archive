---
title: "Windows 7/Ubuntu Loading Problem"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by aoen on 2010-01-19
I recently installed Ubuntu alongside of windows 7 in the following way:
1. Shrank the size of my current partition for windows with Disk Management by 16GB
2. Created a new 16GB partition
3. Restarted and installed Ubuntu, when prompted with what partition Ubuntu should be installed in I was unable to choose the 16GB partition I created so I let Ubuntu take some disk space from the windows 7 partition


Ubuntu boots fine now, but when I try to boot windows 7 the following happens:
1. Variable period of time transpires and there are a bunch of wierd pixel colours at the top of the screen (sort of in a pattern, they keep changing though)
2. A very long time transpires and either: A) the computer restarts automatically OR B) Windows 7 loads

When windows 7 loads it works perfectly, I have had no problems with it when it manages to load.

I was wondering what I could do to fix this problem, would removing ubuntu and it's partitions help?

Thanks for the help guys, I don't know what exactly is going on but I fear something could tip this over and I will be unable to access windows 7 without reinstalling it at all.

---

### Post by akand074 on 2010-01-19
I'm not quite sure how to fix this, but this is deffinately not a problem with having ubuntu on a seperate partition seeing as the two partitions are completely independent of eachother and windows can't even tell that ubuntu is there. I think its a problem that may have occured using your partition manager, you should have used the one in the ubuntu installer its very good and safe (choose manually select partitions in the installer though I believe you already knew that). How to fix it I'm not sure I'd have to look into it a bit more after my classes if I have time.

---

### Post by presence1960 on 2010-01-19
You don't want to use gparted either from the Ubuntu Live CD or the gparted Live CD, or anything other than the windows disk management utility to shrink Vista/win 7 partition. There is a known unresolved bug (see [here]("http://bugzilla.gnome.org/show_bug.cgi?id=379482")).

Now you are going to try using the win 7 DVD to recover Windows on MBR (see [here]("http://ubuntuforums.org/showthread.php?t=1014708"), scroll down for Vista/Win 7 instructions). When completed reboot & see if Windows 7 boots fine.

If windows boots fine now restore GRUB to MBR from Live CD. If you don't know how to do so post back after doing this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I will need that info to give precise commands to restore GRUB to MBR.

---

### Post by darkod on 2010-01-19
> **aoen said:**
> 
2. Created a new 16GB partition


How many times we have to say this here.... :( Unfortunately most people seem to visit this forum only after they have problems.

YOU NEVER CREATE PARTITIONS FOR LINUX FROM WINDOWS!!! Windows can only create ntfs (not counting fat32) and linux DOES NOT work on ntfs.

You did great shrinking windows to make space for ubuntu. But especially if you are new to partitioning, dual booting, etc, it's best to leave that 16GB space as unallocated, unpartitioned space, and just use Largest Available Free space option when installing ubuntu. That will use the 16GB unallocated space.

Run the script that presence mentioned and we can see what's the current situation.

---

### Post by aoen on 2010-01-20
Thanks for all the help guys, I wasn't expecting to get such thorough support, but as it seems my computer is fine for now, the last 4 times I have tried my computer booted fine. I ran chk dsk and defrag so maybe one of those did something @.@.

---

