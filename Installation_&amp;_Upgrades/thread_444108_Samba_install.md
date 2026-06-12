---
title: "Samba install???"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by CeeBee7 on 2007-05-15
Hi guys... maybe 1 of u experts cud help pleeeeze.
I downloaded Ubuntu 7.04, and see that it has file sharing, also with option of sharing by IP address.
This would work for me, as I should be able to give only a certain (or range) IP/computer access to a folder, so then password is not needed. (or am I misinterpreting?)
Only crap is - I cant get it working  
When I go to System, Administration, Shared folders, a message pops up saying "Sharing services is not installed, need to install either.... Samba or NFS..."... so how can I install it? I choose 1 or both and click install.... few secs, icon spins... message back.
I found on the ubuntu guide, must enter : sudo apt-get install samba smbfs, but all I get is that "samba is not available.... replaced by samba-common", even tried : sudo apt-get install samba (without smbfs, which works on v5.04), but still no luck.
I have even downloaded another 7.04 image from another site, as well as the server edition, but all same messages.... going to shared folders keeps giving msg "Sharing servs not installed"
Am I to believe that samba file sharing is just not available on Ubuntu 7.04  
I'm sure this cud just be another case of the problem being between keyboard and chair  :-D , but cud anybody help with sum advise? or where can I download samba to install? thought file sharing one of the basic requirements for most users

---

### Post by renzokuken on 2007-05-15
its definately available, that message just means they have changed the name of the package.

```
sudo apt-get install samba-common
``` should work. if not open up synaptic package manager and just search for it. although i seem to remember the file sharing wizard installing it for you.

also note, samba is for sharing files between windows and *nix PCs, NFS is used to share files between *nix PCs only

---

### Post by CeeBee7 on 2007-05-15
cool thanx, tried install samba-common, says already there...
but I went to Add/remove progs, added everything I found with samba :-)
seemed to work, no longer getting "Sharing servs not installed" and can now share folders on LAN, BUT the IP / computername option at sharing seems to have disappeared... suppose I installed a different v of samba
now i'll just have to go figure out how to give access based on IP / computername who is trying to open shared folder.
At least I can now share, with password.

---

