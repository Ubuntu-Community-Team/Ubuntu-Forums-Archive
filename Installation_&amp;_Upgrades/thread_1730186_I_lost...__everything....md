---
title: "I lost...  everything..."
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by i_am_an_idiot on 2011-04-15
I had (emphasis on HAD) a Windows 7 system on a 2 TB disk and Ubuntu 10.10 on a separate 1 TB disk.  My intention was to install 11.04 beta 2 alongside 10.10 on the 1 TB disk.  So when I rebooted with the install disk and saw the "Install alongside 10.10" option I thought that's what I wanted...  Of course, you know what happened.

I don't want to say anything definitively because I could be wrong, but I don't recall seeing a single warning that this option would destroy non-Ubuntu partitions on other disks.  Not even a "Are you sure you want to do this?".  As a result of this I've lost years of personal files, class assignments, hundreds of dollars of software which will have to be re-purchased, games I've put countless hours into and more.  I don't want to even think about it.  

Yes, I know I should have backed up.  But how do you back up a 2 TB disk?  Buy another 2 TB disk?  And I thought I was smart enough to avoid choosing any options which would nuke my data.  I guess I was wrong about that.

I know that as far as tragedies go, this is pretty small time, but I'm in a state of shock now.  Has anyone had a similar problem or stories of their own to tell?  Hearing other experiences might make me feel a little better.  Now, if you will excuse me, I'm going to lay down and have a good cry now.

---

### Post by Telengard C64 on 2011-04-15
> **i_am_an_idiot said:**
> Yes, I know I should have backed up.  But how do you back up a 2 TB disk?  Buy another 2 TB disk?

Yes, exactly. And it isn't enough to have only one backup. [3-2-1](http://www.dpbestflow.org/backup/backup-overview) is a good rule of thumb.

> And I thought I was smart enough to avoid choosing any options which would nuke my data.  I guess I was wrong about that.

Really none of us is that smart. Everyone experiences data loss at some point, even those who refuse to admit it. The data on your computer is constantly in jeopardy from numerous threats, including but not limited to:

[list]
[*]User error like accidental deletion, mistaken overwriting, or partitioning/formatting the wrong drive. It happens to the best of us.
[*]Malicious software like viruses, *prank* scripts, or trojans. Linux systems may be less likely to succumb to malware, but a naive user can still be coaxed into running an ill advised script or installing a rootkit.
[*]Software errors caused by program bugs, regressions, or just plain bad design.
[*]Hardware failure.
[*]Fire, natural disaster, or anything else which may result in the destruction of your computer.
[/list]

By the way, I don't know for a fact that your data is unrecoverable. Maybe one of these can still help you. Even after partitioning and formatting it still may be possible to recover files. Only overwriting the disk will completely destroy the data AFAIK.

[list]
[*][http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[*][http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[*][http://trinityhome.org](http://trinityhome.org)
[*][http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[/list]

---

### Post by Hedgehog1 on 2011-04-15
While I trust your judgement that things are toast, if you would like a second opinion, please do this:

From Ubuntu on the Disk, **OR** from the LiveCD/LiveUSB:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.


***The Hedge***

:KS

p.s. If you installed from a LiveUSB, sometimes the USB becomes /dev/sda and then your first hard drive is /dev/sdb.  This may have been what sunk you, making you think you were installing on the second drive which is normally /dev/sdb.

---

### Post by d3v1150m471c on 2011-04-15
[http://tombuntu.com/index.php/2008/04/09/recover-deleted-files-with-foremost/](http://tombuntu.com/index.php/2008/04/09/recover-deleted-files-with-foremost/)

I use foremost. It will recover most stuff. I also recommend scalpel. You can install and use these from a liveCD so you don't have to worry about running off the disk and deleting anything or overwritting anything. good luck to you. Hope these help. See also:

[http://www.google.ca/search?hl=en&source=hp&biw=991&bih=627&q=ubuntu+recover+deleted+files&aq=o&aqi=&aql=&oq=](http://www.google.ca/search?hl=en&source=hp&biw=991&bih=627&q=ubuntu+recover+deleted+files&aq=o&aqi=&aql=&oq=)

edit:
just found this - looks promising:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by i_am_an_idiot on 2011-04-15
Thanks for the substantive replies and useful info.  I checked the partitions and 11.04 ate up the whole thing.  I'm already re-installing Windows 7 as I type this.  Luckily, nothing I've lost will ruin me financially or academically.  And I have a 500GB usb drive that contains most of my stuff older than year or two back and a USB key that has most of my academic work on it.  This still hurts, but I've learned a valuable lesson.

---

