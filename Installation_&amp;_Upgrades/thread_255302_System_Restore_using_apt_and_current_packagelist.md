---
title: "System Restore using apt and current packagelist?"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by tsiMental on 2006-09-11
Hi, I've managed to screw up my apt by forcefully installing a custom package. - Which I probably shouldn't have.

I thought I would use tar to backup my homefolder, sources.list, xorg.conf and rc.local.

Then, I thought I should make a list of all the packages I've installed.
dpkg -l > packages.list

How should I go about to reinstall all these packages for instance from a LiveCD? - In the easiest possible way. I don't want to go throught the list and choose package by package in synaptic.

---

### Post by ajgreeny on 2006-09-11
OK, this may not work but have you tried uninstalling the forced package with aptitude, instead of apt-get?  I know it's just another front end for apt, but it's just a thought that it might work.  Otherwise, can you uninstall apt using dpkg? I don't even know if it is possible if you didn't install it that way.  Or perhaps just download the apt package direct and then use dpkg to reinstall it?

Just some possibillities and other thoughts you may not have had.

Best of luck!

---

### Post by tsiMental on 2006-09-11
Thanks for the thoughts ajgreeny.

I accually managed to fix this problem without having to reinstall ubuntu :D 

It wasn't actually the apt-package which was broken. I had installed Projekt Looking Glass, using a daily built cvs snapshot .deb package... I forced it to install using dpkg -i --force-all [package]. Which is not a good idea.

The way I fixed it:
I found all the files that the package lg3d-core had installed was found in the following directories, using dpkg -L lg3d-core:
/usr/shared/lg3d
/etc/lg3d

dpkg (and apt too, I think) stores their information on installed packages in:
/var/lib/dpkg
and
/var/lib/dpkg/info

So I uninstalled the lg3d packages that were not broken using dpkg -r [package]. And deleted the directories:
/usr/shared/lg3d
/etc/lg3d

I removed all the files about lg3d in /var/lib/dpkg/info:
rm /var/lib/dpkg/info/lg3d*

And lastly I removed all info about lg3d in the files 'available' and 'status' in /var/lib/dpkg.

Then apt-get, synaptic, adept and the others were working again!! \o/

---

