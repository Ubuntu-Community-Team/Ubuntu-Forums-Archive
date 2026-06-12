---
title: "cdrom-detect indicates custom cd is not Ubuntu"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by BCSFD204 on 2010-04-27
Hi all...
I've been experimenting trying to create an unattended install CD-ROM for a machine I am planning to use as a testing sandbox.
For the record, this is the first time I've ever attempted to do something like this.
My outcome is to build an unattended CD that would install Ubuntu Server, VirtualBox, and some other toys and tools. 
In other words, if I needed to start over again, I just boot off this CD and walk away for a while.
My starting point was a White Paper entitled Automated deployments of Ubuntu by Nick Barcet dated 09/2008.
I've added some information from two Ubuntu books I bought and some things I found searching the web site. 
Once I get around my current problem, I think the install is going to be a combination of Kickstart and preseeding.
I think I've basically got the parts but I do not appear to have them put together the right way.
Most of my attempts will begin to boot from the CD. However, I get a couple of different installer messages.
Looking at the syslog message stream, here is what I find. Transcription errors are mine. :-)
When I boot from a VANILLA 10.04 beta2 CD, I get the following and the installer seems happy.
cdrom-detect: CD-ROM mount succeded: device=/dev/sr0 fstype=iso9660
cdrom-detect: iso9660 extensions: RRIP_1991A
cdrom-detect: detected CD "Ubuntu-Server 10.04 "lucid lynx" - Beta i386 (20100406.1)'
cdrom-detect: detected cd 'Ubuntu-Server 10.04 "lucid lynx" - beta i386 (20100406.1)'
cdrom-detect: detected cd with 'lucid' (lucid) distribution
When I build my custom CD using the information I have collected I get errors on the installer screen and the following in syslog:
cdrom-detect: cd-rom mount succeded: device=/dev/sr0 fstype=iso9660
cdrom-detect: The cd on /dev/sr0 is not an Ubuntu cd!
It appears that the installer can physically find and mount the cd. But then is must do some validity checking and it chokes.
I've searched the Ubuntu site and Google and I have not found any message text similar to "the cd on /devv/sr0 is not an Ubuntu cd!"
I've tried some of the things that seemed marginally related in my searches but I have not found the right answer.
I think my first question should be:
Can someone explain to me how "cdrom-detect" figures out that the cd in question is or is not an Ubuntu cd?
I think the second question should be:
If someone knows what makes cdrom-detect happy, can you tell me what I have to do to create the "thing" that makes it happy?
Any help/insights would be very welcome.
Thanks.
Tom
 
P.S. This is my first time in any forum so even posting this is a learning experience. :-)

---

### Post by mbmather on 2011-03-21
I am also stuck here.

---

