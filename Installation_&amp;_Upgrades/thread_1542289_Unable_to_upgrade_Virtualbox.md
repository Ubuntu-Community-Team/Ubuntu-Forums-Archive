---
title: "Unable to upgrade Virtualbox"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by caifa on 2010-07-30
Hi all!
I'm trying to upgrade Virtualbox but I get the following error. What can I do?

I use Ubuntu Release 10.04 with Linux 2.6.32-24 generic


[IMG]http://img695.imageshack.us/img695/1310/screenshotgdebigtk.png[/IMG]

---

### Post by ptn107 on 2010-07-30
Check /var/log/vbox-install.log

Looks to me like you should have removed the older version of VB before installing the new one.  I have not tried to upgrade 3.2.4 to 3.2.6, but I'm sure it wouldn't work flawlessly if I tried.  I hope your not running a custom kernel or anything besides the default 2.6.32-24-generic.

I downloaded and installed the 64-bit version from [_here_]("http://download.virtualbox.org/virtualbox/3.2.6/virtualbox-3.2_3.2.6-63112~Ubuntu~lucid_amd64.deb").

I downloaded the virtualbox-3.2_3.2.6-63112~Ubuntu~lucid_amd64.deb to /home/phil/Downloads/ so at the terminal I did:

```
cd /home/phil/Downloads/
sudo aptitude install libqt4-network libqt4-opengl libqtcore4 libqtgui4 -y
sudo dpkg -i virtualbox-3.2_3.2.6-63112~Ubuntu~lucid_amd64.deb
sudo usermod -a -G vboxusers phil
```

Then I logged out and back in and it works fine.

To reiterate I would completely remove the old version first.  It will still keep your settings and vm's.

---

### Post by caifa on 2010-08-02
Thanks for the answer!

I'm not running a custom service, and I didn't remove the previous version of virtualbox before upgrading it.

I've tried to install it manually but I receive the same error when I type:

*sudo aptitude install libqt4-network libqt4-opengl libqtcore4 libqtgui4 -y*

If I skip this step and I run directly

*dpkg -i virtualbox-3.2_3.2.6-63112~Ubuntu~lucid_amd64.deb*

the update runs correctly.

Should I worry about *libqt4*?

---

### Post by moonport on 2010-08-02
You can check if Package Manager is working fine:

sudo apt-get clean all
sudo apt-get update
sudo apt-get install htop

---

### Post by caifa on 2010-08-10
There is nothing to do, I tried your commands and I tried to install htop, but the installation process always fails at this point: "Running depmod".
I noticed that I have the same problem whenever I try to install something with Synaptic: the programs seem to be installed properly, but I always get this error at the end of the installation.


# sudo apt-get install htop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 66.1kB of archives.
After this operation, 217kB of additional disk space will be used.
Get:1 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid/universe htop 0.8.3-1ubuntu1 [66.1kB]
Fetched 66.1kB in 0s (137kB/s)
Selecting previously deselected package htop.
(Reading database ... 195642 files and directories currently installed.)
Unpacking htop (from .../htop_0.8.3-1ubuntu1_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up htop (0.8.3-1ubuntu1) ...

Errors were encountered while processing:
 linux-image-2.6.32-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

