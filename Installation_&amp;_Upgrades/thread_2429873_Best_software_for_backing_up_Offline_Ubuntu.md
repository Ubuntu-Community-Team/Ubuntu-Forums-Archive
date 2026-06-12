---
title: "Best software for backing up Offline Ubuntu?"
date: 2019-10-24
forum: Installation &amp; Upgrades
---

### Post by giant-paw on 2019-10-24
Hi all !
This question is a little bit different from mainstream (i think).
I want to backup my Ubuntu system, but it's Offline system, it's not booted, it just resides on a hard drive. And I can't boot it because it's broken.

I want to backup my sole user, his password, and everything in command of Root, preserving read/write rights, all security etc., wi-fi settings and all network settings, Gnome settings, full Firefox backup, and Transmission with settings for example.

If I just copy all files, I'm afraid that would be insecure and there are also root's files which are not easily written or moved. And I'm a linux noob :confused:...
Very much thank you for hints.

---

### Post by TheFu on 2019-10-24
You are correct to think that just copying the files isn't sufficient.  Unix backups need to contain these things for each file:
* data
* owner
* group
* permissions
* ACLs
Just the data alone isn't enough for any files outside a single userid's HOME directory.

Boot from a Live Desktop Ubuntu system (flash drive), install whatever backup tool you want, connect and mount whatever backup storage you like and backup the files using sudo.  The target storage almost always needs to be formatted with a native Linux file system, so the owner/group/permissions are retained, along with the data. A few backup tools don't care about the target file system - **duplicity** and **fsarchiver** don't.

Some misconceptions need to be cleared up.  Not having a password for any userid isn't a big deal. If you have physical access to the system, you can always boot using grub option that provide root access and you can reset any password you like, unless the OS is encrypted. Encryption breaks all sorts of things, unless you know how to decrypt the storage.  User accounts and passwords are stored in /etc/ in the files that have *passwd* and *shadow* in the name.

I don't understand "everything in command of Root" - can you explain please?

Almost all system settings are stored in /etc/ somewhere.
All end-user settings are stored in the userid's HOME directory.  Personal gnome and firefox settings are there.  I don't use transmission, but doubt settings would be outside the HOME. 

This will all be a challenge for a noob.

I don't backup the OS on any of my systems.  I backup only information needed to recreate the OS as it was. My restore process starts by performing a fresh install using the current ISO for the Ubuntu version I want.  This means that swapping hardware, disks, networking, GPUs, doesn't matter to my backup/restore methods.  I certainly don't care what a password was 4 yrs ago.

I worry that you are thinking in the Windows way where their are magic files hidden in odd places.  That isn't how Unix works.

On my laptop, I backup these areas:
```
--include /root
--include /etc
--include /var/www
--include /var/log/nginx
--include /var/lib/awstats
--include /usr/local
--include /home";
```
I do webapp development, so that's why I grab anything under /var/ at all.
/root/ is where I place system hardware and crontabs and storage setup and lists of manually installed packages. 
/etc/ is where system settings are stored. This is more for reference than anything else.
/usr/local/ is where I put manually installed programs/scripts that are loaded outside the package management system.
/home/ is where local account data is stored for local users.  I have some LDAP users which use NFS for their HOME directories. Those are backed up on the NFS server.

I use **rdiff-backup**, but there are 20+ other, reasonable, choices.  rdiff-backup needs for the target storage to be native Linux, I think.  **rsync**, **rbackup**, **rsnapshot** do as well, because they use hardlinking for versioning.  Today, it really isn't worth our time NOT to have versioned backups.  

IMHO.

---

### Post by giant-paw on 2019-10-24
> **TheFu said:**
> The target storage almost always needs to be formatted with a native Linux file system, so the owner/group/permissions are retained, along with the data. 
.
There's some like btrfs and ext4, is ext4 OK for this task?

> **TheFu said:**
> I don't understand "everything in command of Root" - can you explain please? 
I guess everything that normal user can't access.

> **TheFu said:**
> On my laptop, I backup these areas:
```
--include /root
--include /etc
--include /var/www
--include /var/log/nginx
--include /var/lib/awstats
--include /usr/local
--include /home";
```
Thanks for these, I'll probably use everything listed except /var.

Thanks for your reply, It really helpful. I'm now looking into official repos Ubuntu backup-ers, or Rsync since it's so good with Grsync, or Fwbackups / Simple Backup Suite.

I'm also curious, which type of files are the best for keeping backups, one big file or a folder with each one file visible, or specific extensions?

---

### Post by TheFu on 2019-10-24
> **giant-paw said:**
> There's some like btrfs and ext4, is ext4 OK for this task?


I wouldn't use btrfs for anything, but I'm biased. There were issues with data loss and caveats against using btrfs for any virtualization needs.  ext4 is fine.  Avoid exFAT, FAT32, NTFS. File systems that support native Unix permissions and ACLs are what we want for backup storage.

> **giant-paw said:**
> I guess everything that normal user can't access.

Huh?  You've lost me.  What any userid can access is 100% controlled by the file permissions, groups, owner and ACLs. There isn't anything else.

> **giant-paw said:**
> Thanks for these, I'll probably use everything listed except /var.

My list is a starting point. What you need is dependent on your situation.  On some of my servers, I don't bother with /home/ at all, but need /opt/ and /var/lib/.  What is needed, depends on what is running on a system.  You never need /proc/ or /sys/ or any other pseudo-file systems.

> **giant-paw said:**
> Thanks for your reply, It really helpful. I'm now looking into official repos Ubuntu backup-ers, or Rsync since it's so good with Grsync, or Fwbackups / Simple Backup Suite.

grsync isn't a backup tool.  rsync can be tricked into being a backup too, but not without lots of effort.  rdiff-backup is basically rsync with built-in versioning.  The most recent backup appears as a mirror, so restoring 1 file or a directory from the backup last night is trivial. A copy/scp is all that is needed.  Going back 23 days or 62 days or 129 days and getting files isn't much harder, but using the rdiff-backup tool for that is the easiest way.  rdiff-backup is highly efficient with storage.  60 days of versioned backups needs about 1.2x the original storage for the data backed up.

Don't forget to capture a list of manually installed packages somewhere in the backup data, so you don't have to rediscover what you want installed.  **apt-mark showmanual** is the command for that.  Just redirect the output into a file that is somewhere in your backed up data.  

> **giant-paw said:**
> I'm also curious, which type of files are the best for keeping backups, one big file or a folder with each one file visible, or specific extensions?
Huh?  The backup tool controls that.  Also, Linux doesn't have file extensions.  Any extensions are for humans only, completely optional.  Linux isn't Windows even if it might seem similar from a quick look.

---

