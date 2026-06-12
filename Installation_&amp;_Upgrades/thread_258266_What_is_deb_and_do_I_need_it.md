---
title: "What is deb? and do I need it"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by madsurfer on 2006-09-15
Hi
I am a new user to Linux, I have installed Ubuntu 6.06 and so far it has been a good experience, however in trying to get to my old ntfs drive where all my data is I have come unstuck. The current install does not include ntfs-3 which I believe is still in beta. However I decided to install it anyway but fell at the first hurdle, what is "deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main" what does deb mean? I am following the procedure at "https://wiki.ubuntu.com/ntfs-3g" for installing ntfs-3. Is this right?

---

### Post by mitch.c on 2006-09-15
> **madsurfer said:**
> what is 'deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main' what does deb mean?

'deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main' is what should be added to /etc/apt/sources.list to enable synaptic/apt-get/aptitude to download the 'deb' package that you are trying to install. Ubuntu uses Debian package management system which means all the automatic installations use a deb package.

To add to sources.list:
```
gksudo gedit /etc/apt/sources.list
```
Then add 'deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main' (without the quotes) at the end of the file, and save.

Update apt (from terminal):
```
sudo apt-get update
```
Once you do that the package you want to install should be available in your package manager for installation.

---

