---
title: "Adding Java to Firefox"
date: 2004-10-30
forum: Installation &amp; Upgrades
---

### Post by trico on 2004-10-30
The installation went smoothly for most everything but I don't have Java support with my Firefox installation.  I think that this is normal - probably licencing issues.  Are there instructions somewhere on how to add it myself?

Trico

---

### Post by ubuntu-geek on 2004-10-30
This should do the trick for you...
 
 [http://ubuntuforums.org/showthread.php?t=198](http://ubuntuforums.org/showthread.php?t=198)

---

### Post by trico on 2004-10-30
My Firefox doesn't have a 'plugins' directory.

My steps so far:
Downloaded the bin file from java.com
Then in a terminal window I said:
# sudo chmod a+x j2re-1_4_2_05-linux-i586.bin
# ./j2re-1_4_2_05-linux-i586.bin
 
This creates a directory named j2re1.4.2_05
To move it I said:
# sudo mv j2re1.4.2_05 /usr/local

**The next step is to navigate to the /home/myid/.mozilla/plugins directory and here I run aground.  My .mozilla diretory looks like this:**

[email]larry@trico:~/.mozi[/email]lla/firefox $ ls -l
total 8
drwx------    7 larry    larry        4096 2004-10-30 11:39 default.idl
-rw-r--r--    1 larry    larry          89 2004-10-27 18:07 profiles.ini

Here's default.idl
[email]larry@trico:~/.mozilla/firefox/default.idl[/email] $ ls -l
total 1012
-rw-------    1 larry    larry        2871 2004-10-30 11:39 bookmarks.html
drwxr-xr-x    2 larry    larry        4096 2004-10-30 11:38 Cache
drwxr-xr-x    2 larry    larry        4096 2004-10-29 19:47 Cache.Trash
-rw-------    1 larry    larry       65536 2004-10-30 11:39 cert8.db
drwxr-xr-x    3 larry    larry        4096 2004-10-30 11:39 chrome
-rw-r--r--    1 larry    larry          65 2004-10-30 11:39 compatibility.ini
-rw-r--r--    1 larry    larry          24 2004-10-30 11:39 components.ini
-rw-r--r--    1 larry    larry      126840 2004-10-30 11:39 compreg.dat
-rw-r--r--    1 larry    larry        1862 2004-10-30 12:45 cookies.txt
-rw-r--r--    1 larry    larry          24 2004-10-30 11:39 defaults.ini
-rw-r--r--    1 larry    larry        3656 2004-10-30 11:15 downloads.rdf
drwxr-xr-x    3 larry    larry        4096 2004-10-30 11:39 extensions
-rw-r--r--    1 larry    larry        1777 2004-10-30 11:39 formhistory.dat
-rw-r--r--    1 larry    larry       88632 2004-10-30 12:45 history.dat
-rw-r--r--    1 larry    larry         326 2004-10-30 11:38 install.log
-rw-------    1 larry    larry       16384 2004-10-30 11:39 key3.db
-rw-r--r--    1 larry    larry        6569 2004-10-30 11:39 localstore.rdf
lrwxrwxrwx    1 larry    larry          14 2004-10-30 11:39 lock -> 127.0.0.1:7072
-rw-r--r--    1 larry    larry        1120 2004-10-27 19:23 mimeTypes.rdf
-rw-r--r--    1 larry    larry        4750 2004-10-30 11:39 prefs.js
-rw-r--r--    1 larry    larry         752 2004-10-27 18:07 search.rdf
-rw-------    1 larry    larry       16384 2004-10-27 18:43 secmod.db
-rw-------    1 larry    larry         418 2004-10-29 19:48 signons.txt
drwxr-xr-x    3 larry    larry        4096 2004-10-27 18:07 US
-rw-r--r--    1 larry    larry       75917 2004-10-30 11:39 xpti.dat
-rw-r--r--    1 larry    larry      568091 2004-10-30 11:39 XUL.mfasl

Extensions sounds promising, but I don't know what I'm looking for.  Does this look like the right kind of thing?
[email]larry@trico:~/.mozilla/firefox/default.idl[/email]/extensions $ ls -l
total 8
drwxr-xr-x    4 larry    larry        4096 2004-10-30 11:39 {a7c6cf7f-112c-4500-a7ea-39801a327e5f}
-rw-r--r--    1 larry    larry        1104 2004-10-30 11:39 Extensions.rdf

I do have one extension loaded.  Perhaps that's a new name for the plugins.

Trico

---

### Post by Rancoras on 2004-10-30
The lack of a plugins folder is referenced in that same thread that ubuntu-geek gave you.

---

### Post by trico on 2004-10-30
Oops.  

Ok, I added the plugins directory and the symbolic link and Java is working with firefox now.

Thanks,
Trico

---

