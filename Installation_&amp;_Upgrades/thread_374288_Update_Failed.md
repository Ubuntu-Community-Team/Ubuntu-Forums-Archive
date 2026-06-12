---
title: "Update Failed"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by castoroil97 on 2007-03-02
Hi everyone

My name is David and I have been Windoze free for 1 week

I love Ubuntu

2 kinks need to be worked out.

1- my AWE 64 ISA card will not work, unless I run sudo modprobe snd-sbawe
and then log out, then back in.  I tried ALSA site on trying to get the card in, but it did not work.
If you have a suggestion, please let me know.

I am willing to buy a new card, as long as it is inexpensive, any suggestions?

2- I did the update (the orange and white icon in the systray (i know, a windows term)
after reboot I got the error:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I ran apt-get install -f

and below was the output..how can I fix that?

thanks in advance

root@strskow:/home/casterai# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgnet2.0-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openoffice.org-common
Recommended packages:
  openoffice.org-style-crystal openoffice.org-style-hicontrast
The following packages will be upgraded:
  openoffice.org-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/11.4MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 117672 files and directories currently installed.)
Preparing to replace openoffice.org-common 2.0.4-0ubuntu2 (using .../openoffice.org-common_2.0.4-0ubuntu4_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.0.4-0ubuntu4_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
***
* Updating MIME database in /usr/share/mime...
Wrote 480 strings at 20 - 27dc
Wrote aliases at 27dc - 2990
Wrote parents at 2990 - 3360
Wrote literal globs at 3360 - 33c4
Wrote suffix globs at 33c4 - 674c
Wrote full globs at 674c - 6770
Wrote magic at 6770 - bd80
Wrote namespace list at bd80 - bd90
***
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-common_2.0.4-0ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kateikyoushi on 2007-03-02
Seems that's a corrupted deb. I would delete it. Then update and upgrade.

```
sudo rm /var/cache/apt/archives/openoffice.org-common_2.0.4-0ubuntu4_all.deb
```

---

### Post by castoroil97 on 2007-03-03
:guitar: 


that did the trick, thank you very much!!!

---

