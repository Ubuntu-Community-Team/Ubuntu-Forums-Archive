---
title: "How can I run a PXE install without Internet Access?"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by zolodon on 2006-10-22
First and foremost, I should state that I'm new to the Ubuntu community (this is my first post here) and still a beginner with Linux as a whole...

That said, I decided I'd start my Ubuntu adventure by picking a project...which happened to be figuring out how to get Ubuntu on a laptop with no CDROM.

I began with some PXE research and found many wonderful arcticles to get me moving quickly.  With only a few snags here and there, I've even managed to set up the laptop to boot the installer as intended from the server...  The part I get messed up on, though, is how to configure the installation source since the server (Ubuntu 6.06) and laptop are on an isolated network with no Internet access (I can get the server connected long enough to download any ISO/files I may need).

Is there a way to mount the CDROM or an ISO on the server so that the network boot of the laptop can see it?  It seems my only option is selecting an Internet mirror site, which does me no good.

NOTE:  I have seen mention of setting up my server as a mirror...but that looked quite complicated and was not well documented on the sites I visited.  If this is the approach I must take, please direct me to some documentation that may help.

Thanks in advance for any info you can share with me for my first Ubuntu project.

---

### Post by zolodon on 2006-10-23
BTW...  I'd much rather direct the install to run an ISO upon bootup than launch a CD.  Is that any more or less difficult to accomplish?

---

### Post by somnoliento on 2006-10-29
The easiest way I've found to do this is by installing a local http server, which serves the files from the ISO (mounted as a loopback device). Is this an option on the LAN you're on? Do you already have a local http server?

(I didn't understand your second question)

---

### Post by naimarshad on 2006-10-29
hello guys there,
zolodon posted exactly same problem what i have, I am having problem that i have laptop with no cd. Some how I managed to download the iso image on my xp box on the same laptop. Now either I should teach the installer to get the iso image and install it from my local HD or get it from the local http or ftp server, as I already have one ftp server on (XP) running in my network, the second question he posted is also same that he first wants to boot into installer to launch the iso then he could launch cd mount command or some thing fimiliar to it!

Please any guru help us to solve it, If zoldon already done with this problem please reply to me.

---

### Post by somnoliento on 2006-10-30
I think you can use your local ftp server, but I doubt Windows is capable of allowing direct access to the files inside the ISO (as mounting would in Linux); you probably have to re-create the CD structure in the FTP server, or look for a windows equivalent to mounting the ISO.

---

### Post by naimarshad on 2006-10-30
hey guys nothing worked for me, probably the mounting iso wil not work with live cd but with alternate install. Let me check it today and i will be back.

---

### Post by unfaigui on 2006-12-16
I have the same problem too. What files that you put it on the local ftp server? I uploaded all the files that are on the ubuntu-alternate-6.06. Did i do it correctly? How do you guys mount the iso file on  the cd into the windows box?( I confues ).

unfaigui

---

### Post by MoHaX on 2007-03-07
Is there any soultion? I've same problem - I need a netboot (it works fine) AND local ftp/nfs/http mirror. Is it possible? I've kubuntu 6.10 alternate dvd.

---

### Post by MoHaX on 2007-03-09
So, solution is quite easy. I've used netboot image from kUbuntu 6.10 alternate DVD, and selected my http server (which one serves full content of alternate DVD) on the step where installer asks to select mirror location, on top of list of mirrors there is "enter manual" menu item.

---

### Post by zolodon on 2007-04-26
I did manage to get this working a while back, but regrettably I didn't take very good notes of the process involved...since I was just happy to have it working (one of my first Linux projects aside from distro-shopping).  :oops: 

I do know, however, that I ended up using the "alternate" CD ISO and another Linux box running DHCP, a web server (as MoHaX mentioned), and the client PXE booting.  With some more tweaking I could probably get the whole process to work "unattended", but I don't think I'll have time in the next few weeks to look into this.

I'll post more results when I get a chance to reload this laptop again.

---

### Post by kerry_s on 2007-04-26
[http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/)

---

### Post by zolodon on 2007-05-01
Well....it looks like I'll be forced to rework this project sooner than I planned (curses to the laptop I have with no CD-ROM that won't properly upgrade like normal!)...

In the next week or so I should have the steps for doing this worked out enough to post a guide a "newby" (like myself) can use to at least get the basic OS loaded.  The end goal for me, though, is to figure out how to do a start-to-finish remote install...similar to Microsoft's RIS product.  I'll post my results in this thread.

---

### Post by andytof47 on 2007-05-22
so can you post your results ---- I'm kind of at the same point

PXE boot all good just need to set up a mirror

---

