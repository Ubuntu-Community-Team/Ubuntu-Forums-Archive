---
title: "Install over Win 8.1"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by eipapp on 2014-07-27
I'm trying to install Ubuntu 14.04 in place of Win 8.1, NOT dual boot but in place of. During the installation process, however, I get a message "No operating system" detected. 
I don't understand why Ubuntu does not recognize my Win 8.1 OS so was afraid to continue. What can I do to properly install Ubuntu in place of my current
Windows OS so as not to screw up my machine?
Any and all help/suggestions appreciated.

Thanks,
Bruce

---

### Post by Bucky Ball on 2014-07-27
Boot to a desktop from a LiveDVD/USB (choosing the option 'Try Ubuntu'). Once there, launch Gparted. Do you see your Windows partition? Right click, unmount, delete. Go back to the desktop and hit the install icon.

---

### Post by eipapp on 2014-07-27
Sounds simple enough. I'll give it a go and let you know how I make out.

Thanks !!

---

### Post by eipapp on 2014-07-27
Thanks, Bucky, it worked like a charm.

Bruce

---

### Post by oldfred on 2014-07-27
What system and model?

Ubuntu often does not correctly see Windows 8 as it may be hibernated with the fast boot or needs chkdsk. And for many users it overwrites the entire hard drive including recovery partitions.
So best to make a full backup of your Windows install. We get many users who have one application or game that only works in Windows or later want to reinstall Windows to sell system. Only the vendors OEM version will work with your Windows product key which is not embedded in your UEFI.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And always best to use Something Else if you do not want to totally erase entire hard drive.
      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by Bucky Ball on 2014-07-27
Excellent news! Please mark the thread as solved to help others by following the second link in my signature. ;)

---

### Post by Bucky Ball on 2014-07-27
Excellent news! Please mark the thread as solved to help others by following the second link in my signature. ;)

PS: oldfred makes some very valid points which I didn't. Worth a read, even though after the fact.

---

