---
title: "installing 8.04 over existing ubuntu"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by yon2501 on 2008-06-10
ok so i have/had a partitioned ubuntu/windows system windows decided to break down completely so i had to reinstall i reinstalled it on the partition that it was originally on, but for some reason i cannot boot to the ubuntu partition now because grub wont start. so i decided to redownload ubuntu 8.04, burn it to disc and reinstall over the existing ubuntu partition since i have everything backed up on an external hd anyway. the prblem is that for some reason the ubuntu installer isnt detecting my current partitions and wants to install over all my windows stuff as well as the ubuntu.

---

### Post by Pumalite on 2008-06-10
You have to go Manual and point to the right partitions.

---

### Post by yon2501 on 2008-06-10
yes i know thats the normal method but it ignores the partitions and lumps them all to the full disc space.

---

### Post by Pumalite on 2008-06-10
Post a screenshot of gparted

---

### Post by yon2501 on 2008-06-10
heres the screen of the manual portioning window
[IMG]http://i168.photobucket.com/albums/u198/yon2501_pics/Screenshot.png[/IMG]

---

### Post by avtolle on 2008-06-10
Before we get too far along here, on the downloaded iso, did you check the md5sum of the file before burning it to disk?

---

### Post by Pumalite on 2008-06-10
Checking the disk is a fine idea, but post a screenshot that shows the drive and its partitions or the lack of them.

---

### Post by yon2501 on 2008-06-10
you mean from the add new partition menu? because that screenshot is all of it its just showing the drive as a whole without the existing partitions at all.

---

### Post by Pumalite on 2008-06-10
You could try checking this thing with Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Post screenshot

---

### Post by yon2501 on 2008-06-10
ok so i downloaded it and burned it to a disc but honestly i dont really know what to do when i boot from the disc.

---

### Post by Pumalite on 2008-06-10
If the default boot doesn't work; try 'force-vesa'
Better even; make sure you download version: gparted-Live-0.3.7.iso

---

### Post by yon2501 on 2008-06-10
i dont see that version of the iso on the download page only the tar.bz2 veresion.

---

### Post by Pumalite on 2008-06-10
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by yon2501 on 2008-06-11
ok so that method wasnt working for me at all so i decided to try something else. im following [this]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") guide but when i get to the partitioning portion of the install i get an error now.

at least im getting the propper partitioning screen now
[http://i168.photobucket.com/albums/u198/yon2501_pics/Screenshot-1.png]("http://i168.photobucket.com/albums/u198/yon2501_pics/Screenshot-1.png")

but when ive selected the partitions i want to create i get this error message after it attempts to make them
[http://i168.photobucket.com/albums/u198/yon2501_pics/Screenshot-1-1.png]("http://i168.photobucket.com/albums/u198/yon2501_pics/Screenshot-1-1.png")

then it leads me to the manual partitioning window which is a pain for someone like me whos new to this
[http://i168.photobucket.com/albums/u198/yon2501_pics/Screenshot-2.png]("http://i168.photobucket.com/albums/u198/yon2501_pics/Screenshot-2.png")
at this screen i tried to manually resize and still got the same error message

---

### Post by Pumalite on 2008-06-11
What problem did you have with the iso I pointed out to you?
What are you trying to resize? I thought you wanted to install on top of the old one.

---

### Post by yon2501 on 2008-06-11
well that method wasnt working for me so i tried to remember what method i used the first time i dual booted. so i re-re-installed windows and formatted and partitioned with that and huzza it worked ive just been to busy to label this as solved-ish

---

### Post by Pumalite on 2008-06-11
Glad you got it to work.

---

