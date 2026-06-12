---
title: "Ubuntu installed on the wrong disk"
date: 2019-02-16
forum: Installation &amp; Upgrades
---

### Post by anll on 2019-02-16
Hi everyone, 

I have successfully installed Ubuntu on my new computer (Lenovo 330S). Unfortunately, I installed it on the 16G Optane disk instead of the HDD. I wanted to remove Windows completely (I don't need it) but now, I have Windows on the 1T HDD and Ubuntu on the small disk. I am unsure about the best way to end up with Ubuntu on the HDD and nothing on the Octane. I tried to get info on how to remove Ubuntu and reinstall it but the threads I find are about removing Ubuntu by installing back Windows, which is not applicable in my case.
Any help is welcome!

Thanks,

---

### Post by jeremy31 on 2019-02-16
Boot up the install media, try without installing, open gparted and delete the partitions on Optane

---

### Post by anll on 2019-02-16
I am sorry, I am not familiar at all with this, could you explain it more in detail please?

---

### Post by yancek on 2019-02-16
Use the Ubuntu installation DVD/USB.  When it has booted to the desktop, open gparted from a terminal.  You should see a GUI with the drive/partition information.  Make sure you select the correct partition on the correct device in the main window then click on the Partition tab at the top and move the mouse down to Delete in the drop down menu.  Click the Apply check mark at the top to apply the changes.  The link below is to the GParted Manual which has very detailed instructions on this and other partitioning processes.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by oldfred on 2019-02-16
If deleting Windows the Octane SSD will not be used. It was only used for boot of Windows.
It will actually make Ubuntu much faster.
But it is small, so you want just your / partition, but not /home on the Octane and have all your data on the HDD.

You can use gparted to delete partitions and create a new ext4 formatted partition for /home.
Detailed instructions.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 
    
Gparted is on the Ubuntu live installer or you can create a gparted live system separately. 
       [http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php) 
            Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
[https://gparted.org/news.php](https://gparted.org/news.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by anll on 2019-02-20
Thank you all for your help. I could not do the last suggestion because I discovered that Linus does not deal with ntfs, which took the whole HDD. This explains also why I wasn't unable to install Linux on the HDD disk in the first place, so I removed totally Windows with Gparted and reinstalled everything on the HDD disk.

---

