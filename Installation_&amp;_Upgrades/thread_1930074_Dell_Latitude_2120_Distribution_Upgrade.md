---
title: "Dell Latitude 2120 Distribution Upgrade"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by afbase on 2012-02-23
I just unboxed my new dell latitude 2120.  It came with 10.10 installed. I want to upgrade to 11.04 (and perhaps to 11.10 if possible).   

When I click on the "upgrade" button in update-manager, i receive this error
```
Authentication failed  Authenticating the upgrade failed. There may be a problem with
```
I have tried the libreadline.so.6 trick in [http://ubuntuforums.org/showthread.php?t=1711179](http://ubuntuforums.org/showthread.php?t=1711179)  by downloading the latest libreadline from gnu, make, make install.  It turns out to be libreadline.so.6.2 that i compiled and it stored it into /usr/local/lib  by default.  I try update-manager again and still run into the same issue. 
```
Authentication failed  Authenticating the upgrade failed. There may be a problem with
```

I've tried typing in
```
gpg
```
I got the following error:
```
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC

```
I guess the libreadline.so.6 is just a pain.  What other fixes are there?

---

### Post by afbase on 2012-02-23
> **afbase said:**
> 
```
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC

```
I guess the libreadline.so.6 is just a pain.  What other fixes are there?

If I download the [libreadline](ftp://ftp.gnu.org/gnu/readline/) tar ball (version 6.1 or 6.2) from GNU mirrors, is there a way to ```
./configure 
make
sudo make install
``` such that I can preload /usr/lib/libncurses.so?  I am not sure what this means exactly but I noticed that [ this link](http://www.segger2.com/index.php?page=Thread&threadID=925) is the same or similar for a slackware system.  I wonder is this is the same problem for debian-based systems.  

Any comments about this are much appreciated.

---

