---
title: "GPG no default key error"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by gnitram on 2010-01-18
I have followed this [http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)
 
in order to install XBMC and I got this message in the terminal:
 
asrock@asrock-desktop:~$ sudo add-apt-repository ppa:team-xbmc 
[sudo] password for asrock: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 189701DA570C56B9488EF60A6D975C4791E7EE5E 
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com 
gpg: key 91E7EE5E: "Launchpad PPA for XBMC for Linux" not changed 
gpg: Total number processed: 1 
gpg:              unchanged: 1 
asrock@asrock-desktop:~$ sudo add-apt-repository ppa:team-xbmc 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 189701DA570C56B9488EF60A6D975C4791E7EE5E 
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com 
 
gpg: key 91E7EE5E: "Launchpad PPA for XBMC for Linux" not changed 
gpg: Total number processed: 1 
gpg:              unchanged: 1 
asrock@asrock-desktop:~$      $ sudo apt-get update 
$: command not found 
 
 
So I then tried to add what I think is the relevant GPG key by typing this in terminal:
 
asrock@asrock-desktop:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 189701DA570C56B9488EF60A6D975C4791E7EE5E
 
 
this message appeared;
 
gpg: requesting key 91E7EE5E from hkp server subkeys.pgp.net
gpg: key 91E7EE5E: public key "Launchpad PPA for XBMC for Linux" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
 
I again then followed the XBMC install instructions and got the following again:
 
asrock@asrock-desktop:~$ sudo add-apt-repository ppa:team-xbmc
[sudo] password for asrock: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 189701DA570C56B9488EF60A6D975C4791E7EE5E
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg: key 91E7EE5E: "Launchpad PPA for XBMC for Linux" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
asrock@asrock-desktop:~$ 
 
Excuse my ignorance, but I don't know why this is not working, would anybody be kind enough to help me. It is running on a Karmic 9.10, only been installed a few days ago and alll of the updates completed.
 
Many thanks in anticipation

---

### Post by phillw on 2010-01-18
Hi, you can add 3rd party repositories this way --> [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories)

Take note of the warning to check it is compatible with Ubuntu, for adding keys, you need to sudo the commands.

Regards,

Phill.

---

### Post by plucky on 2010-01-18
> asrock@asrock-desktop:~$ $ sudo apt-get update
$: command not found



Extra $ is why the command doesn't run.Try again without the $

---

### Post by gnitram on 2010-01-19
Thanks so much , the problem was solved by adding the gpg key via following the advice I received here:

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/97838](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/97838)

XBMC is now installed and am loving it and ubuntu!:o

---

