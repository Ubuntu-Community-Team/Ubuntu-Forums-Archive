---
title: "Wubi Netbook Install 10.4 fails"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by le_top on 2010-08-30
I've tried several times over the past day to install Ubuntu Netbook using Wubi but it kept on failing after the download of the ISO.
 
After checking the log, I notice that it complains that 10.04 != 10.04.1 regarding the version.
For the netbook, the ISO downloaded is indeed 10.04 while the installation title says it is installing 10.04.1.
 
I am sure that there is an easy fix for this in Wubi.
 
I've used Wubi in the past and I am quite happy about it. This is not the proper place for it, but I'ld like to see the installation type support VirtualBox too ;-) - i.e., the Ubuntu setup installed by Wubi should be able to run inside VirtualBox.

---

### Post by bcbc on 2010-08-30
> **le_top said:**
> I've tried several times over the past day to install Ubuntu Netbook using Wubi but it kept on failing after the download of the ISO.
 
After checking the log, I notice that it complains that 10.04 != 10.04.1 regarding the version.
For the netbook, the ISO downloaded is indeed 10.04 while the installation title says it is installing 10.04.1.
 
I am sure that there is an easy fix for this in Wubi.
 
I've used Wubi in the past and I am quite happy about it. This is not the proper place for it, but I'ld like to see the installation type support VirtualBox too ;-) - i.e., the Ubuntu setup installed by Wubi should be able to run inside VirtualBox.

Wubi.exe will only install the same version of Ubuntu as it is configured to. So if wubi says 10.04.1 it will ignore the 10.04 .iso and download a new one. You will need to find the old wubi.exe and use that instead. Or download the 10.04.1 .iso. There is no getting around this (except an intricate process involving editing the .iso file).

I think the version you want is r189 and can be found here: [http://people.canonical.com/~evand/wubi/lucid/](http://people.canonical.com/~evand/wubi/lucid/)
(but note you'll then have to download all the updates that come with 10.04 and that'll take you to 10.04.1 anyway - it'll be quicker to download the 10.04.1 .iso using bittorrent).

---

### Post by le_top on 2010-08-30
Hi

Thank you for your reply.

I do not mind installing the latest version, it is just that 'Wubi' is downloading the 10.04 Netbook version.

The r189 version says it can not find the metalink and r190 downloads ubuntu-10.04-netbook-i386.iso.torrent .

The workaround surely is to trick Wubi into using the downloaded iso by renaming it and putting it in the same directory as where wubi is, but it is best that this works 'out of the box' for the currently available latest version in each of the categories.

Further - for a simple version issue - it might be useful to prompt the user about accepting this issue.

---

### Post by bcbc on 2010-08-30
> **le_top said:**
> Hi

Thank you for your reply.

I do not mind installing the latest version, it is just that 'Wubi' is downloading the 10.04 Netbook version.

The r189 version says it can not find the metalink and r190 downloads ubuntu-10.04-netbook-i386.iso.torrent .

The workaround surely is to trick Wubi into using the downloaded iso by renaming it and putting it in the same directory as where wubi is, but it is best that this works 'out of the box' for the currently available latest version in each of the categories.

Further - for a simple version issue - it might be useful to prompt the user about accepting this issue.

Oh ok - I get it. When you run wubi.exe direct it gives you a choice of what flavour of Ubuntu you want to install. If you download the Ubuntu 10.04.1 .iso, then it will use it, but only if you select Ubuntu from the wubi drop down box. 

If you select "Netbook edition", then it will ignore the ubuntu .iso and download the netbook one. Since there is no 10.04.1 netbook .iso (for whatever reason) it's downloading the 10.04 one.

You can't trick wubi.exe by renaming the .iso - it actually looks inside the .iso to find a \disk\.info file (something like that) and pulls the version info from that.

---

### Post by le_top on 2010-08-30
Yep - that is the problem.

Also - unfortunately - after pulling the ISO and detecting that it is the wrong version, Wubi seems to delete the ISO it fetched and tries getting another one from several sources which fails end ends in a 'getaddrinfo failed'.

So I guess I'll wait a couple of days before trying again.

---

### Post by bcbc on 2010-08-30
> **le_top said:**
> Yep - that is the problem.

Also - unfortunately - after pulling the ISO and detecting that it is the wrong version, Wubi seems to delete the ISO it fetched and tries getting another one from several sources which fails end ends in a 'getaddrinfo failed'.

So I guess I'll wait a couple of days before trying again.

Download the .iso you want using bittorrent. It's way faster than wubi and you don't have to download it again (e.g. if you reinstall). You'll also have it available to create a live CD/USB as well - very useful.

Place wubi.exe and the downloaded .iso in the same folder, and it will pick it up and use it.

---

### Post by bcbc on 2010-08-31
PS just found a thread - someone had the same problem. Turns out the wubi.exe from 10.04.1 can't install the 10.04 netbook edition. You need to use the original wubi.exe from 10.04. Here's a link to the thread: [http://ubuntuforums.org/showthread.php?p=9777414](http://ubuntuforums.org/showthread.php?p=9777414)

---

