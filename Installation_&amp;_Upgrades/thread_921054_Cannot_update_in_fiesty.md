---
title: "Cannot update in fiesty"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by linuxlearn on 2008-09-15
I am running fiesty 7.04 and can no longer do updates. I want
to upgrade firefox. Here is the output from apt-get update

(The last 15-20 lines)

Get:7 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas/all Packages [13.4kB]                             
Fetched 34.8kB in 6s (5141B/s)                                                                     
Reading package lists... Done
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: You may want to run apt-gety update to correct these problems

-----------


Any ideas.

---

### Post by kostkon on 2008-09-15
Go to *System -> Administration -> Software Sources* and in the *Third Party Software* tab you'll find this repository. Just disable it. 

Also, remove any duplicate entries you will find there.

Then go to *System -> Administration -> Update Manager* to check for new updates.

---

### Post by linuxlearn on 2008-09-16
That got rid of the errors. Thanks.  But it still will not update to the latest firefox.

I did a reload on the update manager.  Also did a search for the firefox package in 
synaptic package manager, and the latest did not exist their either.

---

### Post by zvacet on 2008-09-16
Maybe [this]("http://ubuntuzilla.wiki.sourceforge.net/") is what you are looking for.

If you want to use **feisty-seveas** repo then type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 49A120FD1135D466
gpg --export --armor 49A120FD1135D466 | sudo apt-key add -

---

### Post by linuxlearn on 2008-09-17
I have decided to do a distrobution upgrade to 7.10 to see if that helps.  Because 
the above did not work either.

Thanks

---

