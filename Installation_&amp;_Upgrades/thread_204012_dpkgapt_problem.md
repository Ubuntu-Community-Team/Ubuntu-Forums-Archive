---
title: "dpkg/apt problem"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by ewdp on 2006-06-26
Since upgrading to Dapper, I can no longer run apt-get install.

ewd@lappy:~$ sudo apt-get install linux-image-2.6.15-25-686
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  linux-doc-2.6.15
Recommended packages:
  lilo
The following NEW packages will be installed:
  linux-image-2.6.15-25-686
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
Need to get 0B/22.4MB of archives.
After unpacking 64.1MB of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-image-2.6.15-25-686_2.6.15-25.43_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libdbus-1-2': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.15-25-686_2.6.15-25.43_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

dpkg -c /var/cache/apt/archives/libdbus-1-2_0.60-6ubuntu8_i386.deb returns:

drwxr-xr-x root/root         0 2006-05-16 03:43:50 ./
drwxr-xr-x root/root         0 2006-05-16 03:43:50 ./usr/
drwxr-xr-x root/root         0 2006-05-16 03:43:49 ./usr/share/
drwxr-xr-x root/root         0 2006-05-16 03:43:49 ./usr/share/doc/
drwxr-xr-x root/root         0 2006-05-16 03:44:00 ./usr/share/doc/libdbus-1-2/
-rw-r--r-- root/root      3586 2004-08-10 10:18:37 ./usr/share/doc/libdbus-1-2/README
-rw-r--r-- root/root       549 2005-11-08 05:57:13 ./usr/share/doc/libdbus-1-2/AUTHORS
-rw-r--r-- root/root     11193 2006-05-16 03:40:19 ./usr/share/doc/libdbus-1-2/copyright
-rw-r--r-- root/root    121966 2005-12-01 08:05:29 ./usr/share/doc/libdbus-1-2/changelog.gz
-rw-r--r-- root/root      6473 2005-12-01 05:01:33 ./usr/share/doc/libdbus-1-2/NEWS.gz
-rw-r--r-- root/root     12172 2006-05-16 03:40:19 ./usr/share/doc/libdbus-1-2/changelog.Debian.gz
drwxr-xr-x root/root         0 2006-05-16 03:44:00 ./usr/lib/
-rw-r--r-- root/root    225236 2006-05-16 03:44:00 ./usr/lib/libdbus-1.so.2.0.0
lrwxrwxrwx root/root         0 2006-05-16 03:43:50 ./usr/lib/libdbus-1.so.2 -> libdbus-1.so.2.0.0

So, I guess there's nothing wrong with the package.

ewd@lappy:~$ sudo dpkg -c /var/cache/apt/archives/libdbus-1-2_0.60-6ubuntu8_i386.deb > /var/lib/dpkg/info/libdbus-1-2.list
bash: /var/lib/dpkg/info/libdbus-1-2.list: Permission denied

ewd@lappy:~$ file /var/lib/dpkg/info/libdbus-1-2.list
/var/lib/dpkg/info/libdbus-1-2.list: ERROR: invalid mode 0116

So I guess the file list is broken.
Is there a way around this?

The machine is a Toshiba Tecra M3.

Any help would be appreciated.

Thank you.

---

### Post by rbalfour on 2006-06-26
try this.

$ sudo su
$ apt-get clean
$ apt-get update
$ apt-get install <packagename>

---

### Post by ewdp on 2006-06-26
Thanks for the quick reply.
But it still produced the same error.

Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  linux-doc-2.6.15
Recommended packages:
  lilo
The following NEW packages will be installed:
  linux-image-2.6.15-25-686
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
Need to get 0B/22.4MB of archives.
After unpacking 64.1MB of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-image-2.6.15-25-686_2.6.15-25.43_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libdbus-1-2': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.15-25-686_2.6.15-25.43_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rbalfour on 2006-06-26
$ apt-get -f install

I notice you need a dist-upgrade.

$apg-get dist-upgrade

---

### Post by ewdp on 2006-06-26
Still not working.
I still believe /var/lib/dpkg/info/libdbus-1-2.list is a corrupted file, so hence the dpkg errors.

ewd@lappy:~$ file /var/lib/dpkg/info/libdbus-1-2.list
/var/lib/dpkg/info/libdbus-1-2.list: ERROR: invalid mode 0116

---

### Post by ranf on 2006-06-26
[QUOTE=ewdp]
ewd@lappy:~$ sudo dpkg -c /var/cache/apt/archives/libdbus-1-2_0.60-6ubuntu8_i386.deb > /var/lib/dpkg/info/libdbus-1-2.list
bash: /var/lib/dpkg/info/libdbus-1-2.list: Permission denied
[/QUOTE]
This step didn't work. Try this instead:
```
sudo dpkg -c /var/cache/apt/archives/libdbus-1-2_0.60-6ubuntu8_i386.deb | sudo tee /var/lib/dpkg/info/libdbus-1-2.list
```

---

### Post by ewdp on 2006-06-27
ewd@lappy:~$ sudo dpkg -c /var/cache/apt/archives/libdbus-1-2_0.60-6ubuntu8_i386.deb | sudo tee /var/lib/dpkg/info/libdbus-1-2.list
tee: /var/lib/dpkg/info/libdbus-1-2.list: Permission denied
drwxr-xr-x root/root         0 2006-05-16 03:43:50 ./
drwxr-xr-x root/root         0 2006-05-16 03:43:50 ./usr/
drwxr-xr-x root/root         0 2006-05-16 03:43:49 ./usr/share/
drwxr-xr-x root/root         0 2006-05-16 03:43:49 ./usr/share/doc/
drwxr-xr-x root/root         0 2006-05-16 03:44:00 ./usr/share/doc/libdbus-1-2/
-rw-r--r-- root/root      3586 2004-08-10 10:18:37 ./usr/share/doc/libdbus-1-2/README
-rw-r--r-- root/root       549 2005-11-08 05:57:13 ./usr/share/doc/libdbus-1-2/AUTHORS
-rw-r--r-- root/root     11193 2006-05-16 03:40:19 ./usr/share/doc/libdbus-1-2/copyright
-rw-r--r-- root/root    121966 2005-12-01 08:05:29 ./usr/share/doc/libdbus-1-2/changelog.gz
-rw-r--r-- root/root      6473 2005-12-01 05:01:33 ./usr/share/doc/libdbus-1-2/NEWS.gz
-rw-r--r-- root/root     12172 2006-05-16 03:40:19 ./usr/share/doc/libdbus-1-2/changelog.Debian.gz
drwxr-xr-x root/root         0 2006-05-16 03:44:00 ./usr/lib/
-rw-r--r-- root/root    225236 2006-05-16 03:44:00 ./usr/lib/libdbus-1.so.2.0.0
lrwxrwxrwx root/root         0 2006-05-16 03:43:50 ./usr/lib/libdbus-1.so.2 -> libdbus-1.so.2.0.0

ewd@lappy:~$ ls -la /var/lib/dpkg/info/libdbus-1-2.list
?--x--xrw- 19791 1869772145 7227392 1031038313 1995-03-27 15:12 /var/lib/dpkg/info/libdbus-1-2.list

ewd@lappy:~$ du /var/lib/dpkg/info/libdbus-1-2.list
1.5G    /var/lib/dpkg/info/libdbus-1-2.list

This list file is causing the problem for sure.

---

### Post by ranf on 2006-06-27
[QUOTE=ewdp]
ewd@lappy:~$ ls -la /var/lib/dpkg/info/libdbus-1-2.list
?--x--xrw- 19791 1869772145 7227392 1031038313 1995-03-27 15:12 /var/lib/dpkg/info/libdbus-1-2.list

ewd@lappy:~$ du /var/lib/dpkg/info/libdbus-1-2.list
1.5G    /var/lib/dpkg/info/libdbus-1-2.list

This list file is causing the problem for sure.[/QUOTE]
Yes, definitely. 

---
ranf@schlepp:~$ ls -la /var/lib/dpkg/info/libdbus-1-2.list
-rw-r--r-- 1 root root 350 2006-05-16 15:41 /var/lib/dpkg/info/libdbus-1-2.list

ranf@schlepp:~$ cat /var/lib/dpkg/info/libdbus-1-2.list
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libdbus-1-2
/usr/share/doc/libdbus-1-2/README
/usr/share/doc/libdbus-1-2/AUTHORS
/usr/share/doc/libdbus-1-2/copyright
/usr/share/doc/libdbus-1-2/changelog.gz
/usr/share/doc/libdbus-1-2/NEWS.gz
/usr/share/doc/libdbus-1-2/changelog.Debian.gz
/usr/lib
/usr/lib/libdbus-1.so.2.0.0
/usr/lib/libdbus-1.so.2
---

I'd first do a "sudo chown root:root <filename>" then a "sudo chmod u+rw <filename>". If that doesn't help make a backup copy and remove it.

---

### Post by ewdp on 2006-06-30
root@lappy:/var/lib/dpkg/info# chown root:root libdbus-1-2.list
chown: changing ownership of `libdbus-1-2.list': Operation not permitted

root@lappy:/var/lib/dpkg/info# chmod u+rw libdbus-1-2.list
chmod: changing permissions of `libdbus-1-2.list': Operation not permitted

root@lappy:/var/lib/dpkg/info# mv libdbus-1-2.list /opt/
mv: cannot move `libdbus-1-2.list' to `/opt/libdbus-1-2.list': Operation not permitted

I even tried to remove the file without any success.
Never experienced something like this before.

Should I do an fsck?

---

### Post by ranf on 2006-06-30
Ouch, very weird.
fsck may help.

---

