---
title: "Does 14.04.1 provide TRIM in fstab for Intel SSDs / where's Nvidia driver"
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by Rizlaw on 2014-07-26
I got tired of waiting for an LTS upgrade notification to update from 12.04.4 to 14.04.1, so I did a fresh install of 14.04.1 to /root and left my /home partition intact.

I have read that during a new installation of 14.04, the installer automatically recognizes Intel and Samsung SSDs and provides the necessary TRIM command as a chron job. I've never used chron jobs so I'm not sure where that chron job file is located to verify that my Intel SSD has been properly recognized and a "discard/trim" chron job properly activated in my new 14.04.1 install.

Q1. How/where do I verify that my Intel SSD has a chron job for Discard/Trim?

I also noticed that my new "fstab" file no longer shows the "discard" option for my Intel SSD. It simply shows "errors=remount -ro   0   1"
In my old fstab file, I manually entered the "discard" option to enable trim: "discard,noatime,nodiratime,errors=remount -ro    0  1".

Q2. Should I manually edit my "fstab" file and add the "discard" option to be sure it's working correctly?



Thank for any helpful input.

---

### Post by QIII on 2014-07-26
Hello.

Trim is enabled in the kernel by default for at least Intel and Samsung SSDs.  Maybe more by now.  

There should be a job in /etc/cron.weekly.  I moved mine to cron.daily.  I modified mine to trim / and /home.

I've seen arguments both ways for discard in fstab.  I figure just leaving the cron job is good enough.

As for your video driver question, it might be better to start a new thread since that is a completely different subject.

---

### Post by Rizlaw on 2014-07-26
Thanks QIII.

I presume that running the command "gksu nautilus" and then moving the "fstrim" file from the weekly folder to the daily folder is what you mean?
Since I only have two partitions on my Intel SSD ( / and /home) I'm not sure there is I need to edit the file as it seems that it will simply perform trim on any Intel and Samsung SSD partitions that it finds; in my case, I only use /root and /home on my SSD, no swap, etc. If I'm wrong, what code did you use to limit "trim" to your /root and /home partitions?

---

### Post by Rizlaw on 2014-07-26
Thanks QIII.

I presume that running the command "gksu nautilus" and then moving the "fstrim" file from the weekly folder to the daily folder is what you mean?
Since I only have two partitions on my Intel SSD ( / and /home) I'm not sure there is I need to edit the file as it seems that it will simply perform trim on any Intel and Samsung SSD partitions that it finds; in my case, I only use /root and /home on my SSD, no swap, etc. If I'm wrong, what code did you use to limit "trim" to your /root and /home partitions?

---

### Post by oldfred on 2014-07-27
I just created new trim command in 12.04. I have not checked nor added it yet to my 14.04, but need to as I hope to convert to my 14.04 install shortly.

 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim

   #!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

Running trim manually gives me this:

   fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

---

### Post by QIII on 2014-07-27
@Rizlaw

> 
I presume that running the command "gksu nautilus" and then moving the "fstrim" file from the weekly folder to the daily folder is what you mean?

Yes. Or using sudo mv ... in the terminal.

oldfred:

Looks about like mine ...

```
#!/bin/sh
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
fstrim -v /home >> $LOG


```

The argument I have heard against discard is that it is continually doing it, thus decreasing the response of the SSD.  I don't know how much that little bit of work would really affect any given operation.  SSDs are pretty darn fast.

---

### Post by Rizlaw on 2014-07-27
> **oldfred said:**
> I just created new trim command in 12.04. I have not checked nor added it yet to my 14.04, but need to as I hope to convert to my 14.04 install shortly.

 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim

   #!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

Running trim manually gives me this:

   fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

Thanks Oldfred,

Actually, I did have the Webup8 post [http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html]("http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html")  about SSD trimming bookmarked in my browser and completely forgot about it because I had enabled the "discard" option in my /etc/fstab file. I have now created a daily trim cron job:

```
#!/bin/sh
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
fstrim -v /home >> $LOG
```

 and tested it and got a result very close to yours. It appears to work.

 However ........

I forgot to mention that when I installed 12.04 two years ago, I selected the option to encrypt my /home directory. Later I realized that, for me, this was a mistake. I haven't been brave enough to try and remove the /home encryption. I've read several recommendations on how to do it, but none of them are clear enough to convince me that it can be done safely. IMO is should be as simple as entering the uniquely generated long encryption passphrase and clicking on an unencrypt button. Anyway, my current clean install of 14.04.1 has left the encryption intact.

The Webup8 post says, without explanation, that for encrypted partitions you need to add more code for the daily trim cron job to work properly. This confuses me since I have already been using "discard" in my 12.04 fstab file for more than two years, with no apparent ill effects. When I look at the simple code in the default 14.04.1 Ubuntu weekly cron job file:

```
#!/bin/sh
# call fstrim-all to trim all mounted file systems which support it
set -e

# This only runs on Intel and Samsung SSDs by default, as some SSDs with faulty
# firmware may encounter data loss problems when running fstrim under high I/O
# load (e. g.  https://launchpad.net/bugs/1259829). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives.
exec fstrim-all
```

I don't see anything like the extra encryption code mentioned in the Webup8 instructions.  So, I'm assuming that I don't need the added encryption code recommended by Webup8. Would you agree or disagree?

Also, should I remove the "execute" option from the weekly trim cron job now that I've enabled a daily trim cron job? Or, should the I leave it alone and let both trim cron jobs execute daily and weekly?

Thanks.

---

### Post by Rizlaw on 2014-07-27
Thanks QIII for your answer in post 6.

I added a daily trim cron job just like yours. But my concern is that I did not take into account my encrypted /home directory. It seems a Webup8 post suggests that I need to add more code for the encrypted /home partition. I'm not sure about that: see my response in post 7 to "Oldfred's" post 5 above.

Thanks again.

---

### Post by impliedconsent2 on 2014-07-27
> **Rizlaw said:**
> 
```

# This only runs on Intel and Samsung SSDs by default, as some SSDs with faulty
# firmware may encounter data loss problems when running fstrim under high I/O
# load (e. g.  https://launchpad.net/bugs/1259829). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives.
```

I only point out that comment for those without Intel or Samsung drives (like my OCZ) and works fine on a cron.weekly.

---

