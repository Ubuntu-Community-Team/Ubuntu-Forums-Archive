---
title: "Error with wget during installation sublime-text"
date: 2019-06-06
forum: Installation &amp; Upgrades
---

### Post by sed_faster on 2019-06-06
Hello folks,

I am trying install sublime-text through terminal on my Lubuntu as this article refers to: [https://www.sublimetext.com/docs/3/linux_repositories.html](https://www.sublimetext.com/docs/3/linux_repositories.html)

My system is:
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
$ uname -a
Linux user 4.18.0-18-generic #19~18.04.1-Ubuntu SMP Fri Apr 5 10:22:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

I am following this steps:
```

$ wget -q0 - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
wget: invalid option -- '0'
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
gpg: no valid OpenPGP data found.

$ sudo apt-get install apt-transport-https
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apt-transport-https
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 1692 B of archives.
After this operation, 153 kB of additional disk space will be used.
Get:1 http://pt.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 apt-transport-https all 1.6.11 [1692 B]
Fetched 1692 B in 0s (14,7 kB/s)             
Selecting previously unselected package apt-transport-https.
(Reading database ... 165983 files and directories currently installed.)
Preparing to unpack .../apt-transport-https_1.6.11_all.deb ...
Unpacking apt-transport-https (1.6.11) ...
Setting up apt-transport-https (1.6.11) ...


$ echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
deb https://download.sublimetext.com/ apt/stable/

$ sudo apt-get update
Hit:1 http://pt.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://pt.archive.ubuntu.com/ubuntu bionic-updates InRelease                                                                                                                                                
Hit:3 http://pt.archive.ubuntu.com/ubuntu bionic-backports InRelease                                                                                                                                              
Hit:4 http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu bionic InRelease                                                                                                                                 
Hit:5 http://security.ubuntu.com/ubuntu bionic-security InRelease                                                                                                                                      
Hit:6 https://typora.io/linux ./ InRelease                                                                                       
Get:7 https://download.sublimetext.com apt/stable/ InRelease [2562 B]                                      
Err:7 https://download.sublimetext.com apt/stable/ InRelease  
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F57D4F59BD3DF454
Reading package lists... Done
W: GPG error: https://download.sublimetext.com apt/stable/ InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F57D4F59BD3DF454
E: The repository 'https://download.sublimetext.com apt/stable/ InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

$ sudo apt-get install sublime-text
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sublime-text
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/9670 B of archives.
After this operation, 51,2 kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 165987 files and directories currently installed.)
Preparing to unpack .../sublime-text_2.0.2-1~webupd8~3_all.deb ...
Downloading...
--2019-06-06 18:41:41--  https://c758482.ssl.cf2.rackcdn.com/Sublime%20Text%202.0.2%20x64.tar.bz2
Resolving c758482.ssl.cf2.rackcdn.com (c758482.ssl.cf2.rackcdn.com)... 95.100.149.23
Connecting to c758482.ssl.cf2.rackcdn.com (c758482.ssl.cf2.rackcdn.com)|95.100.149.23|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
2019-06-06 18:41:42 ERROR 404: Not Found.

download failed
Download done.
Removing outdated cached downloads...
sha256sum mismatch Sublime Text 2.0.2 x64.tar.bz2
Sublime Text is NOT installed.
dpkg: error processing archive /var/cache/apt/archives/sublime-text_2.0.2-1~webupd8~3_all.deb (--unpack):
 new sublime-text package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sublime-text_2.0.2-1~webupd8~3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The problems occurs when I runs the command "wget". But what am I doing wrong?
Thanks

---

### Post by Holger_Gehrke on 2019-06-06
You misread and mistyped the options to the wget-command. That needs to be an upper case 'o', not a zero.

Holger

---

