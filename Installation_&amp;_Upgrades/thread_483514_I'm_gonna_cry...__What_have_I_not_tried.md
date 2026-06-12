---
title: "I'm gonna cry...  What have I not tried???"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by jeepfreak2002 on 2007-06-24
I decided to finally go 100% Linux after getting Guild Wars to work on my machine at work.

I come home w/ a new HD and install 7.04 clean on this machine:

ASUS MN2-E nForce 570 MCP Ultra
AMD 5600 X2
2 GIG RAM
120 GIG Seagate SATA HD
XFX nVidia 7600GT

7.04 installs fine.  I go to run an update and the updates download, but they crash on install.  Everything is corrupted.  I changed the date in the BIOS, and by default the system rescans (I did this by accident) and found errors on the root directory.  I have:

Swapped HD's
Reinstalled 7.04
Re-downloaded and Re-burned 7.04 - then reinstalled
Replaced SATA Cables
Ran HD scan using Seagate tools
Installed Edgy, then Upgraded to 7.04 (through update manager w/o disc) (interestingly the install seemed to work, but the first package that I tried to install (nVidia driver through restricted devices update still crashed) 
Checked MOBO BIOS - they are pretty up to date, and the only update is for increased CPU support.

I have come to the conclusion that this has to be a BIOS issue.  There is some setting that is pissing things off that I can not figure out.  I had found 1 setting that pissed Edgy off, and I disabled that.  I saw APCI setting sometimes cause issues, but I can't turn them off.  I can select S1, S3, or both.  Any other ideas ????

I'm also getting this now when I run Synaptic:

E: /var/cache/apt/archives/python2.5-minimal_2.5.1-0ubuntu1_i386.deb: corrupted filesystem tarfile - corrupted package archive

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by jeepfreak2002 on 2007-06-25
ya know...

This has to be a software issue.  If I install Edgy I can run 171 updates with no prob.  Feisty is causing the issues.  Is there anyone on here that knows enough about the differences between the 2 distro's to know what might be causing this?

Thanks

---

### Post by david_sedman on 2007-08-13
first download the package from here
[http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/p/python2.5/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/p/python2.5/)

then second after downloading copy download file to corupted location by opening terminal and using this comand

sudo cp download_files_location_here corupted_files_directory_location_here

i had the same problem and this fixed it for me.

---

### Post by rbmorse on 2007-08-13
You indicated that you reburned the CD - that's a good step, but did you run the "check cd" from the boot menu?

---

