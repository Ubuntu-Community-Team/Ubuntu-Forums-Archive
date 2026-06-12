---
title: "Open Office 3.0 help needed"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by saitekx50 on 2008-05-25
ok so I just uninstalled openoffice that comes with ubuntu 8.04.  Now I want to install the new openoffice 3.0  How can I do that.  I have downloaded all the deb files  and I dont know which to install.  Please help.


Thanks in advance 

Saitekx50

---

### Post by damis648 on 2008-05-25
All you will need is this file: download it first. [http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0beta](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0beta)

---

### Post by forestpixie on 2008-05-25
Once you have extracted ti - navigate to the DEBS folder in a terminal and do 

```
sudo dpkg -i *
```

Unless it's changed in the last few weeks it won't give you a menu item - I use a launcher to /opt/openoffice.org3/program/soffice

---

### Post by saitekx50 on 2008-05-25
still not working I just want to use the writer. I have installed it in windows.  could you please tell me step by step.  Also should I install the windows version using wine

---

### Post by forestpixie on 2008-05-25
HAve you downloaded the linux version or the windows version - I have no idea if the windows version will work through wine.

If you've downloaded the linux version - I assume it's downloaded to your desktop - if it hasn't you need to find where it is .

Extract the tar.gz where it is - I'm going to assume that it's on your desktop.

Open a terminal and change to the desktop

```
cd Desktop
```

Now change to the openoffice directory - you can use the tab key to fill in the name, mine is called BEA300_m2_native_packed-2_en-US.9301 - if yours is different change the name - inside that is a folder called DEBS

```
cd BEA300_m2_native_packed-2_en-US.9301
cd DEBS
```

if you do a dir now you should have a bunch of files ending in .deb - now run the command

```
sudo dpkg -i *
```
 That should install it to /opt/openoffice.org3

You can run it from there. I assume you know that oo3 is in beta still and could chnage or not be working properly.

---

### Post by some1l8 on 2008-05-25
still in beta stage. if you're not an expert, better waiting for final release

---

