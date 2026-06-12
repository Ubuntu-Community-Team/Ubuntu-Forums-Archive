---
title: "How to reinstall"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by Rattleh2c on 2011-09-01
Ok hello I set up a dual boot ( dual partition )some time ago forgot the password tried in vain to reset it .Now I want to delete ubunto and reinstall it on the same  partition not the vista one .Just to clarify Ive got vista on one partition and ubunto 11.4 on another :confused: I no the solution maybe simple  but I dont want to screw this up Thanks

---

### Post by dino99 on 2011-09-01
how i do it:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by ajgreeny on 2011-09-01
> **Rattleh2c said:**
> Ok hello I set up a dual boot ( dual partition )some time ago forgot the password tried in vain to reset it .Now I want to delete ubunto and reinstall it on the same  partition not the vista one .Just to clarify Ive got vista on one partition and ubunto 11.4 on another :confused: I no the solution maybe simple  but I dont want to screw this up Thanks
Firstly, how did you try to reset your password; it is usually a very simple job:-
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If that does not do what you want, there could be other problems with the installation, so to reinstall the system, just use the normal method up to the disk preparation stage, and then choose "Something else", which is manual partitioning.  You should be able to pick out your current ubuntu partitions (/  and swap?) and choose to install to them again.

You might also like to think about a separate /home partition, which makes life so much easier should you need to reinstall again.
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by Bucky Ball on 2011-09-01
> **ajgreeny said:**
> 

you might also like to think about a separate /home partition, which makes life so much easier should you need to reinstall again.
[separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

+1

---

### Post by Oxwivi on 2011-09-01
If I understand you right, you simply want to know to install in the correct partition.

You can make sure using GParted Partition Editor utility that you can find on the live CD/USB.

Open GParted and a window similar to this one (with the defualt Ubuntu theme) will greet you:

[IMG]http://gparted.sourceforge.net/screens/gparted_1_big.png[/IMG]

Under the File System column you can see the partition format. Your Vista will be installed in the partition with the NTFS file system and the one with ext4 will have Ubuntu. The Partition column will tell you the directory of the partition.

You can simply choose Erase and reinstall Ubuntu option (the screenshot does not show this, but the installer will detect multiple operating systems and appear in your case), but if you do not trust it choose Manual Configuration (Advanced):

[IMG]https://docs.google.com/a/canonical.com/File?id=d4xsvkn_27fbzzwbfp_b[/IMG]

And make sure that that Ubuntu is installed in the correct partition which you found using GParted.

[IMG]http://3.bp.blogspot.com/-5iRCbU3xtBM/TVga3e1BNzI/AAAAAAAAAFg/-GQLXslrd0o/s1600/partitioner6.png[/IMG]

Choosing the correct partition, you need to press the Change button the choose the mount point as / like the above screenshot shows. The ext4 partition with the mount point specified as /.

---

### Post by cipherboy_loc on 2011-09-01
Nice tutorial, Oxwivi. Just thought I would mention that before you begin, you should first do a complete backup. 


Cipherboy

---

### Post by Rattleh2c on 2011-09-01
Ok thought I would give changing my password one more go .So I rebooted selected recovery mode then selected drop to root shell.
At the bottom of the screen it had  " Enter root password for maintenance " so how do I proceed from there to reset my password and hopefully not having reinstall .Thanks for all the help am trying the easiest option first .

---

### Post by cipherboy_loc on 2011-09-01
If you did not set a root password, it should accept leaving the password blank (aka hitting enter). From there you type:

```

passwd (username)

```

where (username) is your username.



Cipherboy

---

### Post by Rattleh2c on 2011-09-01
Ok ill give that a try then I,ve got to go out so ill be silent for a while

---

### Post by Rattleh2c on 2011-09-01
Ok tried that didnt work eventually It allowed me to changed my unix password,  but could not use it to log into ubunto I kept typing passwd then was prompted for a new password which I typed on repeating this password it rejected it so in the end I typed passwd space then my password like this "passwd ***** " this I repeated it and was told unix password changed .

---

### Post by Bucky Ball on 2011-09-01
Then your password is now probaby 'passwd *****'.

---

### Post by Rattleh2c on 2011-09-02
Ok tried passwd ***** didn,t work so deleted and reinstalled from wubi disc ubunto 11.04 i38.
Installed rebooted and removed disc as directed simple but up came a warning which ststed

(/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

I clicked on the close box and up came the log in screen with this message in the top right corner 

Configuration default for GNOME Power Manager have not been installed correctly contact your computer administrator

What do I do download another copy of ubunto ?:confused:

---

### Post by ajgreeny on 2011-09-02
> **Rattleh2c said:**
> Ok tried passwd ***** didn,t work so deleted and reinstalled from wubi disc ubunto 11.04 i38.
Installed rebooted and removed disc as directed simple but up came a warning which ststed

(/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

I clicked on the close box and up came the log in screen with this message in the top right corner 

Configuration default for GNOME Power Manager have not been installed correctly contact your computer administrator

What do I do download another copy of ubunto ?:confused:
It certainly could be that the iso file you downloaded was a bad one, so check the iso md5sum, which you can find at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") with yours.  If you're not sure how to do that have a look at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that matches correctly, just burn it again at as slow a speed as possible, and try installing again.

---

### Post by Bucky Ball on 2011-09-03
Mate, avoid a wubi install. Download (or better still, torrent) the desktop ISO, burn a disk, boot from it, install Ubuntu, arrange and create the partitions how you want (but leave Windows alone), and you're done. Wubi install are  known to be problematic at times.

I would start with 10.04 LTS (the current, stable long term support release). Either way, boot from the disk first and 'Try Ubuntu' and see how the release works. Good luck. Avoid Wubi install. ;)

---

