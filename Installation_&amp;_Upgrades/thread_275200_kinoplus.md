---
title: "kinoplus"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by Sambie on 2006-10-11
Is anybody else having a diffcult problem installing Kinoplus?


brittany@brittany-desktop:~$ sudo apt-get install kinoplus
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  kinoplus
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 80.7kB of archives.
After unpacking 287kB of additional disk space will be used.
Get:1 [http://bs.archive.ubuntu.com](http://bs.archive.ubuntu.com) dapper/universe kinoplus 0.3.5-1.1build1 [80.7kB]
Fetched 80.7kB in 0s (80.7kB/s)
[B]X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/B]
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 1 during global destruction.
Selecting previously deselected package kinoplus.
(Reading database ... 86454 files and directories currently installed.)
Unpacking kinoplus (from .../kinoplus_0.3.5-1.1build1_i386.deb) ...
Setting up kinoplus (0.3.5-1.1build1) ...
brittany@brittany-desktop:~$ sudo apt-get install kino-timfx
Reading package lists... Done
Building dependency tree... Done
[B]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:[/B]

The following packages have unmet dependencies:
  kino-timfx: Depends: kino (>= 0.7) but it is not going to be installed
E: Broken packages
brittany@brittany-desktop:~$ sudo apt-get install kino-dvtitler
Reading package lists... Done
Building dependency tree... Done
[B]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:
[/B]
The following packages have unmet dependencies:
  kino-dvtitler: Depends: kino (>= 0.7) but it is not going to be installed
E: Broken packages
brittany@brittany-desktop:~$

---

### Post by Predius on 2006-10-11
Try the answer offered in [this post.]("http://ubuntuforums.org/showpost.php?p=1264009&postcount=3")

---

