---
title: "Open Office 2 problems"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by mthaddon on 2005-10-16
Hi Folks,

So I had a somewhat troublesome upgrade via the command line to Breezy, but overall was pretty happy with it. Mostly just unresolved dependencies that I had to resolve manually on perl packagages. Anyway, I digress....

I am having problems with Open Office. I can't run either version 1.x or 2.x.

Here's the error messages I get.

/usr/lib/openoffice2/program/javaldx: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice.bin.real: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory

I've done ldconfig -p | grep libz and libz.so.1 is right there in /usr/lib.

Also, I tried doing, ldd `which oowriter2` and got this:

/usr/bin/ldd: line 95: lddlibc4: command not found
        not a dynamic executable

not sure if they're related. Any help appreciated.

Thanks, Tom

---

### Post by azteech on 2005-10-16
[quote=mthaddon]Hi Folks,

So I had a somewhat troublesome upgrade via the command line to Breezy, but overall was pretty happy with it. Mostly just unresolved dependencies that I had to resolve manually on perl packagages. Anyway, I digress....

I am having problems with Open Office. I can't run either version 1.x or 2.x.

Here's the error messages I get.

/usr/lib/openoffice2/program/javaldx: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice.bin.real: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory

I've done ldconfig -p | grep libz and libz.so.1 is right there in /usr/lib.

Also, I tried doing, ldd `which oowriter2` and got this:

/usr/bin/ldd: line 95: lddlibc4: command not found
        not a dynamic executable

not sure if they're related. Any help appreciated.

Thanks, Tom[/quote] 
Sounds like you might have a bad install of oo2 that is keeping both from working.
Have you tried un-installing both versions, from synaptic, rebooting and then re-installing them to see if you have the same problems?

---

### Post by mthaddon on 2005-10-16
Can you help me out with command line way to do this. Want to make sure I fully purge everything and would feel more comfortable doing this from the command line.

Thanks, Tom

---

### Post by azteech on 2005-10-17
[quote=mthaddon]Can you help me out with command line way to do this. Want to make sure I fully purge everything and would feel more comfortable doing this from the command line.

Thanks, Tom[/quote]

Have a look at the following thread .. it should help you.

[http://www.ubuntuforums.org/showthread.php?t=30866&highlight=remove+openoffice](http://www.ubuntuforums.org/showthread.php?t=30866&highlight=remove+openoffice)

---

