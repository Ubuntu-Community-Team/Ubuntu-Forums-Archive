---
title: "Last questions before installing 9.10"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2009-12-26
Last questions before installing Ubuntu 9.10.

1) The LIVE CD boots ok, and when in Ubuntu I can still access to my Windows XP file system. Will I still access it after installing and partitioning the HD?

2) I hope not to need it, but just in case I need to undo the installation, will it work? I mean, will it be possible to delete the partition and have the HD again as a Windows XP disk?

Thanks
Robert

---

### Post by taurus on 2009-12-26
Yes to both questions.

---

### Post by underquark on 2009-12-26
Before re-partitioning and installing, best to move all your Windows programs and data to the bottom end of the disk by disabling the Page File and defragging the disk.

From within Windows, goto Control Panel... Performance and Maintenance...System...Advanced (tab)...Performance...Settings(button)...Advanced...Virtual memory...Change(button) and select "No Paging File".  This stops Windows from using a fixed chunk of the disk (usually inconveniently-placed) as a page file (swap file).  Then goto My Computer, right-click on the drive in question and choose Properties...Tools...Defragment Now.

You can now boot into the ubunutu live CD and choose to install.  I'd leave the Windows partition with maybe 75% used/25% free but it depends on your disk size and intended use.  If you use Windows frequently then leave a bit more space (and re-enable the Page File).  You can swap things around later once you become used to ubuntu.

---

### Post by rva1945 on 2009-12-26
> **taurus said:**
> Yes to both questions.

My HD is 80GB size. WXP currently uses 40GB.

What ratio of partitioning do you suggest?

---

### Post by taurus on 2009-12-26
20GB should be plenty for Ubuntu unless you plan to download a bunch of big stuff.

---

### Post by Shazaam on 2009-12-26
To add to what underquark posted you can also delete all but the most recent Restore Point in Windows XP before defragmenting. The Restore points are usually marked as "Unmovable" (green bars) in Windows Disk Defragmenter.

---

### Post by rva1945 on 2009-12-26
> **taurus said:**
> 20GB should be plenty for Ubuntu unless you plan to download a bunch of big stuff.

What is big stuff in Ubuntu? My only big stuff are vids, which will remain in Windows file system.

---

### Post by taurus on 2009-12-26
Movies, music, etc.

If you leave everything in windows, than 10G should be even more than enough.

---

### Post by rva1945 on 2009-12-26
> **taurus said:**
> movies, music, etc.

If you leave everything in windows, than 10g should be even more than enough.


t h a n k s   m a n !!

---

### Post by rva1945 on 2009-12-26
> **taurus said:**
> Movies, music, etc.

If you leave everything in windows, than 10G should be even more than enough.

My last question and then t install Ubuntu 9.10:

My Windows XP file system is NTFS, no problems with partitioning?

---

### Post by nerdtron on 2009-12-26
Yes! Just make a small partition for Ubuntu (10GB perhaps?) and install it there. From within Ubuntu, you can mount your NTFS partitions and you can read/write to those drives with ease.
If after installing ubuntu, you can't read/write to your Windlose partitions you can try using the NTFS Configuration. I installed it using synaptic....
Try Ubuntu and be free!

---

