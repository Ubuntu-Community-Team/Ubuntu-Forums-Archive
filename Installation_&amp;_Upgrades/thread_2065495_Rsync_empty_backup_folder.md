---
title: "Rsync empty backup folder"
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by MocroNL on 2012-10-02
Hey guys. I just installed rsync and want to start a backup. It look likes it works but the folder I'am backing up to is empty after the backup.


This is the output I get after I start a backup.
opening connection using: ssh tls-ams-ns-03 rsync --server -vvulogDtprze.iLsf --partial . /etc/bind/
sending incremental file list
delta-transmission enabled
total: matches=0  hash_hits=0  false_alarms=0 data=0

sent 29 bytes  received 15 bytes  29.33 bytes/sec
total size is 0  speedup is 0.00

BAckup script(Backup.txt): sync -avhe ssh -varuzP /home/backups/ tls-ams-ns-02:/etc/bind/

By the way I'am backing up via ssh which is set up without using a password every time a backup starts.

Does anyone know why my backup folder is still empty?

Thanks in advance.

---

### Post by MocroNL on 2012-10-29
Bump! Can noone answer my mysterious question?:-\"

---

### Post by papibe on 2012-10-29
Hi MocroNL.

My first guess would be that the remote user doesn't have access to /etc/bind.

If that is not the case, I would try to do a full mirror (without the option -u).

BTW, since rsync uses ssh by defualt you can shorten your command to something like this:
```
rsync -avhzP /home/backups/ tls-ams-ns-02:/etc/bind/
```
Let us know how it goes.
Regards.

---

### Post by markbl on 2012-10-29
Why are both of you writing "sync" in your command line? Surely that should be rsync?

---

### Post by MocroNL on 2012-10-31
Heey, thanks for the reply!

I have tried: (rsync -avhzP /home/backups/ tls-ams-ns-02:/etc/bind/) But I got the same output. The rights of the map(bind) are 777 atm.

root@TLS-AMS-ST-12:/home/backups# rsync -avhzP /home/backups/ tls-ams-ns-02:/etc/bind/
sending incremental file list

sent 26 bytes  received 12 bytes  76.00 bytes/sec
total size is 0  speedup is 0.00

Greets.

---

### Post by papibe on 2012-10-31
That may be a correct output is there's nothing new to transfer.

Try forcing a change in a file, and then running rsync in order to see if it transfers it.

Another alternatice: create an empty file:
```
touch /home/backups/dummy.txt
```
Next time, rsync should transfer that file.

Let us know how it goes.
Regards.

---

### Post by MocroNL on 2012-11-01
Thank you papibe! It works and I now see what I did wrong.....

rsync -avhzP (/home/backups/)= Send (tls-ams-ns-02:/etc/bind/)= Receive.

I wanted to backup the /etc/bind into backups.

So It should be like this?
rsync -avhzP tls-ams-ns-02:/etc/bind/ /home/backups/ 

Because I dont wanna make a script on every server that I'am going to backup...

Many thanks!

---

### Post by papibe on 2012-11-01
:D Glad your sort it out.

Please mark this thread as SOLVED (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

