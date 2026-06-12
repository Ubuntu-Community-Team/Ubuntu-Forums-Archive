---
title: "Reboot is stuck after install"
date: 2015-02-04
forum: Installation &amp; Upgrades
---

### Post by musicweb on 2015-02-04
We just installed 14.04 with a RAID1 setup this morning and everything went smoothly until it said we could boot into the new system.

A lot of text flew by, then stopped at this line:

```
Adding 1950652K swap on /dev/md0
```

A cursor shows below this line, but not flashing.

Is something wrong.....?

What do we need to do?

Tx in advance for any help.

---

### Post by oldfred on 2015-02-04
Do not know RAID, nor server installs.

But line it stops on is often not the problem. 
It often is several lines before that. 
Do you see something in the lines before it stops that is an issue?

---

### Post by musicweb on 2015-02-04
This is a few lines before:

```
init: plymouth-upstart-bridge main process (387) terminated with status 1
[    5.457595] init: plymouth-upstart-bridge main process ended, respawning
[    5.460514] init: plymouth-upstart-bridge main process (398) terminated with status 1
[    5.461659] init: plymouth-upstart-bridge main process ended, respawning
```

---

### Post by oldfred on 2015-02-04
Should be 0 or no error.
 terminated with status 1

But I do not know plymouth issues.

---

### Post by musicweb on 2015-02-05
So we just restarted the server and it finally got to a login prompt.
So whatever happened is fixed now.
We still have just swap and / partitions on each RAID device though.
I was reading somewhere that we should have a /boot partition....?
But it's running and we did all the updates....
Setting up ports, etc this morning......
Thanks for all input.

---

### Post by oldfred on 2015-02-05
It used to be that you had to have a /boot partition and some configurations still require it.
 But now grub2 has drivers to allow you to boot directly into some RAID configurations. So if it works you do not need a separate /boot.

---

### Post by musicweb on 2015-02-05
Maybe not the corect forum to ask this.... but I imagine the ubuntu server comes
withthe basic software to run a web server?
Perl, PHP, MySQL, FTP, etc....

---

### Post by oldfred on 2015-02-05
This is an older version, but it still is tasksel which is part of any standard server install. You can add tasksel to any install if desired. Link does show screen shot.

[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)

       Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel

---

