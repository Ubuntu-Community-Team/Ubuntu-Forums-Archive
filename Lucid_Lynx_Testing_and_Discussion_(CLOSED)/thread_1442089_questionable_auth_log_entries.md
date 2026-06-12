---
title: "questionable auth log entries"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andrewthomas on 2010-03-29
I originally posted this in the security discussions forum and it was suggested that I post it here instead.  
[http://ubuntuforums.org/showthread.php?p=9045972](http://ubuntuforums.org/showthread.php?p=9045972)

I got some entries in my auth log that I am puzzled by.  What could be  the cause?  I was not using my machine at the time of the logging.  Any  ideas?

```
Mar 27 16:43:20 ASUSm3a32MVP su[10582]: Successful su for andrew by root
Mar 27 16:43:20 ASUSm3a32MVP su[10582]: + ??? root:andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10582]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:43:20 ASUSm3a32MVP su[10582]: pam_unix(su:session): session closed for user andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10597]: Successful su for andrew by root
Mar 27 16:43:20 ASUSm3a32MVP su[10597]: + ??? root:andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10597]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:43:20 ASUSm3a32MVP su[10597]: pam_unix(su:session): session closed for user andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10618]: Successful su for andrew by root
Mar 27 16:43:20 ASUSm3a32MVP su[10618]: + ??? root:andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10618]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:43:20 ASUSm3a32MVP su[10618]: pam_unix(su:session): session closed for user andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10639]: Successful su for andrew by root
Mar 27 16:43:20 ASUSm3a32MVP su[10639]: + ??? root:andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10639]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:43:21 ASUSm3a32MVP su[10639]: pam_unix(su:session): session closed for user andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10942]: Successful su for andrew by root
Mar 27 16:57:33 ASUSm3a32MVP su[10942]: + ??? root:andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10942]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:57:33 ASUSm3a32MVP su[10942]: pam_unix(su:session): session closed for user andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10957]: Successful su for andrew by root
Mar 27 16:57:33 ASUSm3a32MVP su[10957]: + ??? root:andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10957]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:57:33 ASUSm3a32MVP su[10957]: pam_unix(su:session): session closed for user andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10978]: Successful su for andrew by root
Mar 27 16:57:33 ASUSm3a32MVP su[10978]: + ??? root:andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10978]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:57:33 ASUSm3a32MVP su[10978]: pam_unix(su:session): session closed for user andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10999]: Successful su for andrew by root
Mar 27 16:57:33 ASUSm3a32MVP su[10999]: + ??? root:andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10999]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:57:33 ASUSm3a32MVP su[10999]: pam_unix(su:session): session closed for user andrew
Mar 27 17:00:10 ASUSm3a32MVP gdm-session-worker[1347]: pam_unix(gdm:session): session closed for user andrew
```

---

### Post by andrewthomas on 2010-03-30
Could this have anything to do with ACPI support?  I just remembered that I recently enabled an option in BIOS  for ACPI APIC support because I was going to test if I could use hibernate instead of turning off my computer.  I never got around to trying this, but I noticed that around the time that I had the questionable use of su, the computer was put to sleep.  Is this normal?


```
Mar 30 15:09:01 ASUSm3a32MVP CRON[4437]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar 30 15:10:51 ASUSm3a32MVP anacron[4495]: Anacron 2.3 started on 2010-03-30
Mar 30 15:10:51 ASUSm3a32MVP anacron[4495]: Normal exit (0 jobs run)
Mar 30 15:10:51 ASUSm3a32MVP su[4514]: Successful su for andrew by root
Mar 30 15:10:51 ASUSm3a32MVP su[4514]: + ??? root:andrew
Mar 30 15:10:51 ASUSm3a32MVP su[4514]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 30 15:10:52 ASUSm3a32MVP su[4514]: pam_unix(su:session): session closed for user andrew
Mar 30 15:10:52 ASUSm3a32MVP su[4529]: Successful su for andrew by root
Mar 30 15:10:52 ASUSm3a32MVP su[4529]: + ??? root:andrew
Mar 30 15:10:52 ASUSm3a32MVP su[4529]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 30 15:10:52 ASUSm3a32MVP su[4529]: pam_unix(su:session): session closed for user andrew
Mar 30 15:10:52 ASUSm3a32MVP su[4550]: Successful su for andrew by root
Mar 30 15:10:52 ASUSm3a32MVP su[4550]: + ??? root:andrew
Mar 30 15:10:52 ASUSm3a32MVP su[4550]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 30 15:10:52 ASUSm3a32MVP su[4550]: pam_unix(su:session): session closed for user andrew
Mar 30 15:10:52 ASUSm3a32MVP su[4571]: Successful su for andrew by root
Mar 30 15:10:52 ASUSm3a32MVP su[4571]: + ??? root:andrew
Mar 30 15:10:52 ASUSm3a32MVP su[4571]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 30 15:10:52 ASUSm3a32MVP su[4571]: pam_unix(su:session): session closed for user andrew
Mar 30 15:10:53 ASUSm3a32MVP NetworkManager: <info>  Sleeping...
Mar 30 15:10:53 ASUSm3a32MVP NetworkManager: <info>  (eth0): now unmanaged
Mar 30 15:10:53 ASUSm3a32MVP NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 37)
Mar 30 15:10:53 ASUSm3a32MVP NetworkManager: <info>  (eth0): deactivating device (reason: 37).
Mar 30 15:10:53 ASUSm3a32MVP NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 3591
Mar 30 15:10:53 ASUSm3a32MVP NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Mar 30 15:10:53 ASUSm3a32MVP avahi-daemon[3374]: Withdrawing address record for 192.168.1.101 on eth0.
```

---

### Post by emarkay on 2010-03-30
Surprised there are few comments - to me this seems sort of scary...

---

### Post by VMC on 2010-03-30
To be honest I've never looked at that log before. 
There's nothing there questionable that I can see. 
I don't have ACPI.

pam_unix is account authentication. Been around for quite awhile.

---

### Post by QLee on 2010-03-31
> **andrewthomas said:**
> I originally posted this in the security discussions forum and it was suggested that I post it here instead.  
[http://ubuntuforums.org/showthread.php?p=9045972](http://ubuntuforums.org/showthread.php?p=9045972)

...  Any  ideas?

Did you investigate the suggestion given by cdenly in that other thread?

---

### Post by andrewthomas on 2010-03-31
> **QLee said:**
> Did you investigate the suggestion given by cdenly in that other thread?
I looked around in the cron files and only could find this php file that  I don't have in other installs.

```
CRON[4437]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
```

---

