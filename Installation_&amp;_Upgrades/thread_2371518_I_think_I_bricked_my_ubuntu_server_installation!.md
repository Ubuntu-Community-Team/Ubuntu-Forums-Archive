---
title: "I think I bricked my ubuntu server installation!"
date: 2017-09-15
forum: Installation &amp; Upgrades
---

### Post by bobis on 2017-09-15
Hi,

I had made an rsync backup of /var/* , /root/* and /etc/* folders to my external hard disk few weeks ago and now that I want to turn on my ubuntu server again, I executed a restore command. My external disk is mounted @ /home/bob7/diskos_d/EXHDD/

The restore command was this:

```
rsync --delete --update -aP /home/bob7/diskos_d/EXHDD/pc-server-backup/etc/ /etc/ &&
rsync --delete --update -aP /home/bob7/diskos_d/EXHDD/pc-server-backup/root/ /root/ &&
rsync --delete --update -aP /home/bob7/diskos_d/EXHDD/pc-server-backup/var/ /var/
```

But after the end of this command , I cannot login to putty/ssh , I see the (Network error: Software caused connection abort) error message. 

Also, I cannot login physically because the monitor says:

```
Ubuntu 16.04.3 LTS SERVER-PC tty1
 
SERVER-PC login: [COLOR=#ff0000]root[/COLOR]
 
Login incorrect
SERVER-PC login:    _  
```

...as if the root account or everything I tried to login is bricked! 

How to fix this? only with clean installation or a hotfix is available?

Why the restoring of /etc/* and /var/* folder caused the "brick"? How to do the restoration properly without hurting the OS next time?

My files (the server backups) , fortunately , are safe to my exernal disk right now.

Thank you!

---

### Post by TheFu on 2017-09-15
a) there is no root login for Ubuntu systems.  Login as your normal userid, then use sudo.  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) explains.

b) If the external disk wasn't formatted with a Unix/Linux file system, all that data was lost.  You need to get the permissions back, somehow.  I would just reinstall.  There isn't any script.

c) If you backup without using sudo, ownership, group and permissions for files you don't own are lost.  rsync is an amazing tool, but it is NOT a great backup tool.  Use a backup tool for that - one that retains permissions, ownership, groups, ACLs, as those change over time and supports versioned backups.  rsync can fail when there is file corruption too - having a backup f a corrupted file, isn't really very useful. But if you have 120 days of backups and the corruption happened 35 days ago, you are good. Just restore the file from 36 days ago.  I prefer rdiff-backup, which is a mix of rdiff and rsync. The last backup is just like an rsync mirror, but with the permissions and other things stored in metadata files also captured.  There are other tools, like duplicity, worth your consideration too.

How to restore?  Always boot from alternate media and restore that way.

I'm not so sure that your external disk is safe. If it has NTFS or FAT32, it isn't.

---

### Post by bobis on 2017-09-15
Well, I tried logging in physically via a user in terminal and succeeded logging as root via "su"


I tried booting from a spare USB flash drive, the live kali linux and found out from Gparted that /dev/sda1 is formatted as EXT4 , no NTFS. 

The system disk is[SIZE=2][FONT=arial] a WD1003FZEX CAVIAR BLACK 1TB 3.5''[/FONT][/SIZE] , formatted as EXT4. 

The external disk is a new one , bought 1 month ago, WD10JPVX BLUE 1TB 2.5'' , formatted as NTFS and connection is via USB with a help of a case.

I also issued a "chmod o-w /root/Desktop/etc/sudoers" because I have mounted sda1 (the system ubuntu device disk) @ /root/Desktop of kali and maybe the sudo is fixed from the following error of
```
sudo: /etc/sudoers is world writable
sudo: no valid sudoers sources found, quitting 
sudo: unable to initialize policy plugin
```

But still cannot access ssh or samba , even though the server has access to the internet (ping commands responds to any internet IP) I think it is corrupted for good and I will go for OS reinstall, unless I find a way of fixing the /var/* and /etc/* folders somehow.

---

### Post by TheFu on 2017-09-15
Installed Linux doesn't use NTFS. It cannot. One of the many supported Linux file systems is mandatory.
The external disk being NTFS lost all the permissions for all the files, and you overwrote them.  **Time to reinstall.**

Please don't use kali as a daily use distro. It has 1 purpose - penetration testing.  Using it for any other purpose is asking for lots of trouble and to be hacked.

In Unix-like systems, backups aren't just about the data. The permissions, owner, group and ACLs are absolutely critical.  Without those, you don't have a backup. You have some data that can be referenced, maybe.

A little knowledge is dangerous.

---

