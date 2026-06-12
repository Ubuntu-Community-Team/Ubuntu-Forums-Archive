---
title: "Partition plan ... advice please?"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by Pai on 2007-03-06
I've been running Dapper for the past month (as my first Linux experience), and have decided that I would like to move to a combination of Edgy and XP.

I was planning on having the following six partitions, in order,  on my 232 GB drive:

(*Name | file format | desired size*)
1.) XP | ntfs | *Size?*
2.) Swap | - | 1 GB
3.) /(root) | ext3 | *Size?*
4.) /home | ext3 | *Size?*
5.) Shared | fat32 | 80 GB
6.) DellRestore | vfat | 3.85 GB ("Hidden partition" which simply contains an image of XP for reinstallation. Dell refuses to supply me with a hard copy of XP, so at the moment I'd like to keep this here)

Before I move on, are there any other partitions you think I absolutely should include?

Continuing... Two issues I have with the above layout:

a.) I understand that four primary partitions is the limit. I have never created an extended partition, but I assume that is what I will have to do to accommodate the above needs. Am I sacrificing any functionality by using extended partitions? And, of the above 6 how do you recommend that I group them? I was thinking about having the swap, /, and home all grouped together, but I don't know if that is the best approach, or if you can even put three sub-partitions within one. I'm definitely open to any other suggestions.

b.) What sizes would you recommend for the ones I left blank? I've got roughly 150 GB to divvy up between XP, /, and home. What would you do? I do plan on using Edgy as my primary OS, but I will be using XP for occasional gaming, and platform exclusive programs such iTunes and PS (I know Gimp is all I need, don't tell me that!). My biggest concern is how much room XP really needs for optimal performance.   I have a pretty good idea of what size root and home should be, but that will likely change depending on how much room I need to dedicate to XP.

The continued support is greatly appreciated.
-Pai

---

### Post by Dr. Nick on 2007-03-06
80 gig fat32 is going to be a issue I think, I have a shared ext3 partition and use 
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) to see it from windows

YOu will need to use extended partitions aswell, not functionality lost really.

Fat32 has size limits on the partition and files within. file liit is about 4 gig. ext3 doesnt have that issue

---

### Post by hardyn on 2007-03-06
i do exactly as you have proposed, and it works great!

although i have the shared partition touching both the my /boot and /home patition and the XP partition, eg:

|--NTFS 50GB--|--FAT32 50GB--|--EXT3 15GB--|--swap 1gb--|

works really well, no problems. 

I used fat32 as the shared, as i never have a file over 4gb, even if i do, have ntfs and ext3; and i wanted native access to the shared drive from windows, in case something went wrong and i had to perform some emergency recovery.

---

### Post by confused57 on 2007-03-06
Here's a thread with someone who had a similar question:
[http://www.ubuntuforums.org/showthread.php?t=373955](http://www.ubuntuforums.org/showthread.php?t=373955)

---

### Post by Pai on 2007-03-06
> **Dr. Nick said:**
> 80 gig fat32 is going to be a issue I think, I have a shared ext3 partition and use 
Fat32 has size limits on the partition and files within. file liit is about 4 gig. ext3 doesnt have that issue
I've looked into the Windows support for writing to ext3, which is intriguing, but based on my usage I think I am more comfortable using a shared fat32. I am aware of the general limitations/drawbacks of that file format, which is why I have generally avoided it in the past, however, at this time I think it's the best route for me. I don't dabble in any sort of video ripping/editing, so I highly doubt I'll encounter any files even close to 4 gb that I need to share between each OS.

Anyway, based on the other comments (Much thanks confused57, GeertPoels), here is what I'm now thinking:

(*Name | file format | desired size*)
1.) XP | ntfs | 60 GB
2.) Swap | - | 1 GB
3.) /(root) | ext3 | 25 GB
4.) /home | ext3 | 65 GB
5.) Shared | fat32 | 75 GB
6.) DellRestore | vfat | 3.85 GB ("Hidden partition" which simply contains an image of XP for reinstallation. Dell refuses to supply me with a hard copy of XP, so at the moment I'd like to keep this here)

Comments, suggestions?

The extended partition question still stands.

Thanks again.

---

### Post by Kara Denizi on 2007-03-06
I'm new to this also but on my 200GB notebook I currently have Windows Media Center plus five Linux distros.  Since I had plenty of room I allocated (actually over-allocated) 2GB for a Linux Swap partition and 20GB for each Linux distro (10GB for root (/) and 10GB for /home).  Unlike you I didn't try to make an interface as such with Window files. 

For the first four Linux distros the bootloader was installed in the root partition for that distro.  On the last distro (which for me was Ubuntu 6.10) I installed the bootloader in the MBR (Master Boot Record). 

If I wished to have Windows and only one Linux distro, I'd make one of my primary partitions a 22GB extended partition.  I'd divide that space into three logical partitions as follows:  2GB for swap, 10GB for root (/), and 10GB for /home.  I'd install that distro's bootloader in the MBR.

Again, I'm new to all this so, like you, I'll listen respectfully to the advice of those more knowledgeable and experienced to correct my thinking on the above.  However, using the method noted above, I am able to successfully use both Windows and each of the five Linux distros I'm interested in. 

In respect to your query on how much room to leave for Windows, I'd suggest leaving everything or most everything you don't plan to use in support of your Linux distro or distros for Windows.

---

### Post by GeertPoels on 2007-03-06
If concerned about security, you can consider going into a more detailed partitioning.

Where /boot and /tmp are in different partitions.
[http://www.linuxsa.org.au/tips/disk-partitioning.html](http://www.linuxsa.org.au/tips/disk-partitioning.html)

You could also consider to not put your documents in /home as it also gets filled with various settings from Ubuntu. You might or might not like to mix your docs, music, whatever with these settings.
You have 100GB for home and 80GB shared.
If the shared is just a passthrough, than that's quite a lot.
If you like to share all your music, docs, etc. between the two of them, then /home probably requires far less.

About XP's size : I think especially the games make the difference here. 
With some of them requiring multiple Gigabytes.

---

