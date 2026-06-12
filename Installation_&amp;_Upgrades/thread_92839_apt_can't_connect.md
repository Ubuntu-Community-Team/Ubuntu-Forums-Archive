---
title: "apt can't connect"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by lemonshark on 2005-11-20
Hey everyone, I'm having problems with apt. I've already followed this guide [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php") but I am still getting the same problem. This is the output:

phil@phils-laptop:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138 ). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I am using a proxy to get to the net, but I have put it System>Preferences>Network Proxy

Has anyone got any ideas?

Cheers.

---

### Post by manicka on 2005-11-20
[http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)

---

### Post by lemonshark on 2005-11-20
Thanks for your reply manicka.

I typed export http_proxy="http://<my proxy>:<my port>" and it now works fine.

---

