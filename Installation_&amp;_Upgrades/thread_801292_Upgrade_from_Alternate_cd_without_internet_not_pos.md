---
title: "Upgrade from Alternate cd without internet not possible?"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by Kinetica on 2008-05-20
Hi, I'm fairly new to linux, and ubuntu, and trying to upgrade from 7.10 to hardy without having to do a clean install. However my internet connection drops out regularly (in ubuntu 7.10), so I downloaded the alternate-AMD64 distro from a local fileserver and tried to upgrade from that, but it still requires an internet connection, won't let me finish the upgrade without one, when it gets to a package it can't find (apparently it's not on the cd) it just exits the upgrade after restoring the old system. Can anyone explain why this is happening, I thought the alternate cd distro would allow an internet-free upgrade. Help is much appreciated.

---

### Post by Partyboi2 on 2008-05-21
You should be able to upgrade with the alternate cd without a internet connection. 

> **Upgrading using the alternate CD/DVD**

   Use this method if the system being upgraded is not connected to the Internet.  
  
[LIST=1]
[*] 	 	Download and burn the alternate installation CD.  	
[*] 	 	Insert it into your CD-ROM drive.  	
[*] 	 	A dialog will be displayed offering you the opportunity to upgrade using that CD.  	
[*] 	 	Follow the on-screen instructions.  	
[/LIST]
   If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:  
  gksu "sh /cdrom/cdromupgrade"

---

### Post by Kinetica on 2008-05-22
Yes, see that was the problem, that exact procedure would not work without an internet connection. It would exit with errors whenever it tried and failed to access internet data. CD was fine too as I checked it before I began. Ended suffering through many hours of poor, disconnecting internet, only to install and have nVidia driver issues. Think I'll do a clean boot and regress to 7.10, had no trouble with that (except for crappy internet connection). Thanks though.

---

### Post by Tommy on 2008-05-22
> **Kinetica said:**
> Yes, see that was the problem, that exact procedure would not work without an internet connection. It would exit with errors whenever it tried and failed to access internet data. CD was fine too as I checked it before I began. Ended suffering through many hours of poor, disconnecting internet, only to install and have nVidia driver issues. Think I'll do a clean boot and regress to 7.10, had no trouble with that (except for crappy internet connection). Thanks though.

My guess is that the reason it's failing is because you have installed packages that are not on the CD. (VERY likely!) So the REAL way to do an upgrade without a live Internet connection would be to start with one of the DVD images that has all the packages. If you have any non Ubuntu software installed, those packages will not upgrade, either, however they will be less likely to stop the install process.

Alternatively, if you have a machine with a large hard drive, you could make an ubuntu mirror (while connected to the Internet). Then you can connect the machine and/or drive to the machine you want to upgrade and modify the sources.list on the machine you're trying to upgrade to point to your local mirror. If you have more than one machine to upgrade (all your friends?!) this would be a fast way to do it.

---

### Post by zvacet on 2008-05-22
>  Think I'll do a clean boot and regress to 7.10, had no trouble with that (except for crappy internet connection). Thanks though.

If you think about fresh install of Gutsy you can install Hardy from alternate instead.

---

### Post by Tommy on 2008-05-22
> **zvacet said:**
> If you think about fresh install of Gutsy you can install Hardy from alternate instead.

I agree -- if you are going to do a clean install anyway, go ahead with Hardy. The only problem will be reinstalling the packages that were hanging up the upgrade. Maybe you can get someone to burn an Ubuntu Hardy DVD for you. (Assuming you have a drive that can read a DVD, or can copy the contents to a hard drive.)

---

### Post by ankit_sharm on 2009-11-10
> **Kinetica said:**
> Hi, I'm fairly new to linux, and ubuntu, and trying to upgrade from 7.10 to hardy without having to do a clean install. However my internet connection drops out regularly (in ubuntu 7.10), so I downloaded the alternate-AMD64 distro from a local fileserver and tried to upgrade from that, but it still requires an internet connection, won't let me finish the upgrade without one, when it gets to a package it can't find (apparently it's not on the cd) it just exits the upgrade after restoring the old system. Can anyone explain why this is happening, I thought the alternate cd distro would allow an internet-free upgrade. Help is much appreciated.

sir,
     i do not have inter net connection 
so plse provide to me antenna cd.

---

### Post by grandtoubab on 2009-11-10
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)
**Order Ubuntu CDs or DVDs**Use this option if your Internet connection is too slow to download  Ubuntu. If you're planning a larger deployment or simply to ensure a  swift delivery of as many CDs or DVDs as you need.
REquest a free CD
**Requesting an Ubuntu CD**

      Ubuntu is available free of charge and we can send you a CD of  the     latest version (9.10 (Karmic Koala)) with no extra     cost, but the delivery may take up to ten weeks, so you should  consider     downloading the CD image if you have a fast Internet connection.     

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)


**Upgrading from a Torrent**

  If you're familiar with [torrents]("http://en.wikipedia.org/wiki/BitTorrent_%28protocol%29") and have an ISP that doesn't limit them, you can download the upgrade much more quickly. You'll also be sharing your bandwidth with other Ubuntu users and helping to reduce the load on the servers, which is especially beneficial on release days when the server overload causes problems. 
 Just visit [http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/),  and download the appropriate torrent file for the **alternate**  installation CD, found in the list towards the bottom of the page.  (It  will have a filename like *ubuntu-9.10-alternate-i386.iso.torrent*.)   Load it into your [BitTorrent]("https://help.ubuntu.com/community/BitTorrent")  client, and after it is done downloading the ISO, follow the [alternate  CD upgrade instructions]("http://www.ubuntu.com/getubuntu/upgrading#AlternateUpgrade"). 
 [Detailed  instructions here]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html") and [here]("http://ubuntuforums.org/showthread.php?p=4784633#post4784633").  
[URL="http://releases.ubuntu.com/karmic/"]
http://releases.ubuntu.com/karmic/[/URL]

---

