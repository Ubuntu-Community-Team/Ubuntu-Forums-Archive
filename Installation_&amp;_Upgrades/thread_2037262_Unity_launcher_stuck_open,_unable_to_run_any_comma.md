---
title: "Unity launcher stuck open, unable to run any commands or programs from Dash, 12.04"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by tinker1980 on 2012-08-04
I just now upgraded to 12.04, and I'm having some pretty serious problems. First of all, annoyingly, the Unity launcher is stuck open. In addition, the ONLY things I can do with my computer are programs shown in the launcher. I cannot use the Dash button, no matter what I type in the search bar, even programs I can run from the Unity launcher, it says "Sorry, there is nothing that matched your search.". Using alt-F2 to try and get something to run gives me a search bar, and a blank spot below it. Whatever I type there, it shows up in the bar as I'm typing, but other than that no response. Acts like nothing has been done. 

In addition, there is no shutdown button to be found anywhere. Have to Ctrl-Alt-T and type sudo halt in to shut the computer down - and then it gets hung on the "Ubuntu" screen with four dots. 

Any ideas? Do I need to give it up and install from a live CD?

---

### Post by tinker1980 on 2012-08-04
83 veiws and nobody knows?

---

### Post by tinker1980 on 2012-08-04
Ended up re-installing over it. What a pain. Now I need to know how to delete the Ubuntu Startup disk information from my flash drive. It won't let me touch it. I can't even format the silly thing. 

Don't everyone answer at once.

---

### Post by efflandt on 2012-08-06
How did you install the live/install iso to USB?  If you use **Startup Disk Creator** in Ubuntu, it just uses a common FAT32 file system which about any OS can access or work with.

If you somehow wrote the iso directly to the device instead of a partition, you no longer have a partition or partition table.  Maybe someone who has actually done that could help.

But I would first try using gparted to create an **msdos partition table** and then create a **FAT32 partition**.  That is what I have to do if I accidentally format the device instead of the partition.

---

### Post by tinker1980 on 2012-08-09
> **efflandt said:**
> How did you install the live/install iso to USB?  If you use **Startup Disk Creator** in Ubuntu, it just uses a common FAT32 file system which about any OS can access or work with.

If you somehow wrote the iso directly to the device instead of a partition, you no longer have a partition or partition table.  Maybe someone who has actually done that could help.

But I would first try using gparted to create an **msdos partition table** and then create a **FAT32 partition**.  That is what I have to do if I accidentally format the device instead of the partition.

I used the startup disk creator in Ubuntu. I've tried to delete the files from the USB thumbdrive from windows 7 and ubuntu 11.04 (Cannot get 12.04 to work, it just does what I mentioned in the first post) and I can't delete the files, format the USB drive, or change/create partitions on the thumbdrive. It has the typical set of files that I see when I look at a Live CD or USB thumbdrive being used as a startup disk.

---

### Post by terrypearson on 2013-02-26
> **tinker1980 said:**
> 83 veiws and nobody knows?

Just a suggestion. 

[LIST=1]
[*]Click on the Command line at the top (Called the HUD or Heads up Display).
[*]Then alternately press ESC and ALT back and forth a few times. It has worked for me in the past to get rid of that.
[/LIST]

---

