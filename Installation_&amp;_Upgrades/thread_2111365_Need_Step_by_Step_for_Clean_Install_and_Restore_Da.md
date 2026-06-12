---
title: "Need Step by Step for Clean Install and Restore Data from 12.04"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by kendoori on 2013-02-01
Tried an inplace upgrade a few months ago from 12.04-->12.10 and never properly booted. I got a blank screen. I had cloned prior to the upgrade so I was able to easily reinstall. 

Am running a Thinkpad X201 w/480GB SSD (110Gib free). I don't have a separate home partition, but my home is encrypted. Am also running Gnome-Shell.

I have plenty of external storage for backups etc...

If you are a "fresh install" person, what's your process? or do you have a favorite recipe online that you like to follow?

---

### Post by Bashing-om on 2013-02-01
kendoori; Hi !

Keeping in mind that how one uses their computer is a personal thing. No two people will do the same things.

Me and my method: 
I have always done a clean install from one major release to the next.

I have backups of all my applications's data that is backed up weekly (manually as the mood strikes me); In addition I maintain a "change log" of any alterations I make to my operating system. Breaking and (re)installing has taught me a lot ! My Backups are on a dedicated drive that I only mount manually on-demand and (un)mount when not in use.

Over the years I have set up with many configurations. Now-a-days I go with the standard installs, letting the install wizard take care of it all:
I download the desired .iso image file, burn to disk, boot it and install "along side of" - I presently have four versions installed on this box- 10.04 will soon be over written by 13.04. I use GParted to delete the partitions of the old install to install the new version onto. Done !

For a desk top I find no need for elaborate partitioning. With the standard install on 300+ GB drives I have never experience and out-of-disk space problem doing such, or having to keep track of what data I have on what partition and monitoring them for resource allocation.

In short, keep it simple unless you have a demonstrated need not to go with the standard install <-burned CD <- d/l'd .iso image.

I'll be more than willing to answer any other specific questions.

[INDENT]just my thought

[/INDENT]

---

### Post by presence1960 on 2013-02-02
As Bashing-om has said- there are many ways to set up a machine. I always do clean installs. I always have at least two linux installations and a Windows installation. I keep all my data on a separate NTFS partition so all OSs can access it. This saves a step when installing: I do not need to move my files because they are not on an OS partition. I do not keep a separate /home partition, but rather maintain a back up of the standard /home folder. This contains a lot of the settings I tweaked on my installed software. This back up can easily be restored to a new Ubuntu install so the software will retain it's settings.

I also keep a file of any software I have installed and just install them from terminal after the new install is updated. After the software is installed and all other tweaks are done I make an image of the OS partition with Clonezilla.

There are many options and you will have to find what is the best way that will accomplish what you will want to do with your machine.

---

