---
title: "When ever i try to install something i get Package operation failed"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by justtoplay on 2011-11-20
Here is a example of me trying to install something it happens with every thing



installArchives() failed: Selecting previously deselected package warzone2100. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 125129 files and directories currently installed.) 
Unpacking warzone2100 (from .../warzone2100_2.3.8-1_amd64.deb) ... 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for gnome-menus ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ... 
Downloading... 
--2011-11-19 23:49:53--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz) 
Resolving archive.canonical.com... 91.189.88.33 
Connecting to archive.canonical.com|91.189.88.33|:80... connected. 
HTTP request sent, awaiting response... 404 Not Found 
2011-11-19 23:49:54 ERROR 404: Not Found. 
 
download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of flashplugin-installer: 
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however: 
  Package flashplugin-downloader is not installed. 
  Package flashplugin-downloader:i386 is not configured yet. 
dpkg: error processing flashplugin-installer (--configure): 
 dependency problems - leaving unconfigured 
Setting up warzone2100 (2.3.8-1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 flashplugin-downloader:i386 
 flashplugin-installer 
Error in function:  
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ... 
Downloading... 
--2011-11-19 23:49:56--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz) 
Resolving archive.canonical.com... 91.189.88.33 
Connecting to archive.canonical.com|91.189.88.33|:80... connected. 
HTTP request sent, awaiting response... 404 Not Found 
2011-11-19 23:49:57 ERROR 404: Not Found. 
 
download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of flashplugin-installer: 
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however: 
  Package flashplugin-downloader is not installed. 
  Package flashplugin-downloader:i386 is not configured yet. 
dpkg: error processing flashplugin-installer (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing:

---

### Post by hansdown on 2011-11-20
Welcome to the forum, justtoplay

The warzone package, is 64bit,

Are you running 64bit?

If so, please install,

```
flashplugin-installer
```

From software center, or synaptic.

And,

```
flashaid

```

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by justtoplay on 2011-11-20
o no i am not running 64bit but it seems like every thing im having issues with like installing flash player for videos on youtube

---

### Post by justtoplay on 2011-11-20
some thing just tried to get audacity and got this

installArchives() failed: Selecting previously deselected package libflac++6. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 125426 files and directories currently installed.) 
Unpacking libflac++6 (from .../libflac++6_1.2.1-4ubuntu1_amd64.deb) ... 
Selecting previously deselected package audacity-data. 
Unpacking audacity-data (from .../audacity-data_1.3.13-5_all.deb) ... 
Selecting previously deselected package libid3tag0. 
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-10build2_amd64.deb) ... 
Selecting previously deselected package libmad0. 
Unpacking libmad0 (from .../libmad0_0.15.1b-5ubuntu1_amd64.deb) ... 
Selecting previously deselected package libmp3lame0. 
Unpacking libmp3lame0 (from .../libmp3lame0_3.98.4-0ubuntu1_amd64.deb) ... 
Selecting previously deselected package libportsmf0. 
Unpacking libportsmf0 (from .../libportsmf0_0.1~svn20101010-3_amd64.deb) ... 
Selecting previously deselected package libtwolame0. 
Unpacking libtwolame0 (from .../libtwolame0_0.3.13-1_amd64.deb) ... 
Selecting previously deselected package libvamp-hostsdk3. 
Unpacking libvamp-hostsdk3 (from .../libvamp-hostsdk3_2.1-1_amd64.deb) ... 
Selecting previously deselected package libwxbase2.8-0. 
Unpacking libwxbase2.8-0 (from .../libwxbase2.8-0_2.8.11.0-0ubuntu10_amd64.deb) ... 
Selecting previously deselected package libwxgtk2.8-0. 
Unpacking libwxgtk2.8-0 (from .../libwxgtk2.8-0_2.8.11.0-0ubuntu10_amd64.deb) ... 
Selecting previously deselected package audacity. 
Unpacking audacity (from .../audacity_1.3.13-5_amd64.deb) ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for shared-mime-info ... 
Processing triggers for gnome-menus ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for man-db ... 
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ... 
Downloading... 
--2011-11-20 00:28:23--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz) 
Resolving archive.canonical.com... 91.189.88.33 
Connecting to archive.canonical.com|91.189.88.33|:80... connected. 
HTTP request sent, awaiting response... 404 Not Found 
2011-11-20 00:28:24 ERROR 404: Not Found. 
 
download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of flashplugin-installer: 
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however: 
  Package flashplugin-downloader is not installed. 
  Package flashplugin-downloader:i386 is not configured yet. 
dpkg: error processing flashplugin-installer (--configure): 
 dependency problems - leaving unconfigured 
Setting up libflac++6 (1.2.1-4ubuntu1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up audacity-data (1.3.13-5) ... 
Setting up libid3tag0 (0.15.1b-10build2) ... 
Setting up libmad0 (0.15.1b-5ubuntu1) ... 
Setting up libmp3lame0 (3.98.4-0ubuntu1) ... 
Setting up libportsmf0 (0.1~svn20101010-3) ... 
Setting up libtwolame0 (0.3.13-1) ... 
Setting up libvamp-hostsdk3 (2.1-1) ... 
Setting up libwxbase2.8-0 (2.8.11.0-0ubuntu10) ... 
Setting up libwxgtk2.8-0 (2.8.11.0-0ubuntu10) ... 
Setting up audacity (1.3.13-5) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 flashplugin-downloader:i386 
 flashplugin-installer 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ... 
Downloading... 
--2011-11-20 00:28:25--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz) 
Resolving archive.canonical.com... 91.189.88.33 
Connecting to archive.canonical.com|91.189.88.33|:80... connected. 
HTTP request sent, awaiting response... 404 Not Found 
2011-11-20 00:28:26 ERROR 404: Not Found. 
 
download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of flashplugin-installer: 
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however: 
  Package flashplugin-downloader is not installed. 
  Package flashplugin-downloader:i386 is not configured yet. 
dpkg: error processing flashplugin-installer (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing:

---

### Post by hansdown on 2011-11-20
If you open,

```
software center
```

It's in there.

---

### Post by justtoplay on 2011-11-20
That is where i got it from.

---

### Post by raja.genupula on 2011-11-20
try this 

```
sudo apt-get install -f
sudo apt-get update
```

post here what you got.

---

