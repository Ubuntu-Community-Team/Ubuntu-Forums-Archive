---
title: "Upgrade led to identity crisis"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Fishbowler on 2010-10-12
I upgraded yesterday from Lucid to Maverick.
Initially, I hadn't quite the disk space the installer required, but a quick sudo apt-get clean fixed that.

The installer gave a few errors during the process, each related to dpkg and a cache, but alas, I hadn't the forethought to write them down! All of the errors were the same, with the exception of the package name. Affected were icedtea, a few others, and the latest linux headers (linux-headers-2.6.35-22). As it turns out, disk space was still the issue, and the installer had told me a little fib!

The process continued for a while despite the errors, then eventually told me that because of the errors, the upgrade had failed.

I manually installed linux-headers-2.6.35-22, and ran sudo apt-get install --fix-broken then I rebooted the machine.

I've got the new font, and the new Ubuntu Software Centre.

I don't, however, seem to have a "complete" upgrade. When I SSH to the machine, I see this:

```

Linux piggy 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

1 package can be updated.
0 updates are security updates.

New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Tue Oct 12 07:18:07 2010 from piggy
```

(I didn't choose that rubbish machine name...)

do-release-upgrade gives:
```
Checking for a new ubuntu release
No new release found
```

And despite that "1 package can be updated message", sudo apt-get upgrade gives:
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Anyone got any ideas?
Is there, perhaps, a way to force a re-install of the 10.04>10.10 upgrade?

---

### Post by scovel on 2010-10-12
I'm seeing the same thing.  No disk space problem here though.   The upgrade went without a hitch.  Notice at the top of the screen it says 10.04.1 LTS

```
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Mon Oct 11 17:21:46 EDT 2010

  System load:  0.06               Processes:             180
  Usage of /:   72.3% of 70.30GB   Users logged in:       1
  Memory usage: 45%                IP address for eth0:   10.10.20.20
  Swap usage:   0%                 IP address for virbr0: 192.168.122.1
  Temperature:  30 C

  => /var/mythtv is using 98.8% of 465.71GB

  Graph this data and manage this system at https://landscape.canonical.com/

691 packages can be updated.
0 updates are security updates.

New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.

gordon:~$
```What does 

```
sb_release -a
```give you?  For me it's 

```
gordon:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick

```Don't know why the login script is saying otherwise.  

To upgrade I edited /etc/update-manager/release-upgrades and change the Prompt=LTS to normal, then I ran do-release-upgrade.

Sean

---

### Post by Fishbowler on 2010-10-12
lsb_release gave me the same result - Maverick all the way!

Did you receive any warnings at all during the upgrade? 
I fired mine off through the UI, so they were a little easier to spot!

---

### Post by Fishbowler on 2010-10-18
A little more research has shown that /etc/motd.tail holds all the Lucid stuff, whilst the Maverick stuff is all being added by the update-motd cron job.

I can clean this up myself. Not a problem. But...

Was this supposed to be cleaned by the upgrade?
If so, any idea if anything else could be missing?
Are there places I can check for evidence of clean-up scripts not being run?
Better still, can I re-run it?

---

### Post by efflandt on 2010-10-18
If any of you still have /etc/motd.tail maybe that is the issue.  I do not see that in 10.10.  motd is likely composed by scripts in /etc/update-motd.d/

Another poster who upgraded noticed that it said both 10.10 and 10.04.1 LTS when they logged in with ssh.  So maybe something in upgrades is failing to remove motd.tail.

---

### Post by dan000 on 2010-10-18
This had been driving me crazy. I had the same motd I had when I upgraded. I didn't realize that I also had another one above it.

It looks like during the upgrade /etc/motd.tail was moved to /etc/motd.tail.old, and /etc/motd was moved to /etc/motd.tail, so whenver update-motd was run, the last thing on the motd was the old motd from right before the upgrade.
Simply doing this fixed it for me:
```
sudo mv /etc/motd.tail{.old,}
```

Thanks for the help, guys!

---

