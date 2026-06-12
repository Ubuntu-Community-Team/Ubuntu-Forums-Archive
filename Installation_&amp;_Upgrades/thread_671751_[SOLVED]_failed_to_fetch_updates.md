---
title: "[SOLVED] failed to fetch updates"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by evil316 on 2008-01-18
When attempting to download updates I get this error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  Could not connect to 192.168.1.1:800 (192.168.1.1). - connect (111 Connection refused)

When I copy the link and put it in a browser I can download and install it.  This particular update I can't do that with as the website tells me it's forbidden.  I was able to do it with another update though.

All my updates worked fine a few days ago.  The change I made was I installed updates to get the E17 desktop and make it a Geubuntu from Ubuntu (which also included installed all upgrades in synaptic).  I've since completely removed the Geubuntu packages.  My Xubuntu machine got these same updates without a problem.

Thanks for any help!

---

### Post by yingeric on 2008-01-18
I changed the local site to main site from preferrence and after that it can get the file.
I right click the update icon and select preferrence and then change the site to main site and then click reload.

---

### Post by evil316 on 2008-01-18
That didn't work.  I get the connection refused message for every entry in my repository as well whenever I attempt to reload from either main server or US server.  My other box is configured the same in software sources and it works fine.

---

### Post by cybergalvez on 2008-01-18
> **evil316 said:**
> When attempting to download updates I get this error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  Could not connect to 192.168.1.1:800 (192.168.1.1). - connect (111 Connection refused)

When I copy the link and put it in a browser I can download and install it.  This particular update I can't do that with as the website tells me it's forbidden.  I was able to do it with another update though.

All my updates worked fine a few days ago.  The change I made was I installed updates to get the E17 desktop and make it a Geubuntu from Ubuntu (which also included installed all upgrades in synaptic).  I've since completely removed the Geubuntu packages.  My Xubuntu machine got these same updates without a problem.

Thanks for any help!
getting a similar error:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb)
  403 Forbidden

when I look at the repository myself I don't even see the file its trying to download.  Anyone have an answer to this?  
Jose

---

### Post by cybergalvez on 2008-01-18
found the answer here:
[http://ubuntuforums.org/showthread.php?t=671616]("http://ubuntuforums.org/showthread.php?t=671616")

hope it helps you out as well
Jose

---

### Post by Bubba64 on 2008-01-18
You can also make sure that from system-administration-software sources that you have the repositories marked and you can also change the repositories. You can also access this through synaptic click on settings then repositories. You can also add repositories by finding them with a Google search of your program and then make sure they are the supported sites. You can also look for supported mirrors that have a specific program for downloading. When I updated from feisty to gutsy my download went OK but during the update it stopped itself it turned out that one program gnome desktop I think wouldn't load so I went to a mirror at the college I attend and downloaded it individually and everything has worked fine since. You can also go to synaptic and under filters find broken packages. There are easier ways to due all of these things if you know how to use the terminal but I am new to some of this myself and have limitations in several areas.

---

### Post by evil316 on 2008-01-18
None of those solutions work for me.  When I attempt to check for new updates I get this:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

My other machine has the same repositories and it works fine.  I don't think it's a repository issue, rather a network or configuration issue with gnome.  Everything else to do with my network works perfect.

---

### Post by The Pinny Parlour on 2008-01-19
```
sudo apt-get update
```
Right click on your update notifier and select "check for updates".

---

### Post by evil316 on 2008-01-19
didn't work.  Still get connection refused.

---

### Post by evil316 on 2008-01-20
> **evil316 said:**
> When attempting to download updates I get this error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  Could not connect to 192.168.1.1:800 (192.168.1.1). - connect (111 Connection refused)

When I copy the link and put it in a browser I can download and install it.  This particular update I can't do that with as the website tells me it's forbidden.  I was able to do it with another update though.

All my updates worked fine a few days ago.  The change I made was I installed updates to get the E17 desktop and make it a Geubuntu from Ubuntu (which also included installed all upgrades in synaptic).  I've since completely removed the Geubuntu packages.  My Xubuntu machine got these same updates without a problem.

Thanks for any help!

Bump

---

### Post by evil316 on 2008-01-22
Anyone?

---

