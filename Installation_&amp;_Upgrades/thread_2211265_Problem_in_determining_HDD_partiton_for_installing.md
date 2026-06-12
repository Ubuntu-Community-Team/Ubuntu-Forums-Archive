---
title: "Problem in determining HDD partiton for installing ubuntu 13.10"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by Kartikey Kant on 2014-03-15
I have been trying to install Ubuntu 13.10 on my system along with windows 7.
In windows , I have a C drive(in which windows is installed) of 48.73 GB, a D drive of 283.42 GB and a H drive of 49.62 GB. i also have 2 unallocated space one of 101 MB and other one of 83.89 GB(in which I want to install Ubuntu 13.10).
When I install Ubuntu and select "something else" option in installation type the partition editor shows partitions sda1 of 105 MB (windows loader), sda2 of 52 GB and sda3 of 442 GB. I'm totally confused what is happening.:confused::confused: 
My total HDD space is 500 GB though some of it is unavailable.
please tell me what should I do?

---

### Post by manngaurav on 2014-03-15
Boot through the live usb and post the gparted screenshot., there is an app called screencshot in ubuntu itself i think.  

You may want to take a look at this thread , might help you...
[http://ubuntuforums.org/showthread.php?t=2154899](http://ubuntuforums.org/showthread.php?t=2154899)

---

### Post by Kartikey Kant on 2014-03-16
**Here is the first screenshot :**
[[IMG]http://s13.postimg.org/67sb3y6cn/Screenshot_from_2014_03_16_06_16_56.png[/IMG]]("http://postimage.org/")

[screen shot capture]("http://postimage.org/app.php")

**But after I saved this photo and then again opened gparted it shows:**

[[IMG]http://s9.postimg.org/upy59snrj/Screenshot_from_2014_03_16_07_02_42.png[/IMG]]("http://postimage.org/")
[screen capture freeware]("http://postimage.org/app.php")

I was resizing my partitions using disk management in windows to create unallocated space for Ubuntu.

**Here is a screen shot from disk management**

[[img]http://s14.postimg.org/4e09yq5pd/disk.jpg[/img]](http://postimg.org/image/i7omnryal/full/)
[screencapture](http://postimage.org/app.php)

---

### Post by manngaurav on 2014-03-16
It seems in windows you don't have any PRIMARY PARTITIONS. THE USUAL c drvie and d drive etc.
 
Also your type as dynamic seems very confusing to me. this should be how your drives be looking in windows.

[http://fud.community.services.support.microsoft.com/Fud/FileDownloadHandler.ashx?fid=167d5ac3-a94a-432c-8380-b8b68d973a47](http://fud.community.services.support.microsoft.com/Fud/FileDownloadHandler.ashx?fid=167d5ac3-a94a-432c-8380-b8b68d973a47)

i think you would have to back up all your data on the other drives , then delete all of them through diskmanagement. aprt from the (C:) drive. and then again create PRIMARY PARTITIONS through the unallocated space , and leave the remaining space UNALLOCATED FOR UBUNTU.

if you are able to do so then , again post the diskmanagent and gparted pics. good luck.

It's going to be a little cumbersome because you seem to have messed up with your hard-drive. if you take my word just install ubuntu on live usb in persistence mode and fool around. then you will be confident to let go of windows. I am a total noob too , whatever i know is from searching these forums and getting help from this great community. 
My ubuntu experience is of around 20 hours . haha :) and i have completely switched ot window now. good luck

---

### Post by westie457 on 2014-03-16
@[[COLOR=#000000]Kartikey Kant[/COLOR]]("http://ubuntuforums.org/member.php?u=1522577")
Your issue is worse than you think it is. Your hard drive has been converted to 'Dynamic' and now no OS can be installed to it. Windows will not install and neither will anything else.

Move all of your personal files to external media before doing anything.

There are a couple of things you can try to convert the hard drive back. **There are no guarantees that they will work**.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
[http://www.partitionwizard.com/convertpartition/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-dynamic-disk-to-basic-disk.html)

seem to offer the best chances.

If neither of these suggestions work then the only thing to do is to completely wipe the hard drive and give it a new partition table and reinstall everything.

Not an easy choice to make.

Hope this helps and good luck.

---

