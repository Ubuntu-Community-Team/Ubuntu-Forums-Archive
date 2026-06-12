---
title: "update-manager: no update possible"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by winfried.moser on 2014-07-17
Dear Listers,

I have Ubuntu 12.04 and can't update the system because of an "unresolvable problem". At least that's what the update-manager tells me. 

Typing "sudo apt-get check" into the terminal brings me to the following message.

E:Encountered a section with no Package: header, 
E:Problem with MergeList /var/lib/apt/lists/at.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en, 
E:The package lists or status file could not be parsed or opened.

Any suggestions where to proceed?
Thanks in advance!

Winfried

---

### Post by Frogs Hair on 2014-07-17
Try the following and report any errors . ```
sudo-apt-get update  
``` If there are no errors run the following to install updates.```
sudo apt-get upgrade
``` Close the update manager before using the commands.

---

### Post by winfried.moser on 2014-07-18
Dear Frogs-Hair!

Thanks for your reply! Typing "sudo apt-get update" I get the Errors and Warnings stated below. I guess, the problems have to do with some software, that I installed months ago (tried to get an actual version of R, Latex, vim and vim-r-plugin running, which was very complicated). How should I go on now? 

Thanks!
Winfried

Errors & Warnings

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 3E07F5B89A690089 Launchpad PPA for TeX Live Backports
W: Failed to fetch [http://ubuntu.inode.at/ubuntu/dists/raring-backports/main/binary-amd64/Packages](http://ubuntu.inode.at/ubuntu/dists/raring-backports/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  
W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
W: Failed to fetch [http://ubuntu.inode.at/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages](http://ubuntu.inode.at/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ubuntu.inode.at/ubuntu/dists/raring-backports/universe/binary-amd64/Packages](http://ubuntu.inode.at/ubuntu/dists/raring-backports/universe/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ubuntu.inode.at/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://ubuntu.inode.at/ubuntu/dists/raring-backports/main/binary-i386/Packages)  404  Not Found
W: Failed to fetch [http://ubuntu.inode.at/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://ubuntu.inode.at/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  404  Not Found
W: Failed to fetch [http://ubuntu.inode.at/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://ubuntu.inode.at/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  404  Not Found
W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/at.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

### Post by winfried.moser on 2014-07-18
Thanks to Wild Man I found an answer in this thread 
[http://ubuntuforums.org/showthread.php?t=1813614](http://ubuntuforums.org/showthread.php?t=1813614)
That worked for me!
Winfried

---

