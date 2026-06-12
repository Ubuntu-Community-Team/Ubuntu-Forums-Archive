---
title: "Problems with apt-get -f install"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by Nunners on 2010-06-08
I'm having problems installing various applications, and thought if I tried again from scratch, it might solve the problem, but I can't get back to nothing!

I get the following now:
```
apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  exim4-daemon-heavy sa-exim
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
4 not fully installed or removed.
After this operation, 1,602kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 39877 files and directories currently installed.)
Removing sa-exim ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing sa-exim (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing exim4-daemon-heavy ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing exim4-daemon-heavy (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 sa-exim
 exim4-daemon-heavy
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can someone gi veme some guidance on how to find the log files (if there are any) to find out whats causing the problem?

Thanks
Nunners

---

### Post by dabl on 2010-06-08
Probably, in a terminal, this will fix it:

```
sudo apt-get update
```
```

sudo apt-get remove --purge exim4-daemon-heavy
```

(observe for error output)

```
sudo apt-get remove --purge sa-exim
```

(observe for error output)

```
sudo apt-get clean
```

NOW

```
sudo apt-get install exim4-daemon-heavy sa-exim
```

(observe for error output)

I don't know those packages -- they may have a config screen that you need to give a response during installation.  Use the tab key to move to the "OK" to continue after making whatever response is needed.

---

### Post by piotrwoj on 2010-06-08
set repo sources.list to master server ubuntu.com, other server have to delay and old repo, [SIZE=1]because sometimes happen errors[/SIZE]
 
Regards: Piotrwoj - my site on ubuntu server: [http://www.domar.biz.pl](http://www.domar.biz.pl)

---

### Post by Nunners on 2010-06-09
THanks for the response...

I've tried as suggested, but no further on, as it's still coming up with the same errors....

```
s# sudo apt-get remove --purge exim4-daemon-heavy
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  exim4-daemon-light
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  exim4-daemon-heavy sa-exim
0 upgraded, 0 newly installed, 2 to remove and 4 not upgraded.
5 not fully installed or removed.
After this operation, 1,602kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 39905 files and directories currently installed.)
Removing sa-exim ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format                                                                              error
dpkg: error processing sa-exim (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing exim4-daemon-heavy ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format                                                                              error
dpkg: error processing exim4-daemon-heavy (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 sa-exim
 exim4-daemon-heavy
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Again, tried checking the dpkg.log and it talks about half-installed etc...

```
2010-06-09 08:33:14 startup packages remove
2010-06-09 08:33:14 status half-installed sa-exim 4.2.1-12
2010-06-09 08:33:14 remove sa-exim 4.2.1-12 4.2.1-12
2010-06-09 08:33:14 status half-installed sa-exim 4.2.1-12
2010-06-09 08:33:14 status half-installed exim4-daemon-heavy 4.71-3ubuntu1
2010-06-09 08:33:14 remove exim4-daemon-heavy 4.71-3ubuntu1 4.71-3ubuntu1
2010-06-09 08:33:14 status half-installed exim4-daemon-heavy 4.71-3ubuntu1

```

---

### Post by Nunners on 2010-06-09
This gets stranger and stranger.

I tried
```
apt-get --assume-yes --purge remove exim4-daemon-heavy sa-exim
```

Which removed exim4-daemon-heavy and sa-exim, but then came up with errors on libperl5.10 & libpq5.

Then tried

```
apt-get --assume-yes --purge remove libperl5.10 libpq5
```

And now only libpq5 is the problem....

```
#sudo apt-get --assume-yes remove --purge libpq5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  libpq5
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 606kB disk space will be freed.
(Reading database ... 39866 files and directories currently installed.)
Removing libpq5 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libpq5 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libpq5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Nunners on 2010-06-09
Finally got there... installed libpq5, which cleared it's error cleaned/updated... reinstalled the original packages!

```
sudo apt-get install libpq5
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install exim4-daemon-heavy sa-exim

```

---

