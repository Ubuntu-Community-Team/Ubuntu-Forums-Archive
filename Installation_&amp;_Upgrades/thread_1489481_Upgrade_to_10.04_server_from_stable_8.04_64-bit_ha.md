---
title: "Upgrade to 10.04 server from stable 8.04 64-bit has caused lots of dependency issues"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by hopper333 on 2010-05-21
I recently upgraded from a very stable 8.04 server (amd64) -> 10.04 server via the normal route i.e. do a last update and safe-upgrade on 8.04 and then dist-upgrade -> 10.04.

The update-manager kicked in and downloaded a lot of files, then started installing them over my previous installation as expected.  Some way through this I noticed a bunch of errors from dpkg as downloaded files couldn't be configured.  At the end, there were a lot of errors so I set about removing things that seemed to be involved.  They all seemed related to gnome and gtk apps and libraries so I removed a lot of this stuff and took it down to the bare bones i.e. ssh, samba, ufw and it all seems to be working fine (albeit with a *gigantic* memory footprint with nothing running what is all this ureadahead stuff doing on a server?).  However, when I try to install anything even remotely desktop'y (e.g. synaptic, gnuplot, gedit) I am back in dependency hell.

I am really not used to this - my experience of debian and ubuntu in the past has been excellent package management.  The common feature when the packages can't be configured is messages like the following:

```
undefined symbol: g_malloc0_n
```

which leads me to think that glib, gnome or gtk may be involved.  A very common dependency which cannot be installed (even though there has been a recent update on the repos) is **shared-mime-info**.

Here is some output from aptitude when I recently tried to install gnuplot and the usual suspects couldn't be configured:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up shared-mime-info (0.71-1ubuntu2) ...
update-mime-database.real: symbol lookup error: update-mime-database.real: undefined symbol: g_malloc0_n
dpkg: error processing shared-mime-info (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on shared-mime-info; however:
  Package shared-mime-info is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxgtk2.8-0:
 libwxgtk2.8-0 depends on libgtk2.0-0 (>= 2.17.5); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libwxgtk2.8-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnuplot-x11:
 gnuplot-x11 depends on libwxgtk2.8-0 (>= 2.8.10.1); however:
  Package libwxgtk2.8-0 is not configured yet.
dpkg: error processing gnuplot-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnuplot:
 gnuplot depends on gnuplot-x11 (>= 4.2.6-1); however:
  Package gnuplot-x11 is not configured yet.
dpkg: error processing gnuplot (--configure):
 depenNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                 No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                                                                                                    No apport report written because MaxReports is reached already
                                         dency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-bin:
 libgtk2.0-bin depends on libgtk2.0-0 (>= 2.20.0-0ubuntu4); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgtk2.0-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 shared-mime-info
 libgtk2.0-0
 libwxgtk2.8-0
 gnuplot-x11
 gnuplot
 libgtk2.0-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I'm quite happy at the command line so if anyone can suggest some dpkg, apt-get or aptitude commands to diagnose or resolve this issue then I would really appreciate it.  I don't mean "use -f to force it" but something to work out why it has happened and make sure it doesn't happen again.  Feel free to ask for more diagnostic output if you need it.

Many thanks in advance

Michael

---

### Post by bcschmerker on 2010-05-21
I ran into the same problem on my first attempt to upgrade from 8.04.4 to 10.04, as the two distributions require completely different versions of most of the same packages; many of the 10.04 versions haven't appeared even on PPA's for modifications to 8.04.x.  In my case, I was left with an unbootable system for a short and had to clean-install 10.04 (in my case, from the AMD64 Install CD, as I use an "all-AMD" 'box) to get into a usable state.

---

### Post by hopper333 on 2010-05-21
wow :(

I'm finding it hard to believe that an officially-released server upgrade (with nothing unusual installed) from one amd64 LTS version to another is as broken as that - to require a clean install.

Is anyone else surprised or were we warned and I didn't see it?  Any server admins out there who can compare against upgrades with recent versions of Debian (or Mint)?

M

---

### Post by hopper333 on 2010-06-03
OK I think I have established the cause.

It seems that a number of programs cannot find symbols required.

during install of shared-mime-info:
update-mime-database.real: symbol lookup error: update-mime-database.real: undefined symbol: g_malloc0_n

trying to run synaptic or emelfm2:
symbol lookup error: /usr/lib/libgobject-2.0.so.0: undefined symbol: g_array_ref

So this is pointing to /usr/lib/libgobject-2.0.so.0

Going to the directory gives this (version renamed to old_ was by me as an old version seems to be hanging around but it makes no difference either way).

/usr/lib# ls -alt *libgobject*
lrwxrwxrwx 1 root     26 2010-05-28 22:01 libgobject-2.0.so.0 -> libgobject-2.0.so.0.2400.1
-rw-r--r-- 1 root 290184 2010-05-09 12:23 libgobject-2.0.so.0.2400.1
-rw-r--r-- 1 root 281104 2008-08-08 14:43 old_libgobject-2.0.so.0.1600.4
# ldd libgobject-2.0.so.0
	linux-vdso.so.1 =>  (0x00007fff801ff000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00007fd7cdc37000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007fd7cda02000)
	librt.so.1 => /lib/librt.so.1 (0x00007fd7cd7f9000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007fd7cd539000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00007fd7cd30b000)
	libc.so.6 => /lib/libc.so.6 (0x00007fd7ccf88000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fd7ce086000)
	libselinux.so.1 => /lib/libselinux.so.1 (0x00007fd7ccd6a000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007fd7ccb66000)

Any clues here for anyone?

M

---

