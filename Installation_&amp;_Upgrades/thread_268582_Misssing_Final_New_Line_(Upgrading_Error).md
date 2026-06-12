---
title: "Misssing Final New Line (Upgrading Error)"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by reubadoob on 2006-09-30
Recentlly I've been trying to run an upgrade for 5 programs and having a immense amount of trouble. Namely continously running into this error "'libcc1 is missing final new line'". I have looked all over this forum and no one has a definte solution to this problem but there are plenty of us that have encountered it. Here's a look at the code that I recieved after trying to update the programs:
```

The following packages will be upgraded:
  amarok amarok-xine ktorrent libssl0.9.8 openssl
5 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.8MB of archives. After unpacking 98.3kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com dapper-security/main libssl0.9.8 0.9.8a-7ubuntu0 .2 [2594kB]
Get:2 http://archive.ubuntu.com dapper-backports/main amarok-xine 2:1.4.3-0ubunt u8~dapper1 [54.7kB]
Get:3 http://archive.ubuntu.com dapper-backports/main amarok 2:1.4.3-0ubuntu8~da pper1 [17.1MB]
Get:4 http://archive.ubuntu.com dapper-backports/main ktorrent 2.0.2-0ubuntu1~dapper1 [2076kB]
Get:5 http://archive.ubuntu.com dapper-security/main openssl 0.9.8a-7ubuntu0.2 [976kB]
Fetched 22.8MB in 32s (712kB/s)
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libssl0.9.8_0.9.8a-7ubuntu0.2_i386.deb (--unpack):
 files list file for package `libgcc1' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libssl0.9.8_0.9.8a-7ubuntu0.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

So please if you have any suggestions or any tips on how to correct, work around or somlve this problem PLEASE POST them. I'm getting really tired of seeing that annoying orange asterix in the corner of my screen. Plus, I liked to have up to date software. Who doesn't?

---

### Post by reubadoob on 2006-10-01
Please this problem has still not been resolved. I NEED YOUR HELP!!!

---

### Post by siman on 2006-10-02
i got the same problem with different packages.

```

simon@silentia:~$ sudo apt-get install xmule
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libcrypto++5.2c2a libwxgtk2.4-1-contrib
The following NEW packages will be installed:
  libcrypto++5.2c2a libwxgtk2.4-1-contrib xmule
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 3065kB of archives.
After unpacking 10.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com dapper/universe libcrypto++5.2c2a 5.2.1c2a-2 [1269kB]
Get:2 http://archive.ubuntu.com dapper/universe libwxgtk2.4-1-contrib 2.4.4.1.1ubuntu2 [883kB]
Get:3 http://archive.ubuntu.com dapper/universe xmule 1.10.0b-1ubuntu2 [913kB]
Fetched 3065kB in 7s (393kB/s)
(Reading database ... dpkg: error processing /var/cache/apt/archives/libcrypto++5.2c2a_5.2.1c2a-2_i386.deb (--unpack):
 files list file for package `libconsole' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libcrypto++5.2c2a_5.2.1c2a-2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
and
```

simon@silentia:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  checkinstall gdk-imlib1
The following packages will be upgraded:
  automatix
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/29.4kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing /var/cache/apt/archives/automatix_6.5-6-6.06dapper1_i386.deb (--unpack):
 files list file for package `libconsole' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/automatix_6.5-6-6.06dapper1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I did apt-get clean, apt-get update, apt-get check and a -f install. Problem remains. I have this issue on desktop and laptop, both running Dapper since weeks.

There are other threads out there that report the SAME PROBLEM!!! This doesnt seem to be a user-error?!?!

---

### Post by reubadoob on 2006-10-02
Yea this is craziness. If some one could just post howto add another or a "new line" that would be nice.

---

### Post by Mithrilhall on 2006-10-03
I'm having the same problem installing anything.

---

### Post by siman on 2006-10-05
now, there are some "system updates".. and I can not even apply those. this problem is really getting annoying!! is there no-one with more exptertise, who can guide us through the trouble shooting?

the error message, when I do system-update via the gnome-applet is:
```

E: /var/cache/apt/archives/libssl-dev_0.9.8a-7ubuntu0.3_i386.deb: files list file for package `libconsole' is missing final newline

```

yes.. i also did apt-get clean before trying the update.

thanks...

---

### Post by siman on 2006-10-06
I took the error message literary

```

 files list file for package `libconsole' is missing final newline

```

so I appended a newline to /var/lib/dpkg/info/libconsole.list => everything works now .. hehe.

---

google thinks this might be due to an fsck on the drive or something like that.

---

### Post by vod_ska on 2006-11-24
How u solve the problem? 

Because I have tried to edit the .list of my problematic package, but I couldn't!!!

---

### Post by siman on 2006-11-24
it worked for me, is just added the newline.

> but I couldn't!!!

what do you mean with that.. what doesnt work?

---

### Post by apowell656 on 2007-06-27
Where you ever able to fix this problem it seems that I am having the same problem with no real help from forums , google or random attempts

---

