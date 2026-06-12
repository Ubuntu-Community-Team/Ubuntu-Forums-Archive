---
title: "Can't get virtual box on Lucid"
date: 2009-11-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by YosefKaro on 2009-11-20
I've tried a few different approaches to getting VB on Lucid but I keep running into errors like [this]("http://pastebin.ubuntu.com/323321/") from /var/log/vbox-install.log  I tried installing the the kernel sources that are being requested by VB by using sudo apt-get install linux-headers <kernel version (uname -r)> But that just gives me these errors: E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?  Is there a good alternative to VB or can I some how resolve this issue?  Thanks for reading this overly long post ;)

-Yos

---

### Post by jmmL on 2009-11-20
Well for starters the /var/lib/dpkg/lock errors just mean that somewhere else on your system, dpkg is being used, perhaps through apt-get, aptitude or synaptic. Close down anything that's installing packages (after you've checked it's okay to do so), and try re-installing.

How are you attempting to install? Using the repos or an external package? Try using aptitude if you're using apt-get - I've found it to be better when handling dependencies and suggestions.

---

### Post by plun on 2009-11-20
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

and don't use the crap from repo....

---

### Post by YosefKaro on 2009-11-20
Well, I have tried the repos, terminal and downloading the .deb file.  All of them are giving me pretty much the same error:

Setting up virtualbox-ose-source (3.0.8-dfsg-1ubuntu1) ...
Adding modules to DKMS build system
Doing initial module builds

Error! Your kernel source for kernel 2.6.32-4-generic-pae cannot be found at
/lib/modules/2.6.32-4-generic-pae/build or /lib/modules/2.6.32-4-generic-pae/source.
dpkg: error processing virtualbox-ose-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up virtualbox-ose-qt (3.0.8-dfsg-1ubuntu1) ...

Are you guys also on kernel 2.6.32-4-generic-pae ?

-Yos

---

### Post by plun on 2009-11-20
Yes and uninstall the OSE crap.....

then install the real thing.

---

### Post by jfernyhough on 2009-11-20
Have you installed the kernel headers for your kernel version?

Normally if something can't be found it's not installed...

---

### Post by VMC on 2009-11-20
> **plun said:**
> [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

and don't use the crap from repo....
Maybe that's my problem as well. I went the path of the repo. Now I'll try what you suggested.

Edit: That didn't work for some reason:

```
vmc@vmc-desktop:~$ wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
OK
vmc@vmc-desktop:~$ sudo aptitude install virtualbox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for virtualbox-3.0
No candidate version found for virtualbox-3.0
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

---

### Post by plun on 2009-11-20
Yep....  VB 3.0.12 (Karmic) up and running ChromeOS on Lucid....

[[img]http://ubuntu-pics.de/thumb/31589/snapshot23_nfdo1o.png[/img]](http://ubuntu-pics.de/bild/31589/snapshot23_nfdo1o.png)

The OSE version is just a  RMS mess...

---

### Post by cariboo on 2009-11-20
If you use aptitude to install virtualbox you get the open source version from the repository. I've been using the puel version from [VirtualBox]("http://www.virtualbox.org/wiki/Linux_Downloads"), for the last couple of years, I've never had a problem installing it. It even notifies you that there are updates available.

Installing it is a easy as double clicking it and letting gdebi pull in any missing dependencies.

---

### Post by YosefKaro on 2009-11-20
Ok, now VMware is giving me the same exact problems: saying that the kernel headers cannot be found.  These kernel headers are very important, apparently, in order for VM's to run.  So how can I get these needed kernel headers?

-Yos


Oh, and in answer to an earlier question, I did try to install these headers but 'they could not be found'.  Anyone else having problems ***_currently_*** installing a Virtual Machine on this kernel 2.6.32-4-generic-pae ?

---

### Post by jmmL on 2009-11-20
> **YosefKaro said:**
> Ok, now VMware is giving me the same exact problems: saying that the kernel headers cannot be found.  These kernel headers are very important, apparently, in order for VM's to run.  So how can I get these needed kernel headers?

-Yos
```
sudo aptitude install linux-headers-`uname -r`
```

---

### Post by YosefKaro on 2009-11-20
Yes, I tried that earlier, but this time it worked  :D  Now I'm running into a different problem with VB: apparently, it demands that I use a bootable CD/DVD or a floppy.  Why can't I just use the ISO that I have on my HDD ?  I had no problem doing this with Virtual PC.

-Yos


Could it be because the file is a .vmdk ext ?

---

### Post by jmmL on 2009-11-20
> **YosefKaro said:**
> Yes, I tried that earlier, but this time it worked  :D  Now I'm running into a different problem with VB: apparently, it demands that I use a bootable CD/DVD or a floppy.  Why can't I just use the ISO that I have on my HDD ?  I had no problem doing this with Virtual PC.

-Yos


Could it be because the file is a .vmdk ext ?

Are you trying out chromiumOS by any chance? :P
You're right - you can just use the vmdk.

Select the virtual machine. Go to settings > hard disk. Click on the icon of a folder with a green upwards chevron. Go to "add" and select the vmdk in the file browser. Afterwards, double check that the system is set to boot from the hard disk. Go back to the settings menu for the machine and select "system". Make sure "Hard Disk" is at the top of the list, and selected with a tick.

---

### Post by YosefKaro on 2009-11-20
Thanks a lot; now I am making progress. :D I just can't get passed the login screen of the Chrome OS even though I am using the correct password of 'chromeos'.  Looks like I may have to find a different ISO.

-Yos


Ah, now I see the problem: 'Network not connected and offline login fail'.  So some how, I have to get VB to see my internet connection which may not be so easy since I am using a broadband dongle.

---

### Post by jmmL on 2009-11-20
> **YosefKaro said:**
> Thanks a lot; now I am making progress. :D I just can't get passed the login screen of the Chrome OS even though I am using the correct password of 'chromeos'.  Looks like I may have to find a different ISO.

-Yos


Ah, now I see the problem: 'Network not connected and offline login fail'.  So some how, I have to get VB to see my internet connection which may not be so easy since I am using a broadband dongle.
The log-in process is a bit strange for chromium, sometimes it will work, sometimes it won't. I don't know if you've seen it but I've got a thread here detailing chromiumOS: [http://ubuntuforums.org/showthread.php?t=1331975](http://ubuntuforums.org/showthread.php?t=1331975)

For the log-in information you should use your google account username and password. The "chromeos" password is for the super-user, but you just want to log in as a normal user. I found that if I inputted my username and password correctly once, then it would have the "network not connected" error, but then if I tried again, it would work. I think it just takes a while for chromium to establish a connection. Also, it won't connect directly to your broadband dongle - chromium will connect to a virtual ethernet adapter, and then virtualbox will take care of the connection from the virtual adapter to the outside world (which it should do with no problems).

---

