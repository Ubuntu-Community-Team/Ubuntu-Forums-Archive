---
title: "&quot;Places&quot; Linked to a Separate Drive"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by Norway719 on 2013-10-22
Hello, All.


I really appreciate all the effort thatthis community puts forth. I have always found the answers toseemingly impossible questions here...(usually from a live discsession;)....) At any rate I have been dual booting Ubuntu andWindows 7 for several years now and I just wiped my Ubuntu partitionand installed Saucy from scratch. I have a partitioned SSD with boththe operating systems on it, and an internal storage HDD which holdsthe data that both OS's retrieve, (music, documents, downloads etc)In the past I have made the folders under “Places” in theUbuntu file browser (documents, downloads, music, pictures, videos)link directly to the folders on my storage drive instead of savingthem on the local disk. When its done correctly, it appears that thedata is stored on the local drive, but its actually on the commonstorage drive. In my previous setups, it has been as easy deletingthe things under “Places” and replacing them with the foldersfrom the storage drive, although since upgrading, it does not appear to work the same way.
I was wondering if anyone has done this and has figured out how it works.
The setup that I had before was based on the one made here: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
Below I have attached (maybe) a picture of the links that I am trying to make into the identically named folders on my storage drive.

This has been tough to articulate, and I realize that this hasn't been the best explanation and if it is unclear I'd be happy to try to explain it differently. I don't like to post questions that have already been addressed, but I've done my due diligence and I really can't find anything.
Thanks in advance for any help.

---

### Post by oldfred on 2013-10-22
There are two ways linking the folders or using bind in fstab for each folder. I use linking and link same data partitions into every install, but if networking and want to follow links from networked computer bind may work better.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[URL="http://ubuntuforums.org/showthread.php?t=2137726"]http://ubuntuforums.org/showthread.php?t=2137726
[/URL] Advantages of bind post 16 - Morbius1
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)

[URL="http://ubuntuforums.org/showthread.php?t=2137726"]
[/URL]

---

### Post by Norway719 on 2013-10-22
Its so easy! I'm so stupid! Thank you very much for your help, oldfred. All I needed to do was go to my storage drive, and make a link (shortcut) of all of my files; Music, Downloads, etc.. Then, move those shortcuts to my Home folder, and delete the ones that were already there, and finally, rename the shortcuts to exactly the names of the old folders; Video, Downloads etc...
Sorry for the stupid question and thank you for the rapid response.

---

