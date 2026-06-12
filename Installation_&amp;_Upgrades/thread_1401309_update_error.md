---
title: "update error"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by ekehdi on 2010-02-07
When i come to update manager i get the following message and besides being new to ubuntu, i havent figured that out on the problem, anyone help me fix it please?

Thanks in advance and pardon my pour english.


xxxxxxxxxxxxxxxxxx:popcorn: 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) karmic Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) karmic-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: GPG error: [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) karmic-backports Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic/Release](http://br.archive.ubuntu.com/ubuntu/dists/karmic/Release)  

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release](http://br.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release)  

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.bz2](http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.bz2](http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.bz2](http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.bz2](http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.bz2](http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.bz2](http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.bz2](http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.bz2](http://br.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by suseendran.rengabashyam on 2010-02-09
Hi,

Try the following steps and let me know if it works

1) See whether you can access the Internet, you need to have a proper connection to install any packages.

2) There might me some intermittent problem with [http://br.archive.ubuntu.com/](http://br.archive.ubuntu.com/) . You can change the repository and try update again. Go to System->Administration->Synaptic Package Manger->Settings->Repositories, in the 'Download From:' drop-down menu select the 'Main Server'. Don't forget to click the 'Reload' button and then try installing a package.

3) If your machine is running behind a proxy server, you have to clearly mention that. Go to System->Administration->Synaptic Package Manger->Settings->Preferences->Network, there you can mention the proxy server's IP address/Port. If you don't need to go through a proxy server, you can check 'Direct connection to the internet'. Don't forget to click the 'Reload' button and then try installing a package.

---

### Post by MelDJ on 2010-02-09
the first four errors are because you have added the cdrom as a repo but the cdrom is not in your drive.
 remove it from the repos list by going to system-admin-software sources and uncheck the cdrom from other software

---

### Post by monkeyface766 on 2010-02-17
Removing the backports (unsupported) worked for me :

sudo apt-get remove linux-backports-modules-karmic-generic

sudo apt-get autoremove

restart computer

My problem seemed to have stemmed from a recent attempt to get my microphone working. I had installed linux-backports-modules-alsa-karmic-generic. Removing that alone did not fix it. But removing all of the backports modules worked.

---

