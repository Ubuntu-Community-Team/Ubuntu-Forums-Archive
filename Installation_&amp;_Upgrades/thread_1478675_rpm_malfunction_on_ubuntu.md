---
title: "rpm malfunction on ubuntu"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by rahulchandrak on 2010-05-10
Hi All, today I experienced an weird functioning of rpm on ubuntu. In general, to install any software on ubuntu9.10 we use "apt-get" command,but, the problem with it is that it will install the latest version of that sofware present in the repository. For installing the older versions of the particular software, "apt-get" is not useful. Today I wanted to install the java 1.4 version on my box. I downloaded the rpm.bin file from the oracle Sun site. let us assume that the name of the downloaded file is java1.4.rpm.bin . To convert the file into an rpm format I gave the following command

./java1.4.rpm.bin

This command showed a list of terms and conditions and after accepting, it generated the rpm file java1.4.rpm. Then I gave the command 

rpm -ivh java1.4.rpm
After executing this command, I expected java to be installed but it gave me an error like "rpm: please use alien to install rpm packages on Debian, if you are really sure use --force-debian switch. See README.Debian for more details."


When I do the following steps same-to-same on redhat and when I gave the command
./java1.4.rpm.bin, java got installed automatically and environmental variable was created. I do not know why ubuntu is not supporting the rpm packages. If we want to use "apt-get" then we have to see the alternative way of installing the older versions of any software.

---

### Post by dino99 on 2010-05-10
you may use the ubuntu repositories, search into archives

---

### Post by Dayofswords on 2010-05-10
ubuntu is debian based, and as such, uses .deb packages

read this on how to instal .rpm packages

[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

> Alien converts an RPM package file into a Debian package file or Alien can install an RPM file directly. This is not the recommended way to install software packages in Ubuntu. If at all possible, install packages from Ubuntu's repositories using Add/Remove, apt-get, or the Synaptic Package Manager. Package dependency conflicts may occur when attempting to install RPM packages. The Synaptic Package Manager may be able to fix or remove any broken packages.

---

