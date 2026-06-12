---
title: "Can't download xubuntu 18.04 to other than home partition"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2018-05-13
I have partitioned my system to have a small partition for the OS and a large partition for data.  My OS (home) partition is too small to contain xubuntu 18.04 and I can't find a way to download to another partition.  Apparently both the Torrent download and the mirror downloads are set to download to the home partition.  Once I click on the download they begin downloading immediately and don't allow me to change the destination to another partition (or even to another folder).

Can somebody tell me how I can download xubuntu 18.04 to other than the home partition (folder)????  Any help appreciated......

---

### Post by Ralph L on 2018-05-13
I found the reason that I couldn't change the "Save" location for the mirror downloads.  It was Privacy Manager.  I disabled it for the download website and then I could change the download target partition (folder).  However, I still can't get Torrent to allow me to change the target of the download to other than the home folder.
Any thoughts on how to change that?????????

---

### Post by oldos2er on 2018-05-13
Which torrent client are you using?

---

### Post by Ralph L on 2018-05-13
Thanks for the response.
I just double click on the 64 bit torrent button in [https://xubuntu.org/download](https://xubuntu.org/download).  Then I either execute the Torrent program directly, or I save it to a folder on my Data Partition and double click it there for execution.  Either way it immediately begins the torrent download to my home partition, preventing me from changing the download destination.

---

### Post by kc1di on 2018-05-13
I assume your using transmission as that is the one that come by default in xubuntu. 
If so they you need to tell it where you want it to download to.  You do that by edit tab then preferences then download tab about half way down that menu you'll find a dropdown box with allows you to select the folder you want to save the files in.  It is defaulted to Downloads which is normally found in your home folder. If you want you use a different folder you'll have to choose it in preferences.

---

### Post by Ralph L on 2018-05-13
Thanks to you guy for responding. I really appreciate it!!

kc1di:  Your instructions fixed my problem.  I didn't know that Transmission was a program on my computer.  I thought it was part of what I downloaded, when I clicked on the website Torrent download.  Now that I understand what's going on I followed your instructions, initiated Transmission from the Whiskers Menu, and set the default Torrent download target to Downloads (on my Data Partition).  Then I clicked on the xubuntu website download button, and everything worked.

Thanks again.

---

### Post by kc1di on 2018-05-13
your Welcome Hope you enjoy xubuntu :)

---

