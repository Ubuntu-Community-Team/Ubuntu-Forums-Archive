---
title: "Hard Disk Recovery  1TB - 2 Partitions - [NTFS] - former Win7 Installation"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by newbuntusan on 2012-03-19
My hard disk cannot be mounted under ubuntu and i dont know what to do.
I would format it, but i want to backup my data to an external usb drive first but cant manage to access the partitions. what's the problem?

[http://imageshack.us/photo/my-images/801/screenshotat20120319123.png/](http://imageshack.us/photo/my-images/801/screenshotat20120319123.png/)
[http://imageshack.us/photo/my-images/822/screenshotat20120319123.png/](http://imageshack.us/photo/my-images/822/screenshotat20120319123.png/)
[http://imageshack.us/photo/my-images/192/screenshotat20120319124.png/](http://imageshack.us/photo/my-images/192/screenshotat20120319124.png/)
[http://imageshack.us/photo/my-images/546/screenshotat20120319124.png/](http://imageshack.us/photo/my-images/546/screenshotat20120319124.png/)

What could i do?
I tried to use the "SMART Data" Button that says: View SMART data and run self-tests, but when i open it and click on "Run self test" it always tells me "Hard Disk Problem Detected - A hard disk is reporting health problems" :-(

Is it possible to recover any of my data? What could i do?
Currently, all i have is bootable ubuntu on an USB Stick and an empty external usb drive that i can mount.

---

### Post by ajgreeny on 2012-03-19
It is impossible for me to see anything on your images clearly enough to give you any meaningful answers.

However, I would suggest that it probably needs a windows system to repair the partitions as they have come from a windows environment, rather than trying to use something from a live ubuntu system.

---

### Post by oldfred on 2012-03-19
I have had disk drives fail, fortunately I was able to back up most of my data before total failure.

Your is the first that I have seen Smart Data report:
[COLOR=Red]Disk  failure is imminent.[/COLOR] 

I do not think reformatting will help.

You can try the recovery tools but chances are not good.

You can try testdisk and see it it sees any files.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by Mark Phelps on 2012-03-19
Agree with oldfred that it doesn't look good ... but if you have access to an MS Windows PC and want to try to use MS Windows utilities to recover the data, then read on ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

There's also a FREE MS Windows file system recovery app known as Recuva.  You could try that first -- but my experience in MS Windows is you get what you pay for.

Your data ... your money ... your choice.

---

