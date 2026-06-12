---
title: "Problem when downloading latest updates!"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by mont on 2007-08-02
Hey, got a big problem.
After downloading the latest updates my APT get screwed:(

this is what i get in console.


Preparing to replace libgl1-mesa-glx 6.5.2-3ubuntu7 (using .../libgl1-mesa-glx_6.5.2-3ubuntu8_amd64.deb) ...
Unpacking replacement libgl1-mesa-glx ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu8_amd64.deb (--unpack):
 error creating symbolic link `./usr/lib/libGL.so.1': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I can't get it back, either install new packages until this is fixed.

what to do? would appreciate any help:)
Guess others have this problem also,

---

### Post by UnrulyGrrl99 on 2007-08-03
I am having the same problem:
```
Preparing to replace libgl1-mesa-glx 6.5.2-3ubuntu7 (using .../libgl1-mesa-glx_6.5.2-3ubuntu8_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu8_i386.deb (--unpack):
 error creating symbolic link `./usr/lib/libGL.so.1': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried converting the .deb file to a tarball using alien, then manually copying over the files and creating the symlink.  Problem is that APT is still stuck.  I cant even get it to _remove_ libgl1-mesa-glx.

---

### Post by Pumalite on 2007-08-03
You can try this: sudo dpkg --configure -a
If that doesn't work, you can try this: sudo dpkg --remove --force-remove-<package name>

---

### Post by UnrulyGrrl99 on 2007-08-03
dpkg --remove --force-   did work.
Unfortunately I can't even install the version of libgl1-mesa-glx that worked just before the upgrade (libgl1-mesa-glx_6.5.2-3ubuntu7).  I'm getting the same symbolic link creation error.

I spent hours yesterday getting everything configured/installed on my laptop so I could run Beryl.  Beryl will of course not run without all the GL libs in place.  

:(

any suggestions on getting back on track with the previous version of the various mesa GL libs?

---

### Post by Pumalite on 2007-08-03
Sorry, can't help you there. Somebody that knows will jump in hopefully.

---

### Post by UnrulyGrrl99 on 2007-08-03
I FIXED IT!!!

I decided to do one last search in the forums (this time for "error creating symbolic link" and "no such file or directory"), and found this post:
[http://ubuntuforums.org/showthread.php?t=420073](http://ubuntuforums.org/showthread.php?t=420073)

which mentions trying the command:
```
dpkg-divert --remove /usr/lib/libGL.so.1
```

It found a link that fglrx had set up (even though I removed fglrx).
I re-ran "apt-get -f install" after that, it tried to install libgl1-mesa-glx again, and this time it worked.

Hopefully mont, you can do the same to fix it on your system.

I'm back up and running with Beryl - woohoo!

---

### Post by mont on 2007-08-03
You are a hero! :)

good job;)
I read the forum for many hours without a good solution to this problem.
Thank's alot ;)

---

