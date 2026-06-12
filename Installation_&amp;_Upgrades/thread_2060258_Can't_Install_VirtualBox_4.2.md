---
title: "Can't Install VirtualBox 4.2"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by TedinOz on 2012-09-19
Hi...

Not sure if this is the right place  to run this.

I am trying to install Virtualbox 4.2 in 12.04 LTS using this...

[http://www.webupd8.org/2012/09/virtualbox-420-released-with-support.html](http://www.webupd8.org/2012/09/virtualbox-420-released-with-support.html)

I removed Version 4.1.12-1 via synaptic before running the required commands and all was going well until it got to the point of installation. Terminal shows this output with error :

[HTML]~$ sudo apt-get install virtualbox-4.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libgsoap1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  virtualbox-4.2
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/60.5 MB of archives.
After this operation, 132 MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 261608 files and directories currently installed.)
Unpacking virtualbox-4.2 (from .../virtualbox-4.2_4.2.0-80737~Ubuntu~precise_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/virtualbox-4.2_4.2.0-80737~Ubuntu~precise_i386.deb (--unpack):
 trying to overwrite '/usr/share/virtualbox/VBoxGuestAdditions.iso', which is also in package virtualbox-guest-additions-iso 4.1.12-1
No apport report written because MaxReports is reached already
                                                              dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-4.2_4.2.0-80737~Ubuntu~precise_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

The error detail seems to suggest a link to my previous version but I am not sure what this means. Can any one help please?

Thanks in advance

---

### Post by youngunix on 2012-09-19
You want Vbox 4.2, get it ---->  [here]("https://www.virtualbox.org/wiki/Linux_Downloads")<----- from the official website, it's a deb format, double click and install.

---

### Post by TedinOz on 2012-09-19
@youngunix
Thanks for reply. Tried that but didn't work either. Getting similar failed error...


[IMG][[IMG]http://img819.imageshack.us/img819/7392/vboxf.png[/IMG]](http://img819.imageshack.us/i/vboxf.png/)[/IMG]




```
(Reading database ... 100%
(Reading database ... 261608 files and directories currently installed.)
Unpacking virtualbox-4.2 (from .../virtualbox-4.2_4.2.0-80737~Ubuntu~precise_i386.deb) ...
dpkg: error processing /home/tioz/Downloads/virtualbox-4.2_4.2.0-80737~Ubuntu~precise_i386.deb (--install):
 trying to overwrite '/usr/share/virtualbox/VBoxGuestAdditions.iso', which is also in package virtualbox-guest-additions-iso 4.1.12-1
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe
dpkg-deb: error: subprocess paste returned error exit status 2
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...

```

---

### Post by youngunix on 2012-09-19
did you remove and clean previous installations? Check dependencies, and run the usual commands:
```
 
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get autoclean
sudo apt-get autoremove  #just in case
```

---

### Post by TedinOz on 2012-09-19
> **youngunix said:**
> did you remove and clean previous installations? Check dependencies, and run the usual commands:
```
 
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get autoclean
sudo apt-get autoremove  #just in case
```

Previous installation was completely
 removed in synaptic.Ran the commands you gave and all seems good. I am not sure how to check dependencies. Can you tell me how to do that please?

---

### Post by TedinOz on 2012-09-21
Bumping this. Can anybody guide me please?

---

### Post by TedinOz on 2012-09-21
Update:

I am still researching this. This thread shows the exact same problem for typos1 when trying to upgrade to skype 4. 

[http://ubuntuforums.org/showthread.php?t=2004166&page=2](http://ubuntuforums.org/showthread.php?t=2004166&page=2)

Post #14 gives a new purge command which completely removes the earlier version.

Would anyone know the same command for virtualbox? Or guide me how to frame it?

---

### Post by TedinOz on 2012-09-22
Finally figured this. Discovered in Synaptic that Vbox Guest additions for the earlier version needed to be removed also. Doing this allowed new installation although Guest additions 4.2 had to be obtained and installed anew. 

All is good. Thanks for contributions

---

### Post by minakale on 2013-04-10
dpkg: error processing /var/cache/apt/archives/virtualbox-4.2_4.2.0-80737~Ubuntu~precise_i386.deb (--unpack):

I had the same error when I was trying to build a debian live CD in a chroot while running virtualbox in my main debian account.
After i closed the already running virtualbox , the 2nd one was installed without any problem.

---

