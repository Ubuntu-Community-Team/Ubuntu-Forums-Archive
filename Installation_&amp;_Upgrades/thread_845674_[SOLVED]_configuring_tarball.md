---
title: "[SOLVED] configuring tarball"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by rtrdom on 2008-06-30
In Feisty, Gutsy, and now Hardy, if I download a tarball I put it in
usr. Next if I "tar -xvfz [filename].tar.gz" the screen scrolls a lot of
information past. I believe - from reading all the "how-to's" - the 
next step is to cd to the directory with a similar name as the tarball. Then when in the similarly named directory and I type ./configure, nothing
has ever happened. The terminal tells me "bash: /configure: No such file or
directory". It doesn't matter if I type ./configure, configure, .configure,
or /configure, the result is the same. What are the specific correct steps to install a tarball in Ubuntu Hardy Heron.? There use to be a good tutorial on this but can't find it now.
Any help appreciated.

---

### Post by tamoneya on 2008-06-30
sometimes you have to set the permissions to add executability.  ```
chmod +x configure
./configure
``` if that still doesnt work please post the output of ```
ls -l
```Some tar balls are different and require that you compile with make, make install.

---

### Post by rtrdom on 2008-06-30
Thank you for the response.  When I type chmod +x configure, the result
is "no such file or directory" Same result using sudo. Therefore, the re-sult of ls -l is posted here:
:/usr$ ls -l
total 10892
drwxr-xr-x   2 root root    36864 2008-06-30 17:56 bin
drwxr-xr-x   2 root root     4096 2008-06-22 08:57 games
drwxr-xr-x   2 root root     4096 2008-06-30 17:52 hplip-2.8.6
-rw-r--r--   1  777 jim  11001601 2008-06-30 17:12 hplip-2.8.6.tar.gz
drwxr-xr-x  34 root root     4096 2008-06-30 17:56 include
drwxr-xr-x   8 root root     4096 2008-06-27 19:21 jre1.6.0_06
drwxr-xr-x 170 root root    45056 2008-06-30 17:56 lib
drwxr-xr-x  10 root root     4096 2008-04-22 12:48 local
drwxr-xr-x   2 root root    12288 2008-06-29 08:38 sbin
drwxr-xr-x 300 root root    12288 2008-06-30 17:56 share
drwxrwsr-x   6 root src      4096 2008-06-22 08:58 src
drwxr-xr-x   2 root root     4096 2008-04-22 12:51 X11R6

I have the same problem with hplip-2.8.6 and jre1.6.0_06. Neither will
configure.

---

### Post by rtrdom on 2008-06-30
Thank you for the response.  When I type chmod +x configure, the result
is "no such file or directory" Same result using sudo. Therefore, the re-sult of ls -l is posted here:
:/usr$ ls -l
total 10892
drwxr-xr-x   2 root root    36864 2008-06-30 17:56 bin
drwxr-xr-x   2 root root     4096 2008-06-22 08:57 games
drwxr-xr-x   2 root root     4096 2008-06-30 17:52 hplip-2.8.6
-rw-r--r--   1  777 jim  11001601 2008-06-30 17:12 hplip-2.8.6.tar.gz
drwxr-xr-x  34 root root     4096 2008-06-30 17:56 include
drwxr-xr-x   8 root root     4096 2008-06-27 19:21 jre1.6.0_06
drwxr-xr-x 170 root root    45056 2008-06-30 17:56 lib
drwxr-xr-x  10 root root     4096 2008-04-22 12:48 local
drwxr-xr-x   2 root root    12288 2008-06-29 08:38 sbin
drwxr-xr-x 300 root root    12288 2008-06-30 17:56 share
drwxrwsr-x   6 root src      4096 2008-06-22 08:58 src
drwxr-xr-x   2 root root     4096 2008-04-22 12:51 X11R6

I have the same problem with hplip-2.8.6 and jre1.6.0_06. Neither will
configure.

Tried make and make install. result was "make: *** No targets specified and no makefile found.  Stop."

---

### Post by tamoneya on 2008-06-30
sorry i failed to specify. I wanted you to run both of the above commands in the directory created by untaring the tar ball.

---

### Post by rtrdom on 2008-07-01
Thank you Tamoneya for the reply. I'll post all I did since your last. The
results are not encouraging.
 jim@Bravo:~$ cd /usr/hplip-2.8.6
jim@Bravo:/usr/hplip-2.8.6$ chmod +x configure
chmod: cannot access `configure': No such file or directory
jim@Bravo:/usr/hplip-2.8.6$ ./configure
bash: ./configure: No such file or directory
jim@Bravo:/usr/hplip-2.8.6$ make
make: *** No targets specified and no makefile found.  Stop.
jim@Bravo:/usr/hplip-2.8.6$ make install
make: *** No rule to make target `install'.  Stop.
jim@Bravo:/usr/hplip-2.8.6$

Perhaps this will point to something I've done wrong.
Thanks again.

---

### Post by rtrdom on 2008-07-01
The solution ? for me was to go to: [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) and follow instructions for the Regular Tar Ball. All was
done automatically and in the end, Xsane "found" the printer. Somewhere in
the process of upgrading to 8.04, something caused the printer to lose the
ability to respond correctly to Xsane, or the upgrade caused Xsane to
send old data requests to the hp 7410. Now, all I have to do is find a
solution to unpacking tarballs and configuring them, but I have the time
to do so now.
Thank you Tamoneya for your assistance.

---

