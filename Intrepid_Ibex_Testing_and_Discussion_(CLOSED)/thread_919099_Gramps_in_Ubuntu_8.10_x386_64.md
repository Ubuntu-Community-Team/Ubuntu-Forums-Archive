---
title: "Gramps in Ubuntu 8.10 x386 64"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lrbradford on 2008-09-13
Hi,  Recently reformatted and installed Ubuntu x86 64m and updated to Intrepid.  I used to run Gramps genealogy program in 8.04.  Not able to do so on 8.10.

I removed Gramps, and tried apt-get in a terminal, and this is what I saw:

----------------------------------------------------------------
lynn@lynn-laptop:~$ sudo apt-get install gramps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu libimlib2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gramps
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4719kB of archives.
After this operation, 20.7MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gramps
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
lynn@lynn-laptop:~$ 
------------------------------------------------------------------

I'm not sure if this is the cause of my woes, because I always used the Add/Remove Application GUI before, and never saw a message like that.  When I tried opening Gramps, the task bar showed "Starting..." but nothing ever happened.

Any ideas?

---

### Post by inportb on 2008-09-13
... probably because you don't have Gramps installed. Do you have any nonstandard repositories enabled? Gramps is in Universe, so you should not have to get it from elsewhere.

If you do prefer to get Gramps from a different repository, and trust that repository, you should either install it without verification or add the repository's public key to your keyring.

---

### Post by lrbradford on 2008-09-20
Yes, Gramps is installed, was installed, and is installed again with the same results.  Acts like it is starting, but nothing happens.  Very frustrating, along with this glx thing that keeps shutting down.  I keep sending error reports, and I see where others are having the same issue.  I wonder if the two are some how connected?

---

### Post by lrbradford on 2008-09-20
OK..here's the terminal output when I run gramps from the terminal after using apt-get:

8<----------------------------------------------------------------------

lynn@lynn-laptop:~$ sudo apt-get check gramps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lynn@lynn-laptop:~$ gramps
Upgrading INI file
error: duplicate REP tables used
Failure loading aff file /usr/share/myspell/dicts/en_ZA.aff
Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes.
Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes.
*** glibc detected *** /usr/bin/python: double free or corruption (out): 0x0000000001e029d0 ***

8<snip---------------------------------------------------------------

I Googled that error and found is was an issue with many installs, but can't seem to catch a fix.  Anybody have any ideas?

LB

---

### Post by ccw on 2008-09-20
I'm fine here:

x:~$ apt-cache showpkg gramps
Package: gramps
Versions: 
3.0.1-1 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid_universe_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid_universe_binary-i386_Packages
                  MD5: 74255c718dd2d699400c8ac664c1fe07


Reverse Depends: 
Dependencies: 
3.0.1-1 - librsvg2-common (0 (null)) python (2 2.4.4-6) python-central (2 0.6.6) python-glade2 (0 (null)) python-gnome2 (0 (null)) python2.5 (0 (null)) scrollkeeper (0 (null)) graphviz (0 (null)) python-gnome2-desktop (0 (null)) python-gnome2-extras (0 (null)) python-reportlab (0 (null)) ttf-freefont (0 (null)) xdg-utils (0 (null)) gramps-common (0 (null)) gramps-extending-doc (0 (null)) gramps-manual (0 (null)) python-gtk-1.2 (0 (null)) gramps-extending-doc (0 (null)) gramps-manual (0 (null)) 
Provides: 
3.0.1-1 - 
Reverse Provides:

---

### Post by phenest on 2008-09-20
> **lrbradford said:**
> E: Some packages could not be authenticated
lynn@lynn-laptop:~$ 
------------------------------------------------------------------

Any ideas?

This error is not necessarily related to GRAMPS. Have you added any 3rd party software to the repositories? If so, one of them may not be authenticating, and you may want to try disabling them for now, as they may have no support for Intrepid yet.

---

### Post by lrbradford on 2008-09-20
The only other programs I have added is OOo Database and the Sword Bible Study program from the Sword Project.  I'm removing the OOo Database and see what develops.

I'm not a terminal Commando.  Any commands I could run to post its output to help figure this out?

Thanks,

LB

---

### Post by lrbradford on 2008-09-20
How do I disable or revert back to original repositories?

While typing this post, Gramps didn't open again, but Apport gave me a report to send to developers. Wish I new hwat part of that 5.3 Mb report to post!

LB

---

### Post by UbuWu on 2008-09-20
Apport has a button to send it and it will automatically send the whole report.

---

### Post by lrbradford on 2008-09-20
LOL...I know that.  Thanks anyway.  I submitted the report, so I'll see what the big brains have to add.

---

