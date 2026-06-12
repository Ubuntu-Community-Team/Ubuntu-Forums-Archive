---
title: "Samba Mount Point"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by capi on 2005-05-29
I have Samba working and I want to mount a samba filesystem from a windows computer on my network, So I can read files from windows on the Unix Machine, however I keep getting the error that smbmount cannot find the mount point. I'm not exactly what the mount point would be. 

My Box is running command line only.

---

### Post by clb137 on 2005-05-29
[QUOTE=capi]I have Samba working and I want to mount a samba filesystem from a windows computer on my network, So I can read files from windows on the Unix Machine, however I keep getting the error that smbmount cannot find the mount point. I'm not exactly what the mount point would be. 

My Box is running command line only.[/QUOTE]

Hi Capi,

Please read the info in this link 
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

then decide which way you want to do it and follow the guide

good luck

clinton

---

### Post by capi on 2005-05-29
[QUOTE=clb137]Hi Capi,

Please read the info in this link 
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

then decide which way you want to do it and follow the guide

good luck

clinton[/QUOTE]
 I saw that, maybe I wasn't clear on my question. The guide assumes its on your local computer, what would be the equivelent for something on a non-loca  computer.

For example I was trying smbmount and adding the ip. Second I'm stil confused as to what mount point lines up to. It seems to be the location of the file off of the harddrive. So if I want to know what exactly I need to use for mount point. Do I use something like `C:/Folder/', or is that translated into `/dev/hda1/Folder' or something? How do I figure that out. Currently the command I'm using looks similar to this...

> smbmount sambafs //dev/hda1/SharedFiles username=SAMBAun,password=SAMBApw,ip=192.168.1.2

---

### Post by clb137 on 2005-05-30
hi,

First of all make sure that the dir or dirves you want to view off your win box are available to share,  IE you have set the permissions on your win box.

Second while in the Gnome desktop goto Places>Networkservices you should have a windows open with your network listed, click on the icon that is the name of your winbox,  there should be listed the dirs off your win box

good luck

clinton

---

