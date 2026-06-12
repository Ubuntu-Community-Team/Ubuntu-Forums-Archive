---
title: "start CUPS every reboot?"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by darco on 2009-10-09
My hp printer is not detected unless *I* start the cups service. How do I automate this after each reboot? I have reinstalled everything cups related to no avail.

thxs

darco

---

### Post by slakkie on 2009-10-09
cups is a service/daemon which should be started at boot. 

```

ls -altr /etc/rc?.d/* | grep cups
lrwxrwxrwx 1 root root  14 2009-08-06 03:41 /etc/rc5.d/S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  14 2009-08-06 03:41 /etc/rc4.d/S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  14 2009-08-06 03:41 /etc/rc3.d/S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  14 2009-08-06 03:41 /etc/rc2.d/S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  14 2009-08-06 03:41 /etc/rc1.d/K80cups -> ../init.d/cups

```

If it is not present, check if you have the cups package installed and/or create the symlinks (manually):

```

for i in {2..5} ; do
  sudo ln -s /etc/init.d/cups  /etc/rc${i}.d/S50cups
done
sudo ln -s /etc/init.d/cups /etc/rc1.d/K80cups

```

or via the update-rc.d command, which is the more official way.

---

### Post by darco on 2009-10-09
when I ran this command after a reboot:

```
ls -altr /etc/rc?.d/* | grep cups
lrwxrwxrwx 1 root root  14 2009-10-05 14:26 /etc/rc2.d/S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  14 2009-10-05 14:26 /etc/rc1.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root  14 2009-10-05 14:26 /etc/rc5.d/S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  14 2009-10-05 14:26 /etc/rc4.d/S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  14 2009-10-05 14:26 /etc/rc3.d/S50cups -> ../init.d/cups

```

I also reinstalled cups so I know its there....ran the symlink commands and I get a "file exist" reply for both.

darco

---

### Post by slakkie on 2009-10-09
is /etc/init.d/cups executable?

if not, sudo chmod +x /etc/init.d/cups

---

### Post by darco on 2009-10-09
Yes it is.....




darco

---

### Post by cariboo on 2009-10-09
Just to make sure cups is running, open a terminal and type:

```
ps ax | grep cups
```

you should see something that looks like this:

```
ps ax | grep cups
 1730 ?        Ss     0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
 2505 pts/0    S+     0:00 grep cups
```

If cups is running, access the cups interface at:

```
http://localhost:631
```

and make sure your printer is setup properly.

---

### Post by darco on 2009-10-10
> **cariboo907 said:**
> Just to make sure cups is running, open a terminal and type:

```
ps ax | grep cups
```

you should see something that looks like this:

```
ps ax | grep cups
 1730 ?        Ss     0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
 2505 pts/0    S+     0:00 grep cups
```

If cups is running, access the cups interface at:

```
http://localhost:631
```

and make sure your printer is setup properly.

but thats what my issue is about..it is NOT running.
I am trying to get it to auto run w/o me having to start cups manually.

```
 ps ax | grep cups
20703 pts/0    S+     0:00 grep --color=auto cups
```

The same printer runs perfectly in my 1st partition running Mint 7. I know this is Beta, just trying to work thru these problems.
thxs

darco

---

### Post by slakkie on 2009-10-10
Then you need to look into the logs to see why cups fails to start at boot.

---

### Post by tuggy on 2009-10-10
i'm having the same problem, which is quite annoying.
i tried to execute the S50cups file in rc5.d and this is the output i got:
```
 * Starting Common Unix Printing System: cupsd                                     
Warning: Fake start-stop-daemon called, doing nothing.

```

what does it mean?

---

### Post by darco on 2009-10-10
I checked the daemon.log and did a search for "cups" but nothing appeared. Is this the correct log?
In the dmesg log I see
[CODE]4.255639] type=1505 audit(1255137441.784:10): operation="profile_load" pid=459 name=/usr/sbin/cupsd/CODE]

thxs


darco

---

### Post by wizard10000 on 2009-10-13
I have the same problem.  There isn't anything in the log because as far as I can tell there isn't anything starting cups in the first place.  

I'm pretty sure I don't completely understand the difference between the old rcX.d system and upstart but I don't have an /etc/init/cupsd.conf so I imagine that's why it's not starting.

I came here looking for a fix to this problem and will keep reading but if this isn't bugged it probably needs to be.  If I can't find an answer here I'll be taking it to Launchpad  :)

---

### Post by wizard10000 on 2009-10-13
And apparently here's an answer.

[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/444597](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/444597)

---

### Post by darco on 2009-10-15
Woo Hoo!!....latest update (10/15) fixed my issue!.....

KK is just getting better and better.....


darco

---

