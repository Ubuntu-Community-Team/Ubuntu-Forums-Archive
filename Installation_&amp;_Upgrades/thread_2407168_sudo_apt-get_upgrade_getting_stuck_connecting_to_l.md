---
title: "sudo apt-get upgrade getting stuck connecting to login.mathworks.com"
date: 2018-11-30
forum: Installation &amp; Upgrades
---

### Post by davidsoltysik on 2018-11-30
Hi,

I'm trying to install R on my Ubuntu 16.04.5 LTS Linux machine (xenial). When I run sudo apt-get upgrade, it gets stuck trying to connect to login.mathworks.com and I don't know why.

>  sudo apt-get upgrade

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnome-software gnome-software-common libpam-systemd libsmbclient libsystemd0 libudev1 libunity-control-center1 libwbclient0
  python3-update-manager python3-urllib3 samba-libs systemd systemd-sysv ubuntu-software udev unity-control-center
  unity-control-center-faces update-manager update-manager-core
19 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.8 MB of archives.
After this operation, 46.1 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
0% [Connecting to login.mathworks.com (52.73.71.114)
```
 
-----

I don't know why it's trying to connect to login.mathworks.com. I have MATLAB installed, but I did that using the MATLAB installer, not apt-get. 

I don't know if this is an issue with my machine, my network, or Mathworks. Are there any ideas on how to troubleshoot this problem?

Thanks in advance.

David

---

### Post by oldos2er on 2018-12-02
login.mathworks.com doesn't resolve for me either. I would try removing it from your sources.

---

### Post by CatKiller on 2018-12-02
> **davidsoltysik said:**
> I don't know why it's trying to connect to login.mathworks.com. I have MATLAB installed, but I did that using the MATLAB installer, not apt-get. 

Some installers add repositories so that you can keep getting updates through the package manager. Chrome does that, as does Steam. I guess MATLAB does, too.

It'll either be a .list file in /etc/apt/sources.list.d or an entry in /etc/apt/sources.list. Just delete them and then run update again.

---

