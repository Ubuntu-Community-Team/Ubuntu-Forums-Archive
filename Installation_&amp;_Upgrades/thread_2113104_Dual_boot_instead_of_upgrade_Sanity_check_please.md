---
title: "Dual boot instead of upgrade? Sanity check please"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by gurlinux on 2013-02-06
Hello, I'd appreciate if any guru can sanity-check my upcoming weekend project:

I have a very critical -and happily stable- Oneiric machine acting as a home server. With end-of-support just around the corner it's time to move on, so I decided to upgrade to Precise just because it's LTS and should provide me with long-term stability.

My main concern right now is about the upgrade process, which I want to approach in the safest possible way. And nothing sounds safer to me than the possibility to fully roll back in case of the unexpected. HENCE, behold the dual boot!!

The only problem I have right now is that I do not have an available partition on the main HDD (sda) where the OS should reside. This is how it looks:
Filesystem   Size   Used   Avail   Use%   Mounted on
/dev/sda2   19G   3.2G   15G   19%   /
/dev/sda1   92M   29M   59M   33%   /boot
/dev/sda3   54G   13G   38G   26%   /home
/dev/sdb1   917G   550G   368G   60%   /mnt/bigdisk

My plan is as follows:
1-perform a good backup of all the system files I will need. Also backup everything in /boot/grub manually
2-boot with a Precise DVD or USB
3-gparted, shrink sda2 to half the size, create a new partition on the newly available space (I took a hint [**_from here_**]("http://forums.linuxmint.com/viewtopic.php?f=46&t=124706#p682916") where it creates an extra partition for testing distros)
4-reboot, check my "old world" still works
5-reboot with Precise DVD or USB, install on new partition created in step 3
6-restore system files as needed
7-very possibly, recreate customizations? (cron jobs, init.d autostarted services, etc, etc...)

The good news is that I shouldn't worry too much about the /home data directory, as it's already in its own partition.

If something does go wrong, or I get lost in the way, I can restore my /boot/grub files and my "old world" should be back in business until I figure out -and correct- whatever problem I had.

Soooooo finally... DID I MISS ANYTHING????? 

THANKS for your help!

---

### Post by Mark Phelps on 2013-02-06
I have been "upgrading" Ubuntu versions for years and ALWAYS do it with having one version on one drive, and the new version on a separate drive.

Why?

Because, when you upgrade in-place, you never know what kind of problems will result, and while some of them might be easily fixed, others could be very hard, or impossible, to fix.  And, in the meantime, if you upgraded the only Ubuntu version you had, you now have a "broken" Unbuntu install.

Also, to this day, Canonical STILL does not provide any easy way to "rollback" an update such that, with a single click or selection, you could replace your new "broken" installation with your previous "working" installation.

If you don't have the multiple drives option, you could use Clonezilla to image off your current install to an external drive, at least that way, if things go really bad, you will have a working version from which to restore.

---

### Post by oldfred on 2013-02-06
I am no expert on servers. It looks like a server install uses a lot less space than the desktop with its gui. But you must not have installed a lot of apps.

I would make a list of installed apps. This is a (long) text file & you should review for obsolete apps that you do not want to reinstall. It may pick up old kernels or apps that have been replaced with totally different equivalents.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

    
Servers often are systems that need a separate /boot as they may have RAID, LVM or specially formatted partitions. Yours looks generic and you may not even need the separate /boot. Then your test install would not overwrite the /boot partition and you could still boot old install?

       More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by gurlinux on 2013-02-06
Oldfred: I should have noted that while I call it a "server", it technically is a full-blown desktop. But one of the services it runs is x11vnc, so I can remotely "see" the desktop and do whatever I want. So for all intents and purposes, it's a plain desktop with a bunch of apps and services running 24x7.

By what I see from both replies, it looks I'm somewhat on the right track. It will HAVE TO BE a fresh installation, and a reconstruction later to bring each and every service back to life. I'll have to be diligent in backing up every configuration file needed (as I supposed in my original step 7 task list)

The key point to the process, as I see it, will be the re-sizing of the sda2 ("/") partition, leaving the data in it intact. **Does anybody see any concerns here?** :-k

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by oldfred on 2013-02-06
Any time you edit partitions you can create problems. That is why we always suggest backups. But most do not have issues. I have accidentally overwritten the wrong partition, so user error is ofter the biggest issue.

As long as you do not have partition over 75% or 80% full you should be ok.

---

### Post by gurlinux on 2013-02-06
> **oldfred said:**
> 
As long as you do not have partition over 75% or 80% full you should be ok.

That should be fine then: sda2 is sitting at only 19% usage

All in all, here's my updated plan, written here for posterity:

1-perform a good backup of all the system files I will need. Also backup everything in /boot/grub manually
2-boot with a Precise DVD or USB
*[COLOR="Red"]2a-fully backup the HDD partitions in sda to sdb using **dd** as indicated above by **ahallubuntu**[/COLOR]* (just in case :D )
3-gparted, shrink sda2 to half the size, create a new partition on the newly available space (I took a hint from here where it creates an extra partition for testing distros)
4-reboot, check my "old world" still works
5-reboot with Precise DVD or USB, install on new partition created in step 3
6-restore system files as needed
7-*[COLOR="Red"]install my needed apps [/COLOR]*and recreate customizations for each and every app (cron jobs, init.d autostarted services, etc, etc...)

And above all, be confident... ;)

Thanks!

---

### Post by oldfred on 2013-02-06
If you have to restore a backup created with dd, be sure to restore size of partition first. dd is a bit for bit copy and does not know about anything. It just goes out and does its thing but if you are not careful it can overwrite something you do not want overwritten. And since it copies all bits even zeros there is no way to repair.

I have only used dd to inspect MBR or PBR sectors. 

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

    
Old school way is tar, which I only used to compress a log file & upload it.
       Tar backup script:
[https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html)

---

### Post by darkod on 2013-02-06
Forget about dd and better use something like rsync, cp, or fsarchiver. Why would you use a sector by sector copy command?

You only need to copy the files, keeping ownership and permissions. A simple cp -ax can do that (I have used it to move my /home partition from hdd to ssd, all permissions and ownership was kept).

Also, you mentioned restoring /boot/grub, but if you are in effect doing a new 12.04 clean install, I would leave boot as folder on /. Do not try to use your current /boot partition, not without formatting it. Different versions have different files in /boot, so take that into account.

You also mentioned "restore system files as needed". I have no idea what you mean by that, but not many system files can be restored from 11.10 to 12.04. If we are talking about samba shares for example, yes, you can copy the smb.conf in most cases.
But the generic default system files, I wouldn't try copying them to 12.04 from older version.

It's good that you are thinking ahead and trying to protect yourself from failure, but don't over do it and turn paranoid. :)
Backup your data, most important settings, and that's it. You are planning a clean install of 12.04 to new partition in any way, not an upgrade of the current system. If you get the partition shrink right, not many things can go wrong.

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by darkod on 2013-02-07
> **ahallubuntu said:**
> Because it's simple to do.  As I said, it's also inefficient.  I rarely use it anymore for this.

Note that people asking questions are doing it because they don't know. I don't think we should suggest the simplest solution, but the best one.

> Copying /home is much different than trying to copy /var.

Could you elaborate more about this, for information. What is the difference if permissions and ownership are kept?

Linux is generally very flexible. If you copy the files by keeping permissions, set the mount point correctly, it would usually work.

---

