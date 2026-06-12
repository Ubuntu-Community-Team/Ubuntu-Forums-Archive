---
title: "I want to upgrade, but I feel scared :)"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by unknown user on 2011-10-25
I have been running 11.04 recently and have really enjoyed the experience. It has come to the point where at home, I only ever go into Ubuntu and never seem to use my windows system. I have been able to do everything I want in Ubuntu, find it so much more easier to use than the older versions I had and it is far faster than Windows. 

I have recently been presented with the upgrade to 11.10 message box. I have had a look at the screenshots for 11.10 and it looks really nice. I want to upgrade, but remember in the past when I upgraded from one version to another and the system crashed. I had to reload Ubuntu and lost a fair bit.

Is the change from 11.04 to 11.10 smother now and can I just copy my user folder as a backup? With the user folder, if anything does happen during the upgrade, can I just install the new version of Ubuntu and then add my stored user file and then go from where I left?

---

### Post by Hakunka-Matata on 2011-10-25
One possibility:
Install 11.10 on a separate partition all by itself.  
Do not delete or upgrade your current ubuntu partition.
Do you have room on your HDD?  Post output of code
```
sudo fdisk -l
```

---

### Post by Mark Phelps on 2011-10-25
The main problem you're going to face doing an in-place upgrade is that, after all these years, Canonical has still NOT seen fit to provide even a basic version roll-back capability for Ubuntu upgrades.

To protect against the worst case, where an upgrade really trashes your install such that it won't work at all anymore, you should consider using Clonezilla to back off your current install to an external drive.  That way, if it goes really bad, you can boot from the Clonezilla CD and restore your current working system in only a few minutes.

---

### Post by BHEJU on 2011-10-25
There are lots of issues during the upgrade for multiple reasons (as is case with any OS). I upgraded a week after the release and it crashed as well. I had to do fresh install. 
I suggest you wait a while for all the initial bugs to be identified and sorted.

---

### Post by cortman on 2011-10-25
If you're afraid of losing things, how about backing up your stuff before you try and upgrade?? Since all the software's free anyway reinstalling doesn't mean money for new licenses, etc. I'd say backup and go for it.

---

### Post by unknown user on 2011-10-25
Hi there, thanks for that. I did not know about clonezilla, but sure will look into it. To tell you the truth, I think a new partition may be the way to go as I am running Ubuntu within windows at the moment and keep on running out of space. 

If I do a fresh install and then copy my user folder from 11.04 and then paste it in the new 11.10 will this bring all my data/settings, apart from the programs? I have a list of all the programs that I use so that should be easy enough. A backup, is the user file enough?

---

### Post by drs305 on 2011-10-25
Another simple backup option if you have space on an extra partition is to use fsarchiver. You can use the LiveCD or a systemresuce CD, or another Linux OS as long as your Ubuntu partition is not mounted.

The command to backup an entire partition is very simple. I'll just give you the options I use, which will back up the file with medium compression and display what's going on as it's run. My backup takes about 10 minutes and produces a file about 2GB. I do NOT have data files on the partition - my Ubuntu installation is about 6GB. fsarchiver only backs up the files - it doesn't image the entire partition so the backup image isn't the same size as the partition.

Boot a rescue CD with fsarchiver, or boot the LiveCD and install fsarchiver. Mount a backup partition on which to store the file and move to a folder within it. The example backs up the OS installed on sda5 and saves the file in the folder in which the command is run.

```
sudo fsarchiver savefs -z 3 -v filename /dev/sdXY
```
Example:
sudo fsarchiver savefs -z 3 -v natty.backup.fsa /dev/sda5

If you need to restore the entire partition:
```
sudo fsarchiver restfs -v natty.backup.fsa id=0,dest=/dev/sda5
```

---

### Post by varunendra on 2011-10-27
> **unknown user said:**
> If I do a fresh install and then copy my user folder from 11.04 and then paste it in the new 11.10 will this bring all my data/settings, apart from the programs? I have a list of all the programs that I use so that should be easy enough. A backup, is the user file enough?
The results of copying contents of a previous /home directory over the newer /home directory are full of uncertainty. It may work, maybe not. It depends upon what programs you use and their versions (basically, the consistency between version changes).

In your particular case, the problem with any 'partition backup' tools is that they will only see a windows partition since ubuntu is in a virtual partition contained in a "root.disk" file. So one way to effectively back it up is to just backup the ubuntu\disks directory (with compression, if possible, to save space). But restoring it may be a bit tricky in case it is needed.

So my preferred way was to move as much user-data as possible from /home to another location, then install and use [remastersys]("http://www.geekconnection.org/remastersys/") from within Ubuntu. I used to say a lot of things about it, but unfortunately, its developer seems to have abandoned its development and no downloads are available for it now (at lease not on its official or sourceforge pages). Maybe someone can suggest a good alternate for it. I myself am in search for one.

As for you, the quickest and the best way to go seems to:

[LIST]
[*]Backup your ubuntu\disks directory
[*]Copy the contents (with "Show Hidden Files" enabled) of your /home directory on a thumb drive etc.
[*]Create an empty partition for Ubuntu
[*]Install 11.10 on it
[*]Copy the contents of the backed up /home directory into the newly created one in 11.10 and hope for the best.
[/LIST]
Please note that once grub is overwritten (during installation of 11.10), you won't be able to boot into the existing wubi installation. It's normal.

Hope I didn't miss anything, and it goes well for you.

---

### Post by varunendra on 2011-11-03
> **varunendra said:**
> So my preferred way was to move as much user-data as possible from /home to another location, then install and use [remastersys]("http://www.geekconnection.org/remastersys/") from within Ubuntu. I used to say a lot of things about it, but unfortunately, its developer seems to have abandoned its development and no downloads are available for it now (at lease not on its official or sourceforge pages).

Good news! Remastersys is BACK!! :D
[http://forum.linuxmint.com/viewtopic.php?f=60&p=490001](http://forum.linuxmint.com/viewtopic.php?f=60&p=490001)
[http://ubuntuforums.org/showthread.php?t=1870607](http://ubuntuforums.org/showthread.php?t=1870607)

I seriously think it deserves much more attention and support from both users and developers.

---

