---
title: "Problems installing and updating"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DPic on 2009-02-16
Okay, so i've received similar errors a few times, but i was usually able to make them go away with apt-get clean

That isn't working this time. My hard drive is not full. I've used around 90 of 250 GB. This is what happens: 
```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common gdebi gdebi-core lib32asound2 libasound2 libcryptui0 libcups2 libcupsimage2 libgnome-speech7 libnm-glib0 libnm-util1 libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 libpulsecore9 locales network-manager ppp pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal
  pulseaudio-module-x11 pulseaudio-utils python-gdbm seahorse tzdata tzdata-java xfce4-session
32 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/13.2MB of archives.
After this operation, 2912kB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 178436 files and directories currently installed.)
Preparing to replace tzdata-java 2008i-3 (using .../tzdata-java_2009b-1_all.deb) ...
Unpacking replacement tzdata-java ...
dpkg: error processing /var/cache/apt/archives/tzdata-java_2009b-1_all.deb (--unpack):
 unable to create `./usr/share/javazi/America/Swift_Current': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace tzdata 2008i-3 (using .../tzdata_2009b-1_all.deb) ...
Unpacking replacement tzdata ...
dpkg: error processing /var/cache/apt/archives/tzdata_2009b-1_all.deb (--unpack):
 unable to create `./usr/share/zoneinfo/America/Menominee': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata-java_2009b-1_all.deb
 /var/cache/apt/archives/tzdata_2009b-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas on what the problem is or how to fix it?

---

### Post by taavikko on 2009-02-16
> No space left on device

What does "df -h" print?

---

### Post by xebian on 2009-02-16
> **DPic said:**
> Okay, so i've received similar errors a few times, but i was usually able to make them go away with apt-get clean

That isn't working this time. My hard drive is not full. I've used around 90 of 250 GB. This is what happens: 
[INDENT]~$ sudo apt-get upgrade
Reading package lists... Done
.....
Unpacking replacement tzdata-java ...
dpkg: error processing /var/cache/apt/archives/tzdata-java_2009b-1_all.deb (--unpack):
 unable to create `./usr/share/javazi/America/Swift_Current': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              ...
Any ideas on what the problem is or how to fix it?

Look at your disk usage.  You may have 250GB but if dpkg is allowed only a tiny part and then it complains.  For sure it doesn't lie.

Post here the results of this command 
```
 df -h

```

---

### Post by DPic on 2009-02-16
I get this: 

```
~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             228G   93G  123G  44% /
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  344K  993M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M   64K  993M   1% /dev
tmpfs                 994M  3.8M  990M   1% /dev/shm
lrm                   994M  2.4M  991M   1% /lib/modules/2.6.28-6-generic/volatile
/dev/sdb1             917G  497G  374G  58% /media/storage
```

---

### Post by DPic on 2009-02-17
Any ideas???

---

### Post by taavikko on 2009-02-17
> **DPic said:**
> Any ideas???

bug in tzdata-java preinst / postinst files?

These can be viewed in /var/lib/dpkg/info/

---

### Post by DPic on 2009-02-17
But this happens when trying to install anything

_***Update***_: this worked-- sudo dpkg --clear-avail

---

### Post by chadwick359 on 2009-02-25
Any new updates on this? tried the --clear-avail, to no affect, still can't run my updates.

---

### Post by DPic on 2009-02-25
> **chadwick359 said:**
> Any new updates on this? tried the --clear-avail, to no affect, still can't run my updates.

it seemed to be a filesystem problem (perhaps ext allocating too much/not enough space?) as the next automatic check fixed it

---

### Post by chadwick359 on 2009-02-26
Yeah, after a few days of waiting for it to work itself out the stupid thing worked not 15 minutes after I posted that.. thanks, though.

---

### Post by DPic on 2009-02-28
great, i'm having the problem again. Is there any way to [check the filesystem at boot]("http://ubuntuforums.org/showthread.php?t=1083214") (instead of rebooting 30 times...)?

---

