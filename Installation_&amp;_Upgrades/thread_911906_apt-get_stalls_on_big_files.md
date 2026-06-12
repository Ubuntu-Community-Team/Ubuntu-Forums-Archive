---
title: "apt-get stalls on big files"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by lvangool on 2008-09-06
I'm trying to do a apt-get upgrade. In this example, it's about the KDE4 repo's at launchpad, but the problem persists in ubuntu's own repo's too..

[pre]
Ophalen:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe libzip1 0.8-1 [23,5kB]
Ophalen:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main kde-icons-oxygen 4:4.1.1-0ubuntu1~hardy1~ppa1 [48,9MB]
Ophalen:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main subversion 1.5.1dfsg1-1ubuntu2~hardy1 [1285kB]
Ophalen:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libneon27-gnutls 0.27.2-1 [109kB]
Ophalen:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main libsvn1 1.5.1dfsg1-1ubuntu2~hardy1 [785kB]
Ophalen:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main libapache2-svn 1.5.1dfsg1-1ubuntu2~hardy1 [151kB]
Ophalen:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main python-subversion-dbg 1.5.1dfsg1-1ubuntu2~hardy1 [4016kB]
Ophalen:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main python-subversion 1.5.1dfsg1-1ubuntu2~hardy1 [1235kB]
[http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main kde-icons-oxygen 4:4.1.1-0ubuntu1~hardy1~ppa1 [48,9MB]
2% [2 kde-icons-oxygen 3120012/48,9MB 6%]
0.00 B/s
[/pre]

..and there the download just stalls. Smaller files download normally, but when a bigger one comes by, it stalls after a few seconds. I'm having this for weeks now, changing mirrors fixes this sometimes (nl->be, when that stopped working be->us), but the kde4 repo doesn't have a mirror AFAIK.

---

### Post by Bucky Ball on 2008-09-06
For an upgrade (to Hardy from Gutsy?) you are much better off downloading the iso and going that way (downloading the torrent file and torrenting even better and more reliable). You give no specs on your computer but maybe the big files are seeing they are not going to fit where you are trying to put them and stalling, filling up whatever space you have with the smaller ones.

If the big files were downloading, you may well find you are going to be there for quite some time anyhow (12 hours has been reported). Although the upgrade from Ubuntu Synaptics is a good idea, it is often problematic and unreliable and unexpected problems occurring once all is done. :)

* [http://ppa.launchpad.net]("http://ppa.launchpad.net/") hardy/main kde-icons-oxygen 4:4.1.1-0ubuntu1~hardy1~ppa1 [48,9MB]

... Incidentally, you seem to be trying to download everything in that particular repo. I would suggest you are doing the same with Ubuntu. You realise how big 48,9MB is? (it is actually 48, 900 mb by the looks, just abbreviated, not 48.9! ). That is gonna crash any box.

---

### Post by lvangool on 2008-09-06
Thnx for your reply.

The kde-icons-oxygen package itself is just that, 48 mb, but I could have been any package bigger then 3 or 4 mb's...Please don't mind these packages, it happens with all packages.

there is no disk space problem and when I execute this upgrade multiple times, it downloads another 1 or 2 mb's from that stalling package, until it's done (will take hundreds of repeats). 

Connection is also no problem, 10mbit up+down on optical fiber.
Box is no problem, Duo Core 6850 cpu.

/dev/sdc2              67G   29G   35G  46% /

---

### Post by lvangool on 2008-09-06
If anyone can provide me a bash script which executes 

sudo apt-get dist-upgrade -y --force-yes 

,Ctrl-C's it after 5 seconds and starts it again, It will download the packages fine.

Please understand, the download just STALLS on big files. It starts at ~900kb/s, falling down to 100 kb/s, then 500 B/s and finally saying it will take a 100 days. Then it's stuck.

---

### Post by crooze38 on 2008-09-20
Well hopefully this fix works or at least triggers some with the similar problems to research router firmware. I have not been able to get updates / package installs / downloads or any large file transfer without several attempts and plenty of patience. Each time that I would attempt to download larger files (several megs) the network transfers would just about always stall. Sometimes the downloads would resume from stalls and other times I would attempt downloads several times until it worked... 
___________________
_Router = DGL-4100_


    After many network/router/firewall configuration changes nothing seemed to work until I noticed that my firmware was 1.6 and 1.7 was available. I checked the release notes on 1.7 and problems with Linux did exist in this case. 

DGL-4100 Firmware version 1.7 Release Notes.

New Features:
1.NAT endpoint filtering enabled.

Problems Resolved:
1.PPTP/L2TP Linux crash/reboot issue resolved.
2.Radius Server NAS-IP fix.
3.UPnP port forwarding fixed to function with Sony Location Free TV.
4.UPnP function in Azureus fixed.
5.DHCP Server not providing DNS servers after ipconfig release/renew when the WAN side is connected to the SBC DSL Modem in DHCP mode is resolved.
6.Timezone and Daylight saving in Manual mode support.
7.Disable gaming rule is displayed when a rule is disabled.
8.Duplicated Inbound Filter Rules not allowed on the Inbound Filter Page.
9.RTSP ALG issue resolved.

Enhancements:
1.Rearrangement of the UI to be user friendly. 
2.Pure Networks – Final HNAP Enhancements.
3.Added 2 NTP servers to drop down list – 
	a.ntp1.dlink.com
	b.ntp.dlink.com.tw
4.Simplified the Dynamic DNS page.
5.Removed WCN ActiveX feature .

     Before installing I backed up my config on the router. This is important if you have customized your router that are not "Default" factory settings. I use mac cloning and different IP ranges that are assigned to specific systems on my network so this was a must. 

     After the firmware was updated and I uploaded my custom config file to the router everything worked flawless. No more network stalls. All downloads work blazingly fast and the raw throughput is amazing. Since installing "Hardy" I have had this trouble. Previously I had no trouble. I hope this helps some of you...
:guitar:

---

