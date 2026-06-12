---
title: "Installing Lubuntu 13.04 alongside Win XP with multiple NTFS partitions"
date: 2013-08-09
forum: Installation &amp; Upgrades
---

### Post by Gilad_Pellaeon on 2013-08-09
Here's a question I have and forgive me if it has been asked before. I currently have two NTFS partitions, one is a 60gb (C: drive) partition holding my main Windows XP SP3 install and (E: drive) is the other 15gb NTFS partition just holding nothing but my music collection. Before installing Lubuntu 13.04 would I be better off to delete the E: drive partition and somehow reallocate it back into the C: drive if possible via control panel with *Administrative Tools -> Computer Management -> Disk Management* or is there another way to do this so I can remove that E: drive and setup my dual boot install so that I can have the bare minimum needed on this 80GB hard drive to boot Windows XP and allocate the rest of the drive to Lubuntu? 

Figured I would ask now as I do want to try using Lubuntu as my main OS eventually with Windows XP dual boot as a fallback if needed without worrying about an extra partition I deleted screwing up a dual boot install somehow.

---

### Post by carl4926 on 2013-08-09
SO you have a 60GB and 15GB = 75GB total in use of a 80GB HDD?
How much free space is there in both of those partitions? Integrating the 2 would surely help on space given your minimal real estate.

Assuming you bring the 2 partitions together to make one, how much free space will there be and given that you have to then shrink some space (but only half of that available), how much will you have left for Xubuntu?
Remember you have to defag windows before adjusting partitions and installing xubuntu.

---

### Post by Gilad_Pellaeon on 2013-08-09
> **carl4926 said:**
> SO you have a 60GB and 15GB = 75GB total in use of a 80GB HDD?
How much free space is there in both of those partitions? Integrating the 2 would surely help on space given your minimal real estate.

Assuming you bring the 2 partitions together to make one, how much free space will there be and given that you have to then shrink some space (but only half of that available), how much will you have left for Xubuntu?
Remember you have to defag windows before adjusting partitions and installing xubuntu.

Currently 27gb free on the main drive and 3gb free on the other. I would delete some stuff on C: to free up space and I had planned to format the E: drive to free up more. Didn't even think of defragmenting with a tool I use called Defraggler before installing. I had a rough idea in my head of using something like say 65-70gb for Lubuntu (not sure if i'll install Xubuntu now since this is an old Dell tower with 1 gb ram and Intel q965 graphics) since Lubuntu will probably perform somewhat better then Xubuntu on this old 2007 tower and a basic 5-6gb for Windows XP with the idea being Lubuntu will pretty much occupy the vast majority of the hard drive and leave a tiny bit for Windows XP.

---

### Post by carl4926 on 2013-08-09
You seem to have a plan
Xubuntu should work but lubuntu will offer somewhat less demands on the system, but there is not much in it

---

### Post by Gilad_Pellaeon on 2013-08-09
> **carl4926 said:**
> You seem to have a plan
Xubuntu should work but lubuntu will offer somewhat less demands on the system, but there is not much in it

Basically all I need it for is using Firefox, Thunderbird, Audacious, Google Chrome, an image viewer and some other programs from the Ubuntu apps directory such as Calibre to manage ebooks on my Kindle Paperwhite. If Lubuntu is missing more stuff thats installed with Xubuntu then I think thats ok I can install what I need.

---

### Post by carl4926 on 2013-08-09
> **Gilad_Pellaeon said:**
> Basically all I need it for is using Firefox, Thunderbird, Audacious, Google Chrome, an image viewer and some other programs from the Ubuntu apps directory such as Calibre to manage ebooks on my Kindle Paperwhite. If Lubuntu is missing more stuff thats installed with Xubuntu then I think thats ok I can install what I need.
Lubuntu / Xubuntu whatever
You can install either and get similar results. Lubuntu uses slightly less resources is what I mean

---

### Post by Mark Phelps on 2013-08-09
Problem with your space at present could be serious if the "C:" partition is nearly full.  Windows needs 20% or so free space to operate properly.  If you copy your data files into "C:" and that nearly fills it, that could prevent Windows from working.  

Also, combining the partitions is not really going to get you more free space, it's only going to put it in one partition.

---

### Post by Gilad_Pellaeon on 2013-08-09
For now I took the time this evening to setup Lubuntu 13.04 as an  exclusive on this tower. My fiance's machine will remain running Windows  XP if I absolutely have any desperate need to run a windows program  that bad if I decide not to setup WINE and or a VM. :)

---

### Post by carl4926 on 2013-08-10
> **Gilad_Pellaeon said:**
> For now I took the time this evening to setup Lubuntu 13.04 as an  exclusive on this tower. My fiance's machine will remain running Windows  XP if I absolutely have any desperate need to run a windows program  that bad if I decide not to setup WINE and or a VM. :)
I like it when people make intelligent decisions

---

