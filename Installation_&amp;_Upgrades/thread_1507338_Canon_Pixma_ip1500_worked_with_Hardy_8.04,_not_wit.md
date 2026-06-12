---
title: "Canon Pixma ip1500 worked with Hardy 8.04, not with Karmic 9.10"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by desconocido on 2010-06-11
I have replaced Ubuntu 8.04 with a clean install of 9.10

In 8.04 I used to be able to print to my Canon Pixma ip1500 using the resources at
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

In 9.10 I can no longer get my Canon Pixma ip1500 printer to work because on the one hand:

Open pstocanonbj_3.3-1.1_i386.deb with GDebi Package Installer
```
Error: Dependency is not satisfiable: libcupsys2-gnutls10 (>= 1.1.23-1)
```

and on the other hand:

In [http://packages.debian.org/etch/libcupsys2](http://packages.debian.org/etch/libcupsys2)
download libcupsys2-gnutls10
"Download Page for libcupsys2_1.2.7-4+etch9_i386.deb on Intel x86 machines"
Open with GDebi
```
Error: Breaks exisiting package 'libcups2' conflict: libcupsys2 (< 1.3.7-6)
```

Does anyone have any suggestions?

---

### Post by radddi on 2010-06-11
I have the same printer and everytime I upgrade the OS an epic struggle against illogical errors begins. Now I am with Lucid and just resolved the issue today (finally). Since everytime I have tackled the problem, different results occur I can only tell you what I did today.

First I completely uninstalled CUPS as well as all of the ip1500 install files (bjfilter*). After reinstallation I downloaded the official drivers from CANON: [http://software.canon-europe.com/software/0022415.asp?model=](http://software.canon-europe.com/software/0022415.asp?model=)

I installed them through alien and then followed the following tutorial from point 5 onward: [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500) . Then miraculously, the printer started sucking in pages for the first time in ages.

Concerning your specific problem, I think there might be problems with the packages in [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/) . If you get the same error after using the CANON drivers, then you could try to remove the conflicting packages - libcupsys2-gnutls10 , libcups2 or libcupsys2 .

Best of luck to you! :)

---

### Post by Naggobot on 2010-06-11
Now do not take this as an advice since I do not have a printer but you might want to check[ this.]("https://help.ubuntu.com/community/SynapticHowto#How%20to%20force%20the%20installation%20of%20a%20package%20version")  I have never tried this my self but my guess (now this is an absolute quess) is that the repository needs to be first changed to older repository and then after reloading the package information the package can be forced. 

Now there is absolutely no guarantee that the old will work with new kernel :( and that forcing the package does not break something else that is needed. 

Now I would do it as described above but I also do have a habit of being able to break my installations since I have no solid information about the matter and I am just guessing. My suggestion is that Google about forcing the packages after Googling make up your mind if you dare to try forcing the older package. 

Hopefully someone else has more definite information.

edit: Excellent beaten to it by more proper info :-)

---

### Post by desconocido on 2010-06-18
> **Naggobot said:**
> ...my guess is that the repository needs to be first changed to older repository and then after reloading the package information the package can be forced.

Thanks, I had kept the .deb files from two years ago, so I was trying them first.

---

### Post by desconocido on 2010-06-18
> **radddi said:**
> First I completely uninstalled CUPS as well as all of the ip1500 install files (bjfilter*). After reinstallation I downloaded the official drivers from CANON: [http://software.canon-europe.com/software/0022415.asp?model=](http://software.canon-europe.com/software/0022415.asp?model=)

I installed them through alien and then followed the following tutorial from point 5 onward: [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500) . Then miraculously, the printer started sucking in pages for the first time in ages.

I have got as far as using alien to make the .deb files. More later.

---

### Post by Naggobot on 2010-06-18
I was surfing the threads the other day and stumbled on an info that you need may also need to tell the synaptic that "do not upgrade" the packages in the future. Otherwise the synaptic will attempt to upgrade the packages when never come available. It may be that menu option lock version works (i seem to remember that there is such a option in the menu.)

Check 

[http://ubuntuforums.org/showthread.php?t=1371844](http://ubuntuforums.org/showthread.php?t=1371844)

post #4

---

### Post by desconocido on 2010-06-21
Awesome. I followed the tutorial at [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500) and it all works. Astonishing.

The only difference between what I was doing before and what now, seems to be

```
cd /usr/lib
sudo ln -s libpng12.so.0 libpng.so.2
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libxml2.so.2 libxml.so.1
```

Interesting also that the .deb files produced by alien are smaller or much smaller now than when I did this a couple of years back:

old files
```
-rwxrwxr-x 1 bob  bob    23661 2005-04-08 09:16 bjfilter-common-2.50-2.i386.rpm
-rw-r--r-- 1 root root 6903260 2008-10-30 23:44 bjfilter-common_2.50-3_i386.deb
-rwxrwxr-x 1 bob  bob  1870067 2005-04-08 09:15 bjfilter-pixmaip1500-2.50-2.i386.rpm
-rw-r--r-- 1 root root 1860240 2008-10-30 23:44 bjfilter-pixmaip1500_2.50-3_i386.deb
-rwxrwxr-x 1 bob  bob    89132 2005-04-08 09:15 bjfilter-pixmaip1500-lprng-2.50-2.i386.rpm
-rw-r--r-- 1 root root   87064 2008-10-30 23:44 bjfilter-pixmaip1500-lprng_2.50-3_i386.deb
```

new files
```
-r-xr-xr-x 1 bob  bob    23661 2005-04-08 09:16 bjfilter-common-2.50-2.i386.rpm
-rw-r--r-- 1 root root   23512 2010-06-15 20:46 bjfilter-common_2.50-3_i386.deb
-r-xr-xr-x 1 bob  bob  1870067 2005-04-08 09:15 bjfilter-pixmaip1500-2.50-2.i386.rpm
-rw-r--r-- 1 root root 1863884 2010-06-15 20:46 bjfilter-pixmaip1500_2.50-3_i386.deb
-r-xr-xr-x 1 bob  bob    89132 2005-04-08 09:15 bjfilter-pixmaip1500-lprng-2.50-2.i386.rpm
-rw-r--r-- 1 root root   86216 2010-06-15 20:47 bjfilter-pixmaip1500-lprng_2.50-3_i386.deb
```

Many thanks for your help.

---

