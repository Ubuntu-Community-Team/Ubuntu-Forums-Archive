---
title: "Thunderbird disappears in Hardy"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by eberndl on 2008-07-30
Hi,

Since upgrading firefox yesterday, I've run into some very unusual situations.

1) When I launch Thunderbird, it flashes on the screen, then disappears.  If I try to re-launch it, I get the following error message:

 Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.

2) If I try to open Thunderbird, and then try to open Firefox, the same error occurs in Firefox (but does not happen if I open Firefox before trying to open Thunderbird)

3) I found another person who had similar problems [here]("http://ubuntuforums.org/showthread.php?t=872066&highlight=thunderbird+disappears"). 

Once again, I will post the outputs that were asked for in that thread:

lizz@lizz-desktop:~$ ls -la /media/share/Mozilla/Thunderbird/
total 48
drwxrwxrwx 3 root root 16384 2008-04-30 22:15 .
drwxrwxrwx 4 root root 16384 2008-04-30 22:15 ..
drwxrwxrwx 4 root root 16384 2008-07-30 00:27 feeiwdgl.default

(It's set up like this because I dual boot with Windows)

and then
lizz@lizz-desktop:~$ ls -la /media/share/Mozilla/Thunderbird/feeiwdgl.default/
total 10304
drwxrwxrwx 4 root root 16384 2008-07-30 00:27 .
drwxrwxrwx 3 root root 16384 2008-04-30 22:15 ..
-rwxrwxrwx 1 root root 195 2005-02-27 11:39 90969431.s
-rwxrwxrwx 1 root root 99575 2008-07-25 01:31 abook.mab
-rwxrwxrwx 1 root root 248 2008-07-30 00:27 blocklist.xml
-rwxrwxrwx 1 root root 65536 2008-07-25 01:31 cert8.db
-rwxrwxrwx 1 root root 130 2008-07-27 23:57 compatibility.ini
-rwxrwxrwx 1 root root 151394 2008-07-27 23:57 compreg.dat
-rwxrwxrwx 1 root root 235 2008-05-14 18:23 cookies.txt
-rwxrwxrwx 1 root root 6677 2008-06-09 23:47 downloads.rdf
drwxrwxrwx 2 root root 16384 2008-04-30 22:17 extensions
-rwxrwxrwx 1 root root 212 2008-07-27 23:57 extensions.cache
-rwxrwxrwx 1 root root 196 2008-07-27 23:57 extensions.ini
-rwxrwxrwx 1 root root 2016 2008-07-27 23:57 extensions.rdf
-rwxrwxrwx 1 root root 1423 2004-07-27 19:10 history.mab
-rwxrwxrwx 1 root root 11185 2008-06-17 18:52 impab.mab
-rwxrwxrwx 1 root root 785168 2008-07-30 03:57 junklog.html
-rwxrwxrwx 1 root root 16384 2008-07-25 01:31 key3.db
-rwxrwxrwx 1 root root 40409 2008-07-29 21:57 localstore.rdf
drwxrwxrwx 5 root root 16384 2008-04-30 22:16 Mail
-rwxrwxrwx 1 root root 477 2004-07-08 11:21 mailViews.dat
-rwxrwxrwx 1 root root 10652 2008-05-08 22:37 mimeTypes.rdf
-rwxrwxrwx 1 root root 178976 2008-07-30 18:05 panacea.dat
-rwxrwxrwx 1 root root 0 2008-07-30 20:43 .parentlock
-rwxrwxrwx 1 root root 49 2005-10-01 16:45 persdict.dat
-rwxrwxrwx 1 root root 13282 2008-07-27 23:57 prefs.js
-rwxrwxrwx 1 root root 13479 2008-04-25 07:22 prefs.zal
-rwxrwxrwx 1 root root 16384 2008-04-30 23:02 secmod.db
-rwxrwxrwx 1 root root 4299666 2008-07-28 00:12 training.dat
-rwxrwxrwx 1 root root 0 2008-04-30 17:59 urlclassifier2.sqlite
-rwxrwxrwx 1 root root 10 2008-07-25 01:31 virtualFolders.dat
-rwxrwxrwx 1 root root 1060700 2008-07-27 23:57 XPC.mfasl
-rwxrwxrwx 1 root root 1000626 2008-07-25 01:32 xpc.mfl
-rwxrwxrwx 1 root root 116837 2008-07-27 23:57 xpti.dat
-rwxrwxrwx 1 root root 1162265 2008-07-27 23:57 XUL.mfasl
-rwxrwxrwx 1 root root 1145881 2008-07-25 01:32 xul.mfl


Can anyone help?  I really need my Thunderbird back!

Thanks!!

---

