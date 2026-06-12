---
title: "Lucid Lynx - Can't see all Samba shares"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mockingbird on 2010-03-28
Hi,

I have a Kubuntu Lucid Lynx install and I can only see the files on one of the Windows machines on my network, and when I try to access files on it it asks for a password when it shouldn't.

I so far tried:
sudo apt-get install samba
sudo apt-get install smbfs

That didn't help much, though it did install a few packages:
```
~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,819kB of archives.
After this operation, 18.4MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main samba 2:3.4.7~dfsg-1ubuntu1 [6,819kB]
Fetched 6,819kB in 7s (888kB/s)                                                                                  
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 88304 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.4.7~dfsg-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up samba (2:3.4.7~dfsg-1ubuntu1) ...
Generating /etc/default/samba...
Importing account for nobody...ok
Importing account for moishe...ok
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
smbd start/running, process 3169
nmbd start/running, process 3175

~$ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  keyutils
The following NEW packages will be installed:
  keyutils smbfs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,054kB of archives.
After this operation, 5,861kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main keyutils 1.2-12 [28.2kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/main smbfs 2:3.4.7~dfsg-1ubuntu1 [2,026kB]
Fetched 2,054kB in 2s (796kB/s)  
Selecting previously deselected package keyutils.
(Reading database ... 88372 files and directories currently installed.)
Unpacking keyutils (from .../keyutils_1.2-12_amd64.deb) ...
Selecting previously deselected package smbfs.
Unpacking smbfs (from .../smbfs_2%3a3.4.7~dfsg-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up keyutils (1.2-12) ...
Setting up smbfs (2:3.4.7~dfsg-1ubuntu1) ...

```

---

### Post by mockingbird on 2010-03-28
Now I rebooted and I'm getting this:

"Unable to find any workgroups in your local network.  This might be caused by an enabled firewall."

```
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

---

### Post by mockingbird on 2010-03-28
Ok that post was premature it took some time for the browser to kick in but still I can't see the files in the shares.

---

### Post by mockingbird on 2010-03-28
Anybody?

I had no problems with Windows shares on Debian Lenny.

---

### Post by stlsaint on 2010-03-28
That command to view iptables rules only shows that you do not have any rules configured. That is the default output of unconfigured iptables. Second you are wanting to setup samba?
See here for help: [Samba]("https://help.ubuntu.com/community/SettingUpSamba")

Its long but it goes in depth.

---

### Post by mockingbird on 2010-03-28
Ok I solved the problem.

First thing I dead, as [prescribed per this thread](http://ubuntuforums.org/showthread.php?t=1169149) was to play around with a few settings in smb.conf

you have to change the workgroup name and the name resolve order that seems to have done it.

---

### Post by mockingbird on 2010-03-28
but now I am having another problem that it is asking me for user credentials to access unprotected shares.

---

### Post by mockingbird on 2010-03-28
Ok the solution was to type smbpasswd -a *username*

---

### Post by mockingbird on 2010-03-28
Hmmmm, no I thought it did but some computers are not allowing me access.  I can get into the share but I can't read the file.

---

### Post by mockingbird on 2010-03-28
I have a serious suspicion that this is a problem with Dolphin because now when I right click it and try to play it with VLC (video file) it won't let me.  But then if I copy the file to my harddrive and then stop it in the middle, and THEN try to stream it through Samba, it plays fine.

I never had this problem with Konqueror.

I think I'll submit a bug report.

---

