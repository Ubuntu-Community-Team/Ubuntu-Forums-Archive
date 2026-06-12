---
title: "problems isntalling sun, java, xine..."
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2006-08-26
I just got connected to the internet, and am following the handy setup guide [here](http://ubuntuguide.org/wiki/Dapper#How_to_manually_update_Ubuntu).
However, I'm stuck trying to install java. Any time I try to apt-get something now, I ahve the following message:
```
The following packages have unmet dependencies:
  kaffeine: Depends: libxine-main1 (>= 1.1.1) but it is not going to be installed
  kaffeine-xine: Depends: libxine-main1 (>= 1.1.1) but it is not going to be installed
  libxine-extracodecs: Depends: libxine-main1 but it is not going to be installed
  sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Running apt-get -f install just starts an installation process which fails and suggests I run the same command again.

Finally, this (long) message appears whenever I run apt-get, and I've no idea what it's trying to tell me
```


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
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 3 during global destruction.
Preconfiguring packages ...
(Reading database ... 95798 files and directories currently installed.)
Unpacking libxine-main1 (from .../libxine-main1_1.1.1+ubuntu2-7.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libxine-main1_1.1.1+ubuntu2-7.2_i386.deb (--unpack):
 trying to overwrite `/usr/share/xine/libxine1/fonts/cetus-16.xinefont.gz', which is also in package xine-lib
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
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
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-06-1_i386.deb) ...
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
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libxine-main1_1.1.1+ubuntu2-7.2_i386.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by pickarooney on 2006-08-26
Oops, the java error messages were because I wasn't scrolling all the way down the installer window and tickign the box, sorry!
The main question though is still what the Failed to open device messages are all about.

---

### Post by elettronicha on 2006-08-26
Did you enable the necessary repos?

---

### Post by pickarooney on 2006-08-26
I enabled the repositories as given in the HOWTO. I don't think the BadDevice messages are repository-related though. I seem to have a conflict with xinelib and libxine too.

---

