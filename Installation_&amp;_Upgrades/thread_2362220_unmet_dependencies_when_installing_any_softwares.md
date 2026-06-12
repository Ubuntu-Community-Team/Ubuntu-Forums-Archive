---
title: "unmet dependencies when installing any softwares"
date: 2017-05-25
forum: Installation &amp; Upgrades
---

### Post by manuelmelvin on 2017-05-25
I am working with ROS (Robotics Operating System) with Ubuntu 14.04. I have installed ROS and Aria on my system and now when I am trying to install any softwares I am getting the below message. For example I was trying to install systemback for creating a restore point for my ubuntu.Then I am getting the below message.

```

The following packages have unmet dependencies:
 libaria-dev : Depends: libaria2 (= 2.8.0+repack-1ubuntu1) but it is not going to be installed
 systemback : Depends: libsystemback (= 1.8.402~ubuntu14.04.1) but it is not going to be installed
              Depends: casper but it is not going to be installed or
                       live-boot but it is not going to be installed
              Depends: squashfs-tools but it is not going to be installed
              Depends: systemback-efiboot-amd64 (= 1.8.402~ubuntu14.04.1) but it is not going to be installed
              Depends: systemback-scheduler (= 1.8.402~ubuntu14.04.1) but it is not going to be installed
              Recommends: grub-efi-amd64-bin
              Recommends: lupin-casper but it is not going to be installed
              Recommends: systemback-cli (= 1.8.402~ubuntu14.04.1) but it is not going to be installed
              Recommends: systemback-locales (= 1.8.402~ubuntu14.04.1) but it is not going to be installed
```

Please help me to come out of this issue.

I tried " sudo apt-get -f install" and
 i got the below message
 
```

(Reading database ... 245789 files and directories currently installed.)
Preparing to unpack .../libaria2_2.8.0+repack-1ubuntu1_amd64.deb ...
Unpacking libaria2:amd64 (2.8.0+repack-1ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libaria2_2.8.0+repack-1ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/etc/Aria', which is also in package libaria 2.9.1+ubuntu12
Errors were encountered while processing:
 /var/cache/apt/archives/libaria2_2.8.0+repack-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks in Advance

---

### Post by oldfred on 2017-05-25
Do not know robots.

Is real error from libaria or systemback?

But did you install libaria from Ubuntu repository or from a ppa?

Repository shows this:
libaria (2.8.0+repack-1ubuntu2)

Web site shows this:
[http://robots.mobilerobots.com/wiki/ARIA](http://robots.mobilerobots.com/wiki/ARIA)
 [ARIA 2.9.1 - Ubuntu 16.04 (xenial) or later, amd 64-bit architecture]("http://robots.mobilerobots.com/ARIA/download/current/libaria_2.9.1+ubuntu16_amd64.deb") (libaria_2.9.1+ubuntu16_amd64.deb)  
[LIST]
[*] Open file to install with Ubuntu Software Center or use dpkg -i
[/LIST]

---

