---
title: "Can't remove courier-imap"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by TexLogic on 2007-05-26
Hello,

I installed and later removed courier-imap, but noticed that /etc/courier still existed.  So I deleted it.  A bad idea.  Anyway, in the course of trying to remove some files that became unneeded after removing courier-imap, I found myself unable to uninstall an associated file, courier-authdaemon, IIRC.  So I tried reinstalling courier-imap to get that file back, but that doesn't seem to have worked.  And now I can't uninstall courier-imap at all.  I get the following error:

Removing courier-imap ...
 * ERR: config file missing
invoke-rc.d: initscript courier-imap, action "stop" failed.
dpkg: error processing courier-imap (--remove):
 subprocess pre-removal script returned error exit status 1
 * ERR: config file missing
invoke-rc.d: initscript courier-imap, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 courier-imap
E: Sub-process /usr/bin/dpkg returned an error code (1)

Looking at the courier-imap script in /etc/init.d/courier-imap, it appears that it is trying to run a script in /etc/courier called "imap".  But if I just try creating this file with touch, I get another error -- clearly it's looking for some functionality, not just any file.

I've tried "apt-get --reinstall install courier-imap" and "dpkg -r --force-remove-reinstreq courier-imap".  Neither enables me to remove courier-imap.

Some help for someone new to Ubuntu (after years of FreeBSD and Mac OS X) would be tremendously appreciated.

TexLogic

---

### Post by TexLogic on 2007-05-26
Found the answer in the forum archives with a little more searching (these steps are modified to fit my situation):

1. backup /var/lib/dpkg/status to a safe location
2. remove all courier entries from /var/lib/dpkg/status
3. sudo apt-get upgrade
4. sudo apt-get install courier-imap courier-ssl
5. sudo apt-get remove courier-imap courier-ssl
6. sudo apt-get autoremove libc-client2002edebian gamin libgamin0 courier-ssl expect courier-base mlock courier-authlib-userdb courier-authlib tcl8.4 libglib2.0-0 courier-authdaemon libltdl3

That did the trick.

---

### Post by nativesun on 2007-06-06
After step 5, I get this result:

/etc/courier/imapd: line 101: -: command not found
invoke-rc.d: initscript courier-imap, action "start" failed.
dpkg: error processing courier-imap (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 courier-imap
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone have any ideas on this one?

---

### Post by nativesun on 2007-06-14
Well, duh.  Went to line 101 of /etc/courier/imapd and hashed out line 101 (just referred to debugging info) and courier-imap installed just fine.

---

### Post by lyncas on 2008-06-04
Thank you very much, this worked very the first time I tried it !

---

