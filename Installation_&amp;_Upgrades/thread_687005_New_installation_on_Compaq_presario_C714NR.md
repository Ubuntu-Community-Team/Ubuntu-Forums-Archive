---
title: "New installation on Compaq presario C714NR"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by NAdams81 on 2008-02-03
I just installed Gutsy on this C714NR Presario and I found info on how to get wifi to work.  The problem is I can't get the NIC to work so I can download the ndiswrapper from Synaptic.  Any ideas (easy on my I'm a beginner.

---

### Post by Partyboi2 on 2008-02-04
you can install ndiswrapper from the ubuntu live cd
> **2.3. Installing Packages (Without Internet access)**
[LIST]
[*]Without an Internet connection, you can still install ndiswrapper-utils from the Desktop CD. If you installed from that, the repository in which ndiswrapper-utils is found is on the CD, but not within the live session. You need to boot into your new Ubuntu installation and then reinsert the Desktop CD. You will be asked if you want to add the packages on the CD to your list of repositories.[/LIST]If you installed using the Dapper Alternate CD, those packages except ndisgtk are included on it. 
 Put the CD into the drive, click **System** > **Administration** > **Synaptic Package Manager** and search for *ndis*. If you don't know how to install applications, [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] read this guide]("http://help.ubuntu.com/starterguide/C/ch02.html"). 
quoted from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-6c3f75213ff90d97beac83ac70cd1a6574a16d27](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-6c3f75213ff90d97beac83ac70cd1a6574a16d27)

---

