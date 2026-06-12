---
title: "NAS server"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by MocroNL on 2012-08-29
Heey guys,

Iam trying to build up a NAS server so I can run backups of the network that I'am running. I already have 2 servers connected to each other with NFS, but I don't know what to do after that... Could someone post a link of a guide, explaining how to set up a NAS?? 

Thanks in advance.

---

### Post by MocroNL on 2012-08-30
Anyone??

---

### Post by darkod on 2012-08-30
Are you talking about simple network attached storage, or maybe you meant NFS? Because NFS is different.

For a simple file server you would use Samba, there are many tutorials on google. Here is from the ubuntu documentation:
[https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

---

### Post by Lars Noodén on 2012-08-30
It sounds like you already have a NAS set up using NFS.  What else would you need?  It's possible that you could add Samba and or SSHFS(SFTP) but if NFS is working for you, why change it?

---

### Post by MocroNL on 2012-08-30
True I have NFS working. But I wanna do a regular backup for my network, is that possible with NFS on ubuntu?? I'am familiar with windows server. There I could choose if i would do a incremental backup, on which days it would backup etc etc..

So my questions are:
Can i use NFS to do backups like in win 2003?
If not, which software should I use?

Thank you.

---

### Post by Lars Noodén on 2012-08-30
I wouldn't know what 2003 claims to be able to do.

But with NFS, you do have the ability to have a remote machine's directories and files available as if they were local.  So yes, using NFS you do have the files available for back up.  You could use [tar](http://manpages.ubuntu.com/manpages/precise/en/man1/tar.1.html) or [dump](http://manpages.ubuntu.com/manpages/precise/en/man8/dump.8.html) to get everything at once, but since you ask about incremental backups, you could use [rsync](http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html) to copy from your NFS mounted directory to your local backup directory.

```

rsync –avH --delete /path/from/source/ /path/to/destination/

```

rsync has many options and can even be used to make snapshots.  The nice thing about rsync is that it is fast because it copies only the changes and won't waste resources re-copying a whole file if it already exists at the destination.

---

### Post by MocroNL on 2012-08-30
Alright, thanks for the reply! I will try out rsync.

Greets.

---

### Post by Lars Noodén on 2012-08-30
Have fun.

Once you have worked out how you are doing your backup, then you can put it into a script and call it from [cron](https://help.ubuntu.com/community/CronHowto) so that it runs at a predetermined time.

---

### Post by MocroNL on 2012-08-30
So a "list" of to do things.

1. First make the server and client be able to communicate with eachother via NFS. 

2. Then use rsnyc for making backups.

3. Then write a script with cron that will automate the rsync backups ?

Iam not sure about 3 but that is what cron is for right?

Thanks in advance.

---

### Post by Lars Noodén on 2012-08-30
Yes, those are the steps.  The script is needed because it is much easier to have cron call a script than to try to have cron call a complicated series of programs with options.

cron's file format is a little funky but once you understand it, it is easy to work with:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

You can then use it to schedule all kinds of intervals.

---

### Post by MocroNL on 2012-08-30
Thanks for the enlightment. I will follow the steps and hope it will work!!

Greets.

---

### Post by MocroNL on 2012-11-21
This problem has been solved by making a backup.txt file that contains this list:

rsync -avhe ssh -varuzP  tls-ams-ns-02:/etc/bind/       /home/backups/tls-ams-ns-02

rsync -avhe ssh -varuzP  tls-ams-ns-03:/etc/bind/       /home/backups/tls-ams-ns-03

rsync -avhe ssh -varuzP  tls-ams-mon-10:/usr/           /home/backups/tls-ams-mon-10

rsync -avhe ssh -varuzP  tls-ams-mon-11:/opt/           /home/backups/tls-ams-mon-11

rsync -avhe ssh -varuzP  tls-ams-ws-01:/var/lib/        /home/backups/tls-ams-ws-01

rsync -avhe ssh -varuzP  tls-ams-ws-01:/home/fauser/    /home/backups/tls-ams-ws-01


And a crons.cron file that will automate the backup procedure.

crons.cron:

#Mins - Hours - Days - Months - Day of Week
0       23      *       *       *                /backup.txt

Sorry for the late reply!

Many thanks!!

---

