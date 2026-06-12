---
title: "Linux rescources / mounting Win Partition"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by TTN on 2006-05-18
Hello,
     I have searched for an answer and read the how to's, but I did not find the answer I am looking for. 
My dual boot Breezy is working just fine. 10 GB HD partitioned in half.
However I am running out of partition space for Breezy. 
I installed Baobab to find where it had gone and it shows my mounted Win partition in Media taking half of my Breezy partition space.

Question 1 is am I supposed to loose HD space when I mount the Win partition?

Question 2 is there another way to access the Win files without such a hit on my Breezy rescoures?

Thank you

---

### Post by gerbman on 2006-05-18
[QUOTE=TTN]Hello,
     I have searched for an answer and read the how to's, but I did not find the answer I am looking for. 
My dual boot Breezy is working just fine. 10 GB HD partitioned in half.
However I am running out of partition space for Breezy. 
I installed Baobab to find where it had gone and it shows my mounted Win partition in Media taking half of my Breezy partition space.

Question 1 is am I supposed to loose HD space when I mount the Win partition?

Question 2 is there another way to access the Win files without such a hit on my Breezy rescoures?

Thank you[/QUOTE]
Partition sizes will not change unless you change them. You split the 10GB HD in half, so Ubuntu will never have more than 5GB for its own use. This value should not change when you mount the Windows partition. If you used FAT32 for the Windows filesystem, then you can write to the other partition from Ubuntu, borrowing some of the space. However, if you used the NTFS filesystem for Windows, then I'm afraid you're stuck with 5GB of writable disk space for Ubuntu. Hope that makes sense.

---

### Post by TTN on 2006-05-18
I am sorry I did not phrase the questions right.

I don't have an issue with the partition size.

The issue is the space on my Ubuntu partition being used for mounting the Win partition.

If I read the Boabab report correctly Ubuntu is using 2.8 GB to "mount the Win partition"

---

### Post by gerbman on 2006-05-18
[QUOTE=TTN]I am sorry I did not phrase the questions right.

I don't have an issue with the partition size.

The issue is the space on my Ubuntu partition being used for mounting the Win partition.

If I read the Boabab report correctly Ubuntu is using 2.8 GB to "mount the Win partition"[/QUOTE]Space on the Ubuntu partition isn't being used to mount the Windows partition, Baobab just makes it look like that. Try going to "Preferences" and unchecking the Windows partition. This should give you more accurate figures for disk usage on your Ubuntu partition.

---

### Post by TTN on 2006-05-18
Thank you Gerbman,
      After looking the data over and over I see:
1. that Boabab increased the reported size of the Ubuntu partition by 2.8 GB then
2. shows the Win partition using the 2.8 GB.

with a net effect on the real Ubuntu partition of zero

I guess the over all lesson is if an OS does the job of Win it takes the same space as Win. 

No such thing as a free lunch.

Thanks again.

---

### Post by gerbman on 2006-05-18
[QUOTE=TTN]Thank you Gerbman,
      After looking the data over and over I see:
1. that Boabab increased the reported size of the Ubuntu partition by 2.8 GB then
2. shows the Win partition using the 2.8 GB.

with a net effect on the real Ubuntu partition of zero

I guess the over all lesson is if an OS does the job of Win it takes the same space as Win. 

No such thing as a free lunch.

Thanks again.[/QUOTE]
You're welcome.

---

