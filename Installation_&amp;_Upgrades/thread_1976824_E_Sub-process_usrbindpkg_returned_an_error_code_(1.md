---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by degvik on 2012-05-09
Hi all,

I just installed new Ubuntu 12.04, and tried to install iprint client that only provides rpm packages. I created deb package out of it using 'alien', and installed it, but it didn't work correctly, so I tried to remove the package and it seems I did it in a wrong way, so some information was deleted, but some wasn't. No I'm blocked from using apt-get at all (even to install other things). That's what I get after I run almost any command: 

```
~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  novell-iprint-xclient-sl
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,763 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 183644 files and directories currently installed.)
Removing novell-iprint-xclient-sl ...
/var/lib/dpkg/info/novell-iprint-xclient-sl.postrm: line 5: test: remove: integer expression expected
/var/lib/dpkg/info/novell-iprint-xclient-sl.postrm: line 14: sbin/insserv: No such file or directory
dpkg: error processing novell-iprint-xclient-sl (--remove):
 subprocess installed post-removal script returned error exit status 127
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 novell-iprint-xclient-sl
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems it cannot remove package "novell-iprint-xclient-sl" because something is already missing...

Do you have any idea on how to fix it, without fully reinstalling the ubuntu again? Thanks in advance!

---

### Post by degvik on 2012-05-09
bump.
Maybe there is sub-forum which is better for such a question? Thank you for any info on the matter! I'm still in the woods, considering to reinstall ubuntu from scratch :(

---

### Post by APWi on 2012-09-12
I had exactly the same problem.  Bit of a hack, but insert a # at the beginning of the last line of 
       /var/lib/dpkg/info/novell-iprint-xclient-sl.postrm
i.e. in front of  sbin/insserv
This will enable the novel-iprint package to uninstall without returning an error, then other packages can be installed again.  I've not observed any adverse effects; probably a good idea to reboot after uninstall.

---

