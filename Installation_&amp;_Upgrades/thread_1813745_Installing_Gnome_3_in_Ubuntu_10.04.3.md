---
title: "Installing Gnome 3 in Ubuntu 10.04.3"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by $uraj on 2011-07-28
Hi ubuntu users.. I installed Ubuntu 10.04.3 now. And i need help in installing Gnome 3 in this 10.04. I tried to add the ppa and reload the synaptic, but got an error.

the ppa is : ppa:ubuntu-desktop/gnome3-builds


but am getting error saying 


Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I have good connectivity to internet.

 Do help about steps to be taken to install gnome 3 in 10.04.3


Thanks :)
[IMG]file:///home/suraj/Desktop/Gnome3Error.png[/IMG]

---

### Post by Antarctica32 on 2011-08-07
I got a similar error when I did the same thing.

---

### Post by Basher101 on 2011-08-07
Can you even run gnome 3? Try Fedora 15 and look if gnome 3 works first

---

### Post by burhangondal on 2011-09-30
> **$uraj said:**
> Hi ubuntu users.. I installed Ubuntu 10.04.3 now. And i need help in installing Gnome 3 in this 10.04. I tried to add the ppa and reload the synaptic, but got an error.

the ppa is : ppa:ubuntu-desktop/gnome3-builds


but am getting error saying 


Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I have good connectivity to internet.

 Do help about steps to be taken to install gnome 3 in 10.04.3


Thanks :)
[IMG]file:///home/suraj/Desktop/Gnome3Error.png[/IMG]

after u have added the PPA, click on the gnome 3 ppa in synaptic package manager, click edit, and change the distro name to NATTY from LUCID....refresh and BOOM:popcorn:

---

