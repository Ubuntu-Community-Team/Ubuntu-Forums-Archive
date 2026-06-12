---
title: "xubuntu install files question + dualboot question"
date: 2015-08-14
forum: Installation &amp; Upgrades
---

### Post by peter203 on 2015-08-14
hello, I was thinking to try a dualboot but once I was on the download page of xubuntu I noticed some files I dont know much about, could you please explain me these and wether I need to download them too or not. 

here is the link: [http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/xubuntu/releases/14.04/release/](http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/xubuntu/releases/14.04/release/)

I wonder what are last 4 files, that is : 
 [xubuntu-14.04.3-desktop-i386.iso.zsync]("http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/xubuntu/releases/14.04/release/xubuntu-14.04.3-desktop-i386.iso.zsync")        
[IMG]http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/cdicons/list.png[/IMG] [xubuntu-14.04.3-desktop-i386.list]("http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/xubuntu/releases/14.04/release/xubuntu-14.04.3-desktop-i386.list")             
[IMG]http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/cdicons/list.png[/IMG] [xubuntu-14.04.3-desktop-i386.manifest]("http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/xubuntu/releases/14.04/release/xubuntu-14.04.3-desktop-i386.manifest")        
[IMG]http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/cdicons/torrent.png[/IMG] [xubuntu-14.04.3-desktop-i386.metalink]("http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/xubuntu/releases/14.04/release/xubuntu-14.04.3-desktop-i386.metalink")   

do I need them or I should just get the first one for version 14.04.3 

Additionally  I would like to know many years there's support for this one I read the previous was 3 years.

Lastly do I need to do some HDD change (partition change in windows) before I do the dualboot or does the xubuntu/ubuntu installation makes it automatically?

thanks a lot

---

### Post by yancek on 2015-08-14
The only file you need is the one with the .iso extension.  If you have 64-bit capable hardware, you can use either the amd64.iso or the i386.iso.  I you have 32 bit hardware, you can only use the i386.iso.  The Xubuntu home page at the link below indicates 3 years support.

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

> Lastly do I need to do some HDD change (partition change in windows)  before I do the dualboot or does the xubuntu/ubuntu installation makes  it automatically?
thanks a lot

That depends.  You indicate you have some version of windows but neglect to mention which one.  Makes a big difference.  Also, is your winodws install taking up the entire hard drive or do you have more than one hard drive.  If it is just one drive and the windows install is taking up all the space, you would be best off shrinking from Disk Management in windows which should be available if you have a newer windows release.  Best to post more info so someone can give you more specific advice.

---

### Post by peter203 on 2015-08-14
Its just one drive, windows takes about 60GB of drive (250GB total), I have seen posibility to go with 'dualboot' option during installation, would this make the trick or do I have to bother with Disk Managment in windows?

perfect, thank you very much sir for your help! big thanks!

---

### Post by yancek on 2015-08-14
You didn't mention which windows, if you are using windows 8 or newer it adds complicating boot factors.  If you are using windows 7 or earlier it will be simpler.

 You will have the ability to shrink and modify/create partitions during the install but it is generally advised to shrink/modify windows partitions from inside windows.  After modifying the partition, you should reboot windows and it is also generally advised to run chkdsk from windows.  I

If you see the option to install "Alongside" windows, you can try that.  If something does go wrong, you won't know what it was.  Usually, it works though, just an option.

---

