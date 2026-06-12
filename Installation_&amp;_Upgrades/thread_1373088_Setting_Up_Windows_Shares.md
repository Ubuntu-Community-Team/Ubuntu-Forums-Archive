---
title: "Setting Up Windows Shares"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by PatK100 on 2010-01-05
Hello All,
 
Fairly new to Karmic - wanting to setup some Windows Shares on an external Harddrive.
 
I understand that I need to install Samba to do this but when I try to install it I get the following message:-
 
pat@CCBC-13112:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
samba-common-bin smbclient samba-common
E: Package samba has no installation candidate
 
Can anyone help please
 
Thanks
 
 
Pat

---

### Post by labinnsw on 2010-01-12
Have you tried Synaptic to install samba rather than Apt? See if that works.

---

### Post by Martyn Thompson on 2010-01-12
Hi - type sudo tasksel and asterisk Samba File Server (or whatever it's called) by using your space bar. 

Let us know how you get on.

---

