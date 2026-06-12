---
title: "almost successful deployment"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by Nicolai on 2005-09-17
Hello Ubuntu People.

I'm a recent windows convert and I got myself in a personally challenging mess right now. 

I work as a administrative manager of a small co-operative and after a recent systems audit (a requirement for our government loan appliction), our group was told to cleanse our systems of illegal software as part of the loan application requirements. The board of directors was told that if we cannot afford Windows licenses (after finding out how much it would cost, they decided that we can't afford it), we should look into free and opensource software for our requirements.

Being a small company, we don't have any IT staff. If we need anything, we usually make do by ourselves with what we know and what we usually find in the Internet. (Google had been a wonderful friend.) Through the years, we have managed to build a kludge of systems. Mostly, with me contributing a lot of voluntary work. I am a consultant and do not have any technical background at all.

Anyway, enough of that. 

I have managed (with help from my son) to install Ubuntu 5.04 in 23 of our 25 computers. (Eventually, the two Windows computers will be migrated to Linux too.) We found an working AMD-K6 computer/15Gb hard drive, stuffed it with as many memory(92Mb RAM) we can get and placed  2 network cards and then installed ubuntu "server" in it.  

Thanks to this forum, this server is now working as: DHCP server, Ubuntu-ICS (connected to a DSL) and Ubuntu-firewall (Thanks to that guy who made those scripts available on the net). We have very simple needs and we don't even operate our own email server, relying only on commercial, web-based email services.

Our most considerable experience prior to this project was a single Ubuntu installation at home. Technically, it wasn't done once because we did a lot of re-installations on that same machine - or should we count those too? 8-)

However, we still haven't managed to get NFS / File Sharing to work. Originally, I thought we should setup Samba but read a thread in the forum that we should use NFS instead since it's going to be an all-Linux network.

My eyes are already tired from googling the net and searching for solutions. Could someone, please point me to a newbie's step-by-step  guide for configuring our humble server for NFS and configuring other computers to read/write into these shared folder from our server.

Oh, and we need to share printers too. Unfortunately, it seems that the laserjet 1020 is not supported at all. 

We'd appreciate the help. After I get all these to work, I promise to put up a small guide on how we managed to do what we've done as a guide for others who may want to move to Ubuntu (or Linux) too.

Nicolai Alcantara

---

### Post by az on 2005-09-17
I think your printer works at 600x600 mode.

[http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)


The networking and shared folder tools should get your boxes hooked up together.

If you read the help pages, you should be able to install the required additional NFS packages, or samba package that are needed for your box to talk to the network.  The default setting for Ubuntu is to listen only.

Samba is not that bad.  It is an open specification and is implemented completely in GPL code.  It is very popular and it works fine.  Who cares who first invented it?

Also, I would try installing (or upgrading to) Breezy once it is released.  Perhaps support for your printer will be easier.  Perhaps the documentation for file sharing is also improved.

You can try upgrading one of your boxes to Breezy now.  It is quite useable.  Just change all your current repositories in Synaptic to use breezy instead of hoary.  I wouldn't upgrade your whole network now, but perhaps you can start trying it out.
The HPLIP support is much better in breezy since it was not quite ready for Hoary at the time.

---

### Post by Nicolai on 2005-09-17
Hi Azz.

I've also tried that link you posted. Unsuccessfully :( A test page would come out beautifully, anything else would be blurred. 

We have the same idea! I'm already upgrading the box with the printer to Breezy.

---

