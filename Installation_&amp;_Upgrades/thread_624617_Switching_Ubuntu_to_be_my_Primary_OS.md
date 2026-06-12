---
title: "Switching Ubuntu to be my Primary OS"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by hodge24 on 2007-11-27
Hi everyone,

I've successfully installed Ubuntu 64 bit (Gutsy) on my laptop, and have spent the past couple of weeks configuring, downloading applications, and generally tinkering to get it precisely how I want it. My system is currently a Duel boot system, with XPoo as the primary OS.

I'm almost ready to make the switch, and rid myself of Windoze as my main OS (which I now only use for .NET/SQL Server development for work, and games - but I guess I can take care of that with VMware, WINE, and/or myriad other options).

However, after spending the last two weeks sorting the system out, I'd really rather not have to go through the whole process again (especially having a relatively slow internet connection!), in order to reinstall and set up Ubuntu as my primary OS in a nice new primary partition!

So, my question is: is there a way that I can backup my current system, settings, application installs, drivers etc., and use the backup as the new installation - thus, I guess, essentially creating my own personal distribution for my laptop, which I can burn to DVD, and use the DVD to boot from, partition, and then install, without having to go through the downloads, configuration etc. that I've just completed? OK, that was a rather long sentence... breath...

Thanks so much for any help or information anyone may be able to give.

Hodge (a VERY happy Ubuntu 64 bit user!)

**EDIT:** It seems [remastersys]("http://www.remastersys.klikit.org/") will do precisely what I'm looking for. So, I guess I should edit my question to: has anyone here had any experience with remastersys? Does it do exactly what it says on the tin? What about Mondo? Will this do the same thing? Mondo vs remastersys?

Thanks once again,

Hodge (an increasingly happy Ubuntu 64 bit user)

---

### Post by daengbo on 2007-11-27
You might want to look at the Ubuntu Customization Kit
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

---

### Post by daengbo on 2007-11-27
It's also not too difficult to do manually.

Install Apt-on-CD
Get your current apt cache on an apt CD so you don;t have to download again.
Copy the packages you have installed using 
dpkg -i|grep ^i|awk {'print $2'} > packagelist.txt
If you've done any customization to /etc, copy those files over, too

Reinstall
Add the Apt-onCD with
sudo apt-cd add

Install the packages with this line (and the Cd in the drive)
cat packagelist.txt|while read package;do sudo apt-get install $package;done

Copy over any /etc files

Reboot if you had a lot of services with configs in /etc

You should be done. It's not automatic, but the Unix "everything is a file" mentality makes copying systems quite simple.

This doesn't help if you installed anything from source, though.

If you feel like living on the edge, make backups of your entire partitions, repartition your machine using a live CD, untar into the new partitions, and install Grub via the live CD.

---

