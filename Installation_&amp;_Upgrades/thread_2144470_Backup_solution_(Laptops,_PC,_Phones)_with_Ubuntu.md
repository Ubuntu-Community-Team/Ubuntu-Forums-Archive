---
title: "Backup solution (Laptops, PC, Phones) with Ubuntu"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by theork on 2013-05-12
Hi Community,

I hope this fits the "installation" section, please move to another board if the topic is inappropriate here.

We are running the following devices at home:
1 FritzBox Router with Printer connected via USB
1 Multimedia PC Xubuntu x64bit (DVB-T, DVD/BluRay/mp3 archive), also has connected 3TB Harddrive for all the backups
2 IBM/Lenovo Laptops on Xubuntu (Firefox, Thunderbird, Lightning calender)
2 Mobile Phones (Android / Cyanogen)

Currently all kinds of backups are done by hand (e.g. export phones contacts and calender to a file, copy file to external harddrive, ...) but I would like a solution that does a backup of both laptops and both mobile phones, as soon as they connetc to the W-Lan. I come home, my Laptop logs in, it updates the changed files to the 3TB harddrive. I would like to be able to retrieve single files oder versions, as well as my whole Xubuntu installation in case something goes horribly wrong with the Laptop.

I have read quite a lot this weekend about the different backup solutions for ubuntu
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I also came across some nice tutorials on how to use OwnCloud to synchronize Android Phones with Thunderbrid Calender oder Backup a folder into OwnCloud:
[http://torbjoern-klatt.de/article/2012/04/08/owncloud-plus-thunderbird-plus-android-equals-perfect-sync/](http://torbjoern-klatt.de/article/2012/04/08/owncloud-plus-thunderbird-plus-android-equals-perfect-sync/)
[http://stadt-bremerhaven.de/owncloud-schritt-fuer-schritt-kontaktekalender-unter-android-synchronisieren/](http://stadt-bremerhaven.de/owncloud-schritt-fuer-schritt-kontaktekalender-unter-android-synchronisieren/)

But wouldn't I have to do a backup of the whole OwnCloud thing, to a seperate harddrive, too? How do I limit all this traffic to my home network? How do I initiate it automatically? Do I have to set up another PC or could all this run on the multimedia PC we have?

But to be honest, this is information overload for my poor brain... I have no idea whatsoever where to start. I know how to set up a basic LAMP, guess I could install OwnCloud and all the apps required, but... What is a good strategy to accompish this backup plans? What are the pitfalls? Where to start? 

:confused:

P.S.: If we accomplish this, I am more than willing to write a tutorial :)

---

### Post by TheFu on 2013-05-12
I follow the KISS principle for backups.
* 1 HDD is for receiving backups from all devices on the network.
* From Linux machine, I use rdiff-backup either local or over the network.
* A subdirectory on the backup HDD is shared via Samba to a each other machine - Windows, Android, whatever. A different subdirectory per different machine, so there is no risk of accidentally overwriting the wrong files or a local user accidentally accessing files from backups of other machines.
* From non-Linux machines, I use whatever the OS provides for backups and write to the network drive. "Home" versions of Windows don't support this, but Pro/Ent and Ult do.
* From android, there is a built-in backup tool in ADB. I think this only works over USB and only in "developer" mode. It supports bare metal restores and will backup everything except SMS messages. Android 4.2+ required.  The backups are tgz and encrypted; basically an image. Written to the backup HDD too.

Simple.

I avoid image-based backups unless they are absolutely necessary.  Daily rdiff-backup jobs run from 2am-3am nightly. 100% automatic.  Android backups are manual today since the device requires a password be entered. For me, that is acceptable, it is the lack of versioned backups that I find bad.  I guess Titanium Backup and any of the automation tools could be used on a root'd device to backup selected stuff and push the backups somewhere else. Since 4.x, I haven't needed to root Android.

Your needs mgiht be different.

---

### Post by theork on 2013-05-13
O.K. so i will:

Install Samba Server on our multimedia PC (it's switched on all the time anyway to record TV) and limit access to the local network somehow.
Make a WebDav connection available for each device to seperate folders.
Install backup software that can use WebDav on each device. (rdiff-backup?)
Then I also do a backup of the Backup Drive to a second drive (rdiff-backup?)

Will try that on the weekend (unless other suggestions are posted, too)  Thank you.

P.S.: What do people need things like "OwnCloud" for, if it can be done that easilie without?

---

### Post by TheFu on 2013-05-13
Don't use webdav! The security of it has been broken multiple times.

rdiff-backup uses ssh with keys perfectly. THAT is what you should use.  ssh is secure on LANs and over the internet. With ssh, you don't need any other port open on your systems.  If you want to connect from the internet back into your home network, be sure to run something like fail2ban or denyhosts to protect your ssh connection.  [http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) will explain a little.

There is no need for Samba for any of the Linux PCs, just the non-UNIX platforms.

OwnCloud is for people who 
* trust 3rd parties with all their data
* want step-by-step directions
* are afraid to type 20 commands
* OwnCloud has advertising. ssh doesn't.

---

### Post by theork on 2013-05-13
I run rdiff-backup on the PC that I want to backup and connect to the main PC via ssh? What do i actualy have to install on the target machine hosting the backup drive? And ADB is only via USB. Guess I will search the Android Market for an App that works once I got the PC backup running.

Why do I have to trust 3rd Parties with my Data? I thought the advantage of OwnCloud is that I do not have to use dropbox, wuala, iCloud but run the could software myself on a box I own at home?

---

### Post by TheFu on 2013-05-13
> **theork said:**
> I run rdiff-backup on the PC that I want to backup and connect to the main PC via ssh? What do i actualy have to install on the target machine hosting the backup drive? And ADB is only via USB. Guess I will search the Android Market for an App that works once I got the PC backup running.

Why do I have to trust 3rd Parties with my Data? I thought the advantage of OwnCloud is that I do not have to use dropbox, wuala, iCloud but run the could software myself on a box I own at home?

[http://www.nongnu.org/rdiff-backup/index.html](http://www.nongnu.org/rdiff-backup/index.html) will explain, but I'll try.
Secure connections on UNIX/Linux are almost always made over ssh.  That means anything that ssh supports, these tools will also support. I think this is smart.
rdiff-backup is based on rdiff and librsync. Since librsync supports ssh, so does rdiff-backup.  It is such a great idea that using ssh for machine-to-machine connections is the default.

What do you need to install to use rdiff-backup?  Well, on APT-based Linux systems, dependencies should be included in the package and should be installed automatically.  I don't know if ssh is listed or not, since installing an ssh-server is in the top 3 things I do on **every** Linux/UNIX machine I run - well before backups.  That is it.

OwnCloud - which I have never used - doesn't require any ports to be open on the firewall. If my understanding is correct, that requires a 3rd party running on the internet to proxy connections so a client and server can create their own connection and pass through firewalls. That 3rd party must be trusted.  OTOH, I could be completely wrong.

Other programs that like to use ssh for their connections are:
* sftp
* scp
* winscp
* putty
* rsync ( and any of the 20-50 programs based on this fantastic tool )
* Android versions of ssh, scp, sftp

In my book, rsync and ssh rate in the human invention list with creating fire and the wheel. These tools are THAT great.  Be certain you learn about the ~/.ssh/config file to make your life easier.  Also ssh-keygen and ssh-copy-id make life easier, more convenient AND much more secure.

---

