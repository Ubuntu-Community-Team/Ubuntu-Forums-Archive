---
title: "dependency problems prevent configuration of teamviewer-host"
date: 2024-05-27
forum: Installation &amp; Upgrades
---

### Post by leejenon on 2024-05-27
Hi, 

Could I have some help with this Teamviewer installation please - 

```
[B]Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy[/B]

plex@Mini-PC:~/Downloads$ dir
teamviewer-host_15.53.6_amd64.deb
plex@Mini-PC:~/Downloads$ sudo dpkg -i teamviewer-host_15.53.6_amd64.deb
[sudo] password for plex: 
Selecting previously unselected package teamviewer-host.
(Reading database ... 206347 files and directories currently installed.)
Preparing to unpack teamviewer-host_15.53.6_amd64.deb ...
Unpacking teamviewer-host (15.53.6) ...
dpkg: dependency problems prevent configuration of teamviewer-host:
 teamviewer-host depends on libminizip1; however:
  Package libminizip1 is not installed.
 teamviewer-host depends on libxcb-xinerama0; however:
  Package libxcb-xinerama0 is not installed.

dpkg: error processing package teamviewer-host (--install):
 dependency problems - leaving unconfigured
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Errors were encountered while processing:
 teamviewer-host
plex@Mini-PC:~/Downloads$ 
```

Thanks,,
Lee

---

### Post by leejenon on 2024-05-27
```
plex@Mini-PC:~$ uname -a
Linux Mini-PC 6.5.0-142312122121-generic #0+mediatree+hauppauge~hwe-Ubuntu SMP PREEMPT_DYNAMIC Fri Dec 15 x86_64 x86_64 x86_64 GNU/Linux
plex@Mini-PC:~$ 

```

---

### Post by #&amp;thj^% on 2024-05-27
Would you  also include this:
```
sudo apt --fix-broken install
```
I take it this is a server set-up right?

---

### Post by leejenon on 2024-05-27
Thanks 1fallen, this produced this error 

```
E: Unable to locate package teamviewer-host_15.53.6_amd64.deb
```

Are there pre-installation tasks for Teamviewer re: your message?

Thanks, Lee

---

### Post by leejenon on 2024-05-27
I have just realised this file is an AMD not x86 install file. The Teamviewer x86 download is downloading an AMD install file not an x86 file. I have asked Teamviewer about this incorrect link.
Lee

---

### Post by #&amp;thj^% on 2024-05-27
Yes you would do it all in the same Directory your  teamviewer-host_15.53.6_amd64.deb is located.
```
cd Downloads
sudo dpkg - i  teamviewer-host_15.53.6_amd64.deb
##Followed by
sudo apt --fix-broken install
```

---

### Post by #&amp;thj^% on 2024-05-27
> **leejenon said:**
> I have just realised this file is an AMD not x86 install file. The Teamviewer x86 download is downloading an AMD install file not an x86 file. I have asked Teamviewer about this incorrect link.
Lee
That does not matter, please follow my above post.

---

### Post by #&amp;thj^% on 2024-05-27
Mine went almost the same:
```
 sudo dpkg -i '/home/me/teamviewer-host_amd64.deb' 
[sudo] password for me: 
Selecting previously unselected package teamviewer-host.
(Reading database ... 265873 files and directories currently installed.)
Preparing to unpack .../me/teamviewer-host_amd64.deb ...
Unpacking teamviewer-host (15.53.6) ...
dpkg: dependency problems prevent configuration of teamviewer-host:
 teamviewer-host depends on libminizip1; however:
  Package libminizip1 is not installed.

dpkg: error processing package teamviewer-host (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
Processing triggers for desktop-file-utils (0.27-2build1) ...
Processing triggers for dbus (1.14.10-4ubuntu4) ...
Processing triggers for hicolor-icon-theme (0.18-1) ...
Errors were encountered while processing:
 teamviewer-host
```
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> sudo apt -f install
Correcting dependencies... Done 
The following package was automatically installed and is no longer required:
  libjxl0.7
Use 'sudo apt autoremove' to remove it.

Installing dependencies:
  libminizip1t64

Summary:
  Upgrading: 0, Installing: 1, Removing: 0, Not Upgrading: 0
  1 not fully installed or removed.
  Download size: 22.2 kB
  Space needed: 105 kB / 446 GB available

Continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 libminizip1t64 amd64 1:1.3.dfsg-3.1ubuntu2 [22.2 kB]
Fetched 22.2 kB in 1s (24.0 kB/s)                   
Selecting previously unselected package libminizip1t64:amd64.
(Reading database ... 266788 files and directories currently installed.)
Preparing to unpack .../libminizip1t64_1%3a1.3.dfsg-3.1ubuntu2_amd64.deb ...
Unpacking libminizip1t64:amd64 (1:1.3.dfsg-3.1ubuntu2) ...
Setting up libminizip1t64:amd64 (1:1.3.dfsg-3.1ubuntu2) ...
Setting up teamviewer-host (15.53.6) ...
gpg: directory '/root/.gnupg' created
gpg: keybox '/root/.gnupg/pubring.kbx' created
Processing triggers for libc-bin (2.39-0ubuntu8.1) ...
```
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> teamviewer

Init...
CheckCPU: SSE2 support: yes
Checking setup...
Launching TeamViewer ...
Launching TeamViewer GUI ...

```
```
 apt policy teamviewer-host
teamviewer-host:
  Installed: 15.53.6
  Candidate: 15.53.6
  Version table:
 *** 15.53.6 100
        100 /var/lib/dpkg/status

```

---

### Post by leejenon on 2024-05-27
> **1fallen said:**
> Yes you would do it all in the same Directory your  teamviewer-host_15.53.6_amd64.deb is located.
```
cd Downloads
sudo dpkg - i  teamviewer-host_15.53.6_amd64.deb
##Followed by
sudo apt --fix-broken install
```

THANK YOU - this worked

---

### Post by leejenon on 2024-05-27
1fallen's codes worked for me.

---

### Post by #&amp;thj^% on 2024-05-27
> **leejenon said:**
> THANK YOU - this worked

Your Welcome.

---

