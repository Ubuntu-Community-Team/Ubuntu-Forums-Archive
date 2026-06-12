---
title: "mising lines in libdb4.3"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by waelaltaqi on 2007-10-08
After upgrading to 7.10, i'm having a problem with libdb4.3 ... the problem is effecting system upgrades in general . 
for example, i'm trying to install the PHP editor BlueFish: 

```
(Reading database ... dpkg: error processing /var/cache/apt/archives/bluefish_1.0.7-2_i386.deb (--unpack):
 files list file for package `libdb4.3' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/bluefish_1.0.7-2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i downloaded the library from Debian's website and i tried to remove it and reinstall it: 
```
dpkg -r libdb4.3
(Reading database ... dpkg: error processing libdb4.3 (--remove):
 files list file for package `libdb4.3' is missing final newline
Errors were encountered while processing:
 libdb4.3
Processing was halted because there were too many errors.

```


i tried to install the package on top and it's coming back with: 
```
 dpkg -i  Desktop/libdb4.3_4.3.29-11_i386.deb 
Selecting previously deselected package libdb4.3.
(Reading database ... dpkg: error processing Desktop/libdb4.3_4.3.29-11_i386.deb (--install):
 files list file for package `libdb4.3' is missing final newline
Errors were encountered while processing:
 Desktop/libdb4.3_4.3.29-11_i386.deb
Processing was halted because there were too many errors.

```

i even tried the force option to overwrite the exesting package but no luck: 
```
 dpkg -i --force-overwrite Desktop/libdb4.3_4.3.29-11_i386.deb 
Selecting previously deselected package libdb4.3.
(Reading database ... dpkg: error processing Desktop/libdb4.3_4.3.29-11_i386.deb (--install):
 files list file for package `libdb4.3' is missing final newline
Errors were encountered while processing:
 Desktop/libdb4.3_4.3.29-11_i386.deb
Processing was halted because there were too many errors.

```

i would appreciate any help on this ... 

Regards;

---

### Post by kaotikzen on 2007-10-23
you might try editing the list file in vi

sudo vi /var/lib/dpkg/info/libdb4.3.list

when the file opens in vi it will give a warning talking about how it was missing a final return and that it converted a number of lines, go ahead and hit "y" to finish opening the file.  then you just have to write the changes (:w) and quit (:q)

---

