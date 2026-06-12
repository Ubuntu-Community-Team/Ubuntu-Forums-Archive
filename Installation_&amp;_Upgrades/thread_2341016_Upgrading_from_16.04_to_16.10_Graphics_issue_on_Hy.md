---
title: "Upgrading from 16.04 to 16.10 Graphics issue on Hybrid Laptop"
date: 2016-10-24
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2016-10-24
I have a Laptop with Intel Haswell and Nvidia 970.
All worked fine on 16.04, but after upgrading to 10.10, I get the following weird behaviour.

After booting, I get the Login screen and I can login in ok.
Everything looks fine, but after a few seconds the screen begins to flash intermittently
I can see the same behaviour (intermittent flashing screen) when I go to a text terminal (Ctrl/F1)
Stopping GDM makes no difference to the terminal
I can still enter commands, bit the screen flashed intermittently

Booting into rescue/low graph mode hangs
Booting into rescue mode and dropping to a prompt doesn't work

Not booting with the latest Kernel 4.8.0-27-generic and booting with 4.4.0-46-generic works perfect.

Thanks

---

### Post by Bashing-om on 2016-10-24
lister171254; Hello;

My thought .. proprietary graphic's driver ?... the driver built against the 4.4.0-46 kernel .

If there is a proprietary driver at play here; try and purge the driver and re-install booted to terminal from the 4.8.0-27 kernel .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lister171254 on 2016-10-24
Thanks. That's the first thing I checked. I'm using the nouveau drivers.

I've been using Ubuntu with nvidia cards for a long time and there were more often than not graphic issues with a new release, but I have never had issues using the text terminal.

---

### Post by Bashing-om on 2016-10-24
lister171254; 1st for me also .

When you remove 'quiet splash' in grub's kernel boot line ( e key @ grub boot menu ) and boot, do you see any errors ?

anything relevant :
```

journalctl -b -0 ##shows messages from the current boot,
journalctl -b -1 ##from the previous boot

```

any instructions we can read
[INDENT][INDENT][INDENT]better than nothing
[/INDENT][/INDENT][/INDENT]

---

### Post by lister171254 on 2016-10-25
Have attached two files; works & fails

If you search for nvidia in both files, the 4.4 kernel enables the card, the 4.8 doesn't find files and aborts.

Thanks
Leo

---

### Post by Bashing-om on 2016-10-25
lister171254; Hey ...

Need an alternate means to access the files :
I run a real tight install, and a means to untar is not installed:
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           396M  776K  395M   1% /run
/dev/sda1       4.7G  2.2G  2.3G  49% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.0G   12K  2.0G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   22M  2.0G   2% /run/shm
none            100M  4.0K  100M   1% /run/user
/dev/sda2       9.5G  731M  8.3G   8% /home
/dev/sda8       4.7G  706M  3.8G  16% /var
sysop@1404mini:~$

```
I do not have the room for anything that I do not have to have ( and for what I might need to install in the future) .

[INDENT][INDENT]we can find a way
[/INDENT][/INDENT]

---

### Post by lister171254 on 2016-10-26
Haven't found a way to upload the individual text files. Trying to open them in Nautilus indicates that they are executables (no excutable bits set though), so I cannot upload the text files
Output of 'file' shows 
fails.txt: UTF-8 Unicode text, with very long lines

---

### Post by Bashing-om on 2016-10-26
lister171254l Hey, hey .

Here is an alternate that should work to xfer the logs .
```

journalctl -b -0 | nc termbin.com 9999
journalctl -b -1 | nc termbin.com 9999

```
where the result is a URL back in terminal, pass that link back here .

We see what the system has to say .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by lister171254 on 2016-10-26
Thanks for trying to help, but I don't allow access to my system from the outside.

Given that the same behavior also happens when I boot of the 16.10 LivedCD I've reported this on Launchpad [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1637032](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1637032).
Thanks again,
Leo

---

### Post by Bashing-om on 2016-10-26
lister171254; Good deal;

Let's see what the big boys have to say .

[INDENT][INDENT]one of those times
[/INDENT][/INDENT]

---

