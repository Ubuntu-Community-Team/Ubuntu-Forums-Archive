---
title: "How to get Cisco Packet Tracer 8.2.2 working on Ubuntu 24.04"
date: 2024-05-12
forum: Installation &amp; Upgrades
---

### Post by tijiva on 2024-05-12
Hi All,
        I was trying to install Cisco Packet Tracer 8.2.2 when I got the dependency package ibgl1-mesa-glx missing error and the package installation failed. This package was earlier part of Ubuntu 22.04 and 23.0, but was not available/ deprecated in the latest Ubuntu 24.04 version. Following steps helped me resolve the issue.

_**Download the respective packages:**_

CiscoPacketTracer822_amd64_signed.debp from [https://www.netacad.com/portal/resources/packet-tracer](https://www.netacad.com/portal/resources/packet-tracer)
ibgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.debp from [https://packages.ubuntu.com/search?keywords=libgl1-mesa-glx](https://packages.ubuntu.com/search?keywords=libgl1-mesa-glx)

_**Change the file permissions for installing the same:**_

user@user:~/Downloads$ ll
-rw-rw-rw-  1 user user 282817852 May 12 14:32  CiscoPacketTracer822_amd64_signed.deb*
-rw-rw-r--  1 user user      5584 May 12 15:27  libgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.deb

user@user:~/Downloads$ chmod 755 *
-rwxrw-rw-  1 user user 282817852 May 12 14:32  CiscoPacketTracer822_amd64_signed.deb*
-rwxrw-rw-  1 user user      5584 May 12 15:27  libgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.deb


_**Installing the dependency package:**_

user@user:~/Downloads$ sudo apt install ./libgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.deb
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'libgl1-mesa-glx' instead of './libgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.deb'
The following NEW packages will be installed:
  libgl1-mesa-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/5,584 B of archives.
After this operation, 74.8 kB of additional disk space will be used.
Get:1 /user/Downloads/libgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.deb libgl1-mesa-glx amd64 23.0.4-0ubuntu1~22.04.1 [5,584 B]
Selecting previously unselected package libgl1-mesa-glx:amd64.
(Reading database ... 171870 files and directories currently installed.)
Preparing to unpack .../libgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (23.0.4-0ubuntu1~22.04.1) ...
Setting up libgl1-mesa-glx:amd64 (23.0.4-0ubuntu1~22.04.1) ...

Installing the Cisco Packet Tracer 8.2.2 on Ubuntu 24.04 which will also install other dependent packages:

user@user:~/Downloads$ sudo apt install ./CiscoPacketTracer822_amd64_signed.deb
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'packettracer' instead of './CiscoPacketTracer822_amd64_signed.deb'
The following additional packages will be installed:
  dialog libpthread-stubs0-dev libxau-dev libxcb-xinerama0 libxcb-xinerama0-dev libxcb1-dev libxdmcp-dev x11proto-dev xorg-sgml-doctools
Suggested packages:
  libxcb-doc
The following NEW packages will be installed:
  dialog libpthread-stubs0-dev libxau-dev libxcb-xinerama0 libxcb-xinerama0-dev libxcb1-dev libxdmcp-dev packettracer x11proto-dev xorg-sgml-doctools
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,054 kB/284 MB of archives.
After this operation, 3,968 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y

Unpacking packettracer (8.2.2) ...
Setting up libpthread-stubs0-dev:amd64 (0.4-1build3) ...
Setting up libxcb-xinerama0:amd64 (1.15-1ubuntu2) ...
Setting up dialog (1.3-20240101-1) ...
Setting up xorg-sgml-doctools (1:1.11-1.1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.1) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for shared-mime-info (2.4-4) ...
Processing triggers for sgml-base (1.31) ...
Setting up x11proto-dev (2023.2-1) ...
Setting up libxau-dev:amd64 (1:1.0.9-1build6) ...
Setting up libxdmcp-dev:amd64 (1:1.1.3-0ubuntu6) ...
Setting up libxcb1-dev:amd64 (1.15-1ubuntu2) ...
Setting up libxcb-xinerama0-dev:amd64 (1.15-1ubuntu2) ...
Setting up packettracer (8.2.2) ...
gtk-update-icon-cache: No theme index file.

**and the Packet Tracer was installed successfully and working.**

Thank You

---

### Post by dhruvd22 on 2024-08-18
You're a god. Thankyou so much kind sir. I really appreciate this.

---

### Post by ai7ch on 2024-09-02
Thank you, this worked nicely ^_^

---

### Post by highlycaffeinated13 on 2024-10-05
Upgraded to 24.04.1 and couldn't get Packet Tracer to install because of libgl1-mesa-glx issues. Your thread fixed this! Thank you for sharing.

---

### Post by petregmd on 2024-10-19
The same solution applies to Ubuntu 23.10. I wrote about it here: [https://gulian.uk/how-to-install-cisco-packet-tracer-on-ubuntu-23-10-or-24-04/](https://gulian.uk/how-to-install-cisco-packet-tracer-on-ubuntu-23-10-or-24-04/)

---

