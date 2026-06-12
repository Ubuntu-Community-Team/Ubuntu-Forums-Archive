---
title: "libpython2.5.so not letting user mgmt"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by sheds on 2007-06-10
Hello there.

I've been  trying to get user management to work, but it tells me that there is a problem with libpython2.5.so. Here's the problem: 'Library files  for "libpython2.5.so" not found in paths'.

It tells me there are 2 reasons why this could be happening. Either there was an error during the las KDE upgrade leaving an orphaned control module, or, that there are old third party modules lying around.

I now know what the problem is, but i can't find the commands to do this. I found these files in /usr/lib, and i don't see that particular file, so perhaps that's a start.

libpython2.4.so -> libpython2.4.so.1
libpython2.4.so.1 -> libpython2.4.so.1.0
libpython2.4.so.1.0
libpython2.5.so.1 -> libpython2.5.so.1.0
libpython2.5.so.1.0
libpythonize.so.0 -> libpythonize.so.0.0.0
libpythonize.so.0.0.0

---

### Post by tonyric on 2007-08-30
sudo ln -s /usr/lib/libpython2.5.so.1.0 /usr/lib/libpython2.5.so

---

