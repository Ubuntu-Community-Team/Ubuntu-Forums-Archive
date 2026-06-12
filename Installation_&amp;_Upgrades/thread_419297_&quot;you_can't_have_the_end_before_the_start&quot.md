---
title: "&quot;you can't have the end before the start&quot; error when partitioning with feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by caimex on 2007-04-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107787](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107787) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				When I try to install Feisty with the livecd everything goes fine but when its time to partition my harddrives I run into a wall.

I have two hdds, one with all my files from edgy which I don't want to format. The other drive is a 250gb drive. I click it and create a new partition table. Then I create a 1.5gb swap partition. That works fine, but when I use the remaining space to create an ext3 partition it gives me the error "you can't have the end before the start". I have tried clicking on "begging" and "end" for the location, and I put / as the mount point.

I googled the error and found [**[COLOR="DarkRed"][SIZE="3"]this bug on launchpad[/SIZE][/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107787") which describes my problem exactly: Can't create partitions more than 200gb. Is this just happening to me or this a widespread thing. Anything I can do?

---

### Post by Tommy James on 2007-04-24
Similar issue: I have a 250GB single hard drive.  Tagging along and bumping to the front.

---

### Post by catsanddogs on 2007-04-24
My solution to this was to partition the hard drive using the live cd version of gparted.
[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

The alternate version of Feisty will partition properly.

Feisty and gparted give different sizes for the same partition. In gparted I created a partition 40GB and in the alternate version of Feisty it read it as 43GB. Gparted read the total size as 465GB (approx, don't remember exactly) and Feisty read the total size as 500GB. The manufacturer lists it as 500GB but they round off a GB to 1000 MB's and the size is always advertised as larger than it is. I think gparted gives the correct size.

---

### Post by pvrbyrich on 2007-09-17
I've got the same problem trying to install from the Canonical DVD.  I had the command line version working from the alternate install CD.  If I go back and reinstall from that source, how do I add all the desktop stuff later?  Or is there a better course of action?

---

### Post by Pumalite on 2007-09-17
sudo apt-get install ubuntu-desktop
Make sure you have at least 512 MB RAM

---

### Post by thisiam on 2007-12-24
I had this problem with a 300GB HDD when i tried to do it manually but when i select 
guided to use the whole drive it detected all 300GB.

---

### Post by Pumalite on 2007-12-24
You can use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Make the partitions ahead of time and then install going Manual and using the partitions already made.

---

