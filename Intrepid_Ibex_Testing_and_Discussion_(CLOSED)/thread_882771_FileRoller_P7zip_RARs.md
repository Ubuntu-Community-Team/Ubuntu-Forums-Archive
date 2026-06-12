---
title: "FileRoller P7zip RARs"
date: 2008-08-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-08-07
Anyone having any luck with the new p7zip in fileroller on rar archives? I kepe getting this:

7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=C,Utf16=off,HugeFiles=on,1 CPU)

Processing archive: blah blah

Extracting  blah blah     Unsupported Method

Sub items Errors: 1

---

### Post by mattduckman on 2008-08-07
yes, i did actually get this error, but i forgot to look into it or file a bug because i ended up using the unrar command.

---

### Post by Nullack on 2008-08-13
Bug still exists and Ive raised:

[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/257519](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/257519)

Would someone please confirm the bug in launchpad.

---

### Post by olskar on 2008-08-13
I think it is better to report this directly upstream to bugzilla..

[http://bugzilla.gnome.org/simple-bug-guide.cgi?product=file-roller](http://bugzilla.gnome.org/simple-bug-guide.cgi?product=file-roller)

---

### Post by Nullack on 2008-08-13
Whos to say it isnt due to an Ubuntu or Debian patch? I have reservations about reporting bugs directly to upstream.

---

### Post by foxmulder881 on 2008-08-28
I'm still getting this error when extracting .rar archives with 7z from the command line.

Update: Sorry, my fault. I solved the problem by installing the **p7zip-rar** package.

---

