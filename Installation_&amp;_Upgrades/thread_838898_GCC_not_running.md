---
title: "GCC not running"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by Mehak on 2008-06-23
I am trying to run a C code on my gcc compiler but it gives me a error that file stdio.h not found .

I tried the following things 
**sudo apt-get install build-essential**

directs me to add the cd 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)',since I dun have the original cd of iso image I loaded the os from can you direct me where to find the above disc.

[B]gksudo gedit  /etc/apt/sources.list
[/B]
doesn't let me save the edited changes in the file

Also the vim editor is not working properly in the insert mode and I am unable to download the emacs editor.

Regards
Mehak

---

### Post by iaculallad on 2008-06-23
To enable you're download via the internet repo and not on your CDROM media, try to follow the following steps below.

Navigate to System->Administration->Software Sources, under the "Ubuntu Software" tab, be sure that the Main, Universe, Restricted, and Multiverse is marked as checked. Uncheck the option w/c says "Installable from CDROM/DVD". Select the "Download From:" to equal to "Main Server". Click on close and open your terminal.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential

```

Retry your GCC application.

---

