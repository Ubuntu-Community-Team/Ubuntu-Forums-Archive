---
title: "upgrade process locked"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by bill9 on 2014-11-30
my server has ubuntu 12.04 and since past 2 months or so won't update, won't partial update. tried ps-A|grepapt-get sudo apt-get update etc etc etc and result is always cannot lock /var/lib/apt...
so now after wasting many hours, i'll happily pay somebody to come by and fix it. on the north circular, near phoenix park. anybody interested?
bill

---

### Post by sudodus on 2014-11-30
I'm too far away for hands on help, but I have some tips, that you can try.

1. Reboot and try apt-get again. Maybe the locking will work as intended after a reboot (old Windows trick, yes I know, but it might work).

2. Try the commands in the following list, originally posted by *oldfred*, who has a lot of experience. Remember to use sudo, and run each of the commands each time, maybe even repeat them.

```
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```

Finally, if you get some other error output, please post it in a reply!

Good luck :-)

---

### Post by tgalati4 on 2014-11-30
The presence of a lock file usually means you have a stuck upgrade process; so you need to delete it and start again.  This also happens on the desktop version--if you try running *synaptic* and then try running *sudo apt-get update* in the terminal at the same time.  Only one update process can happen at a time, hence the lock file.

---

### Post by bill9 on 2014-11-30
@tgalati4
Hi, as I just posted to sudodus, I can't even install synaptic. I'm stuck, completely and that is putting it politely
Bill

---

### Post by oldfred on 2014-11-30
If you are absolutely sure you do not have another upgrade process running.

 Locked dpkg - only if sure you are not running another update.
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

---

### Post by bill9 on 2014-11-30
@oldfred
ok, your suggestion did something. after entering the command, it gave me a multiple choice confirmation question about nautilus so i picked yes as the cowards way out - i had sweat running down my face when i hit the enter key. then i rebooted and opened up ubuntu software center. now there is NO progress meter. so it looks like the blockage is gone. but now i'm afraid to do anything in case i destroy the system. everything has to be ok for the office tomorrow morning. should i leave it alone and wait until next weekend or do you think i could try checking for an update?
many thanks, Bill

---

### Post by oldfred on 2014-11-30
I try to have good backups before major changes.

And I would swear system knows if you did backups. If you do have current backups then you do not have issues. But the one time you are in a hurry and do not have backup, then it destroys system.

I would try:
sudo apt-get update
sudo apt-get install synaptic

That then only installs one package and we can see if it works, without trying to do all the updates in the queue.

---

### Post by bill9 on 2014-11-30
thanks. many, many thanks. wish i could return the help
bill

---

