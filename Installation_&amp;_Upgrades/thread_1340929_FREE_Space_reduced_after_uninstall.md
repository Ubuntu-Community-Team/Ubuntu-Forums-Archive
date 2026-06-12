---
title: "FREE Space reduced after uninstall"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by GeorgeOfTheBush on 2009-11-29
I had a total of 33 GB free space on my PC with win xp. There is only ONE partition on my pc (C: - 80 GB) which runs win xp. 

I installed Ubuntu 9.10 through wubi allocating 20 GB for Ubuntu. Because of a problem with ubuntu (grub error), I decided to uninstall ubuntu through wubi's uninstaller. But it didn't work. So I used another program [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe) and uninstalled ubuntu. I expected the free space on c drive to come back to 33 gb. But it shows only 13 gb as free space.

How do I recover the space that I have lost so that I could install Ubuntu again. Any suggestions would be very helpful.

Thanks.

---

### Post by Bunnybugs on 2009-11-29
> **GeorgeOfTheBush said:**
> I had a total of 33 GB free space on my PC with win xp. There is only ONE partition on my pc (C: - 80 GB) which runs win xp. 

I installed Ubuntu 9.10 through wubi allocating 20 GB for Ubuntu. Because of a problem with ubuntu (grub error), I decided to uninstall ubuntu through wubi's uninstaller. But it didn't work. So I used another program [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe) and uninstalled ubuntu. I expected the free space on c drive to come back to 33 gb. But it shows only 13 gb as free space.

How do I recover the space that I have lost so that I could install Ubuntu again. Any suggestions would be very helpful.

Thanks.


As far as I know, there is still a folder with Ubuntu files, Ubuntu keeps the Harddisk file available if you reinstall... Just go to the file-folder, and remove all the data there manually! (Maybe reboot our computer, because 20GB is a lot!)

---

### Post by Dinodoc on 2009-11-29
Not sure if this applies but I seem to remember a while back using a vmware product I think, when you set a "partition" size for the new install it created a file of that size where everything was installed.  Even if actual installed files was only say 1/3 the size. This I am guessing was to ensure that the virtual os would always have that set partition size available.  

Its possible it maybe be a file or directory on windows that contains a blank file to fill the required space or possibly all the data required is stored in one file and then inflated to max partition size.

Maybe something in this thread might help, talks about moving wubi installs to a real partition, maybe somewhere in there shows where the wubi install stores the files.

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by Dinodoc on 2009-11-29
I also see on a link from the thread i just gave you:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

At the very bottom it shows what appears to be a picture of an explorer window showing the Virtual.Disk files, I think this may be what I was referring too.

[http://lubi.sourceforge.net/lvpm-screenshots/resize/3.png](http://lubi.sourceforge.net/lvpm-screenshots/resize/3.png)

Edit: Found this in the thread - *c:\wubi\disks* - try there, I am guessing the virtual disks are there.

---

### Post by GeorgeOfTheBush on 2009-11-29
Thanks a lot Bunnybugs & DinoDoc.

I am still unable to locate the 20GB file that wubi must have created during the installation of ubuntu. Any suggestions? I only have the .iso file used for the installation of ubuntu 9.10.

---

### Post by GeorgeOfTheBush on 2009-11-29
Just ran Windows Disk Defragmenter. Once it finished, the report mentioned about some files that were not defragmented. One of them was the 20 GB file along with its location (C:\found.000\something). I must mention that my searches did not reveal this file.
Just deleted the file from the above location. **Got back my 20 GB!**

Thanks for all your help.

---

