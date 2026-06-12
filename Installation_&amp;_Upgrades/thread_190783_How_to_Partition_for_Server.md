---
title: "How to Partition for Server?"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by leetcharmer on 2006-06-06
I have 3 hard drives: 1) 80GB IDE 2) 80GB IDE 3) 250GB IDE Hardware RAID

I want to make an effective LTSP and SAN (Storage Area Network) server and I need help effectively partitioning my hard drives.

Here's what I was thinking:
/ & swap = 1st 80GB
/home = 2nd 80GB
?? = 250GB (any ideas what this should be mounted as for a storage drive?)

I've seen others make separate partitions for /var (web server) and /usr (not sure why) -- are those wise to consider?

---

### Post by tomski on 2006-06-06
i would put / on the first master/primary hard drive & put the swap on the master/primary hard drive on the second ide/sata channel just to aid performance (less is best = no cd drive!)
if you dont want a web server then dont bother to have /var on a seperate partition
/usr is where most packages are installed , so again with any server the aim is to have only what you need to run or cope with the task, so dont bother with a seperate /usr unless you need it (application server!)
a seperate /home is good for a remote home dir, so less disk space is used on the clinet be it win or linux
/public could be a good candidate for the 250gb raid drive, you could serv it as a nfs share;
 i have a linux box as a firewall with a nfs share (50gb) that i access from a local linux box & a remote windows pc (services for unix installed) in portsmouth
i just installed webmin to configure it all along with a good ssh server for emergencies or non gui

---

### Post by rcarring on 2006-06-06
Do this

RAID 1 first two IDE drives giving you 80GB, put root and swap on these. Data will write to both so if one dies the other should be able to keep going.

RAID 5 on the next four drives, assuming that you have four drives each 250GB giving you 250GB in all available.

Place /Home on RAID 5

Data is the most important as you can always buy two new 80GB disks and RAID1 them. Schedule regular backups.

One question, if you do put /home on the RAID 5 drive how are you going to backup up to  250GB of data? Would you close off the system for an hour to copy the data off to a separate backup?

How would you cope if a user trashes their /home folder and wipes out their documents? Would you be able to restore an individual users data to their own folder including email?

Just some questions that sprung to mind.

---

### Post by leetcharmer on 2006-06-07
[QUOTE=tomski]i would put / on the first master/primary hard drive & put the swap on the master/primary hard drive on the second ide/sata channel just to aid performance (less is best = no cd drive!)
if you dont want a web server then dont bother to have /var on a seperate partition
/usr is where most packages are installed , so again with any server the aim is to have only what you need to run or cope with the task, so dont bother with a seperate /usr unless you need it (application server!)
a seperate /home is good for a remote home dir, so less disk space is used on the clinet be it win or linux
/public could be a good candidate for the 250gb raid drive, you could serv it as a nfs share;
 i have a linux box as a firewall with a nfs share (50gb) that i access from a local linux box & a remote windows pc (services for unix installed) in portsmouth
i just installed webmin to configure it all along with a good ssh server for emergencies or non gui[/QUOTE]

What are the benefits of NFS? Also, is /public a pretty usual mount for a 'storage' center?  What I had in mind was to create an LTSP which would utilize the /home drive (2nd 80GB) for stuff, and the 250 would store backups of all the user's /home accounts as well as be the storage spot for FTP server or just Remote data storage among windows and linux computers in the network.

---

### Post by sjpwong on 2006-06-07
[QUOTE=rcarring]RAID 5 on the next four drives, assuming that you have four drives each 250GB giving you 250GB in all available.

Place /Home on RAID 5[/QUOTE]

Something I have just found in my install today.  If you use RAID on a large drive (I was using RAID5 on 3x80GB partitions) make sure you wait until they have finished synching before you proceed with the installation.  Mine got correupted the first time and I think it's because the synchronisation hadn't completed.

Switch to the virtual console alt-F2 then use a command like

```
mdadm --detail /dev/md0
```

and look for the "Rebuilding" line which tells you the progress.  Wait until it is 100% ie disappears and the raid set says it is clean before proceeding with your install.

---

