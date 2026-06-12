---
title: "mdadm problems"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by windsok on 2010-01-11
Hi All,

I am planning on setting up a 4x1TB RAID5 with mdadm under Ubuntu 9.10.

I tried installing mdadm using "sudo apt-get install mdadm", all worked fine except for the following error: 

```
Generating array device nodes... /var/lib/dpkg/info/mdadm.postinst: 170: /dev/MAKEDEV: not found
failed.
```

The end result is the /dev/md0 device has not been created, as can be seen here:

```
windsok@beer:~$ mdadm --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
```

After googling, I found the following bug which describes the issue: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/368986](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/368986)

However it was reported way back in April 2009, and it does not look like it will be fixed any time soon, so I was wondering if anyone knows a workaround for this bug, to get me up and running?

Thanks!

---

### Post by windsok on 2010-01-11
I tried to manually create the devices and get the following:

```
windsok@beer:/dev$ sudo MAKEDEV md
.udevdb or .udev presence implies active udev.  Aborting MAKEDEV invocation.
```

---

### Post by barnex on 2010-01-11
I don't know if anything is broken for the moment, but a few months ago I could still set up raid 5 on 9.10 without problems. Here's the tutorial I followed, hope it helps!

[http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/comment-page-2/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/comment-page-2/)

For completeness: I had my system installed on a separate drive and used RAID5 for 4 additional storage drives.

---

### Post by windsok on 2010-01-12
hi barnex,

Are you running the ubuntu server edition?

The only thing I can think of is that everything is fine with the server edition as mdadm comes included?

I am running the desktop edition, which does not include mdadm, so i have to install it with apt-get, which is where i come across the problems, as the apt package appears to be broken

---

### Post by windsok on 2010-01-12
okay, I just did a brand new install of 9.10 64bit Server, fully patched and updated.


Looks like mdadm is not included by default in server installation either:

```

windsok@beer:~$ sudo mdadm
sudo: mdadm: command not found
windsok@beer:~$ mdadm
The program 'mdadm' is currently not installed.  You can install it by typing:
sudo apt-get install mdadm
mdadm: command not found

```I tried again to install mdadm:

```

windsok@beer:~$ sudo apt-get install mdadm
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-server
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  postfix ssl-cert
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin resolvconf postfix-cdb mail-reader
The following NEW packages will be installed:
  mdadm postfix ssl-cert
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,630kB of archives.
After this operation, 4,305kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com karmic/main mdadm 2.6.7.1-1ubuntu13 [239kB]
Get:2 http://au.archive.ubuntu.com karmic/main ssl-cert 1.0.23ubuntu2 [10.9kB]
Get:3 http://au.archive.ubuntu.com karmic/main postfix 2.6.5-3 [1,380kB]
Fetched 1,630kB in 8s (188kB/s)
Preconfiguring packages ...
Selecting previously deselected package mdadm.
(Reading database ... 61592 files and directories currently installed.)
Unpacking mdadm (from .../mdadm_2.6.7.1-1ubuntu13_amd64.deb) ...
Selecting previously deselected package ssl-cert.
Unpacking ssl-cert (from .../ssl-cert_1.0.23ubuntu2_all.deb) ...
Selecting previously deselected package postfix.
Unpacking postfix (from .../postfix_2.6.5-3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up mdadm (2.6.7.1-1ubuntu13) ...
[COLOR=DarkOrchid]Generating array device nodes... /var/lib/dpkg/info/mdadm.postinst: 170: /dev/MAKEDEV: not found
failed.[/COLOR]
Generating mdadm.conf... done.
 Removing any system startup links for /etc/init.d/mdadm-raid ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: mdadm start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (S)
update-rc.d: warning: mdadm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
 * Starting MD monitoring service mdadm --monitor                                                                 [ OK ]

Setting up ssl-cert (1.0.23ubuntu2) ...

Setting up postfix (2.6.5-3) ...
Adding group `postfix' (GID 114) ...
Done.
Adding system user `postfix' (UID 104) ...
Adding new user `postfix' (UID 104) with group `postfix' ...
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (GID 115) ...
Done.
/etc/aliases does not exist, creating it.

Postfix was not set up.  Start with
  cp /usr/share/postfix/main.cf.debian /etc/postfix/main.cf
.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.


Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-server
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
windsok@beer:~$

```Note the highlighted text, I am getting the same error, and the md devices are not created in /dev

Can anyone help me here? I am doing something totally wrong, or is mdadm just broken in ubuntu?

EDIT- given I cant find many other people encountering issues with this, I have to assume that when creating a raid with mdadm, that it will be able to generate a new md device itself.

This section of the link barnex posted suggests this should be the case:

> 
Upon pressing return, your RAID device (md0) will be created, if you get the following error (as I did with a fresh install of Edgy-Eft):
 [INDENT]mdadm: error opening /dev/md0: No such file or directory
[/INDENT] Then you need to add the parameter --auto=md to the end of your mdadm create raid command.


---

