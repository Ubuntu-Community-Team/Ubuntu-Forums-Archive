---
title: "Installation Issue"
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by gungaden on 2005-03-08
I am an Ubuntu and Linux newbie. I can navigate the various file directories and know the basic Linux prompt commands. I understand the basic structure and concept, but that is about it.
Hardware - i386, 900Mhz, 1 NIC, broadband, 40Meg HD, NVIDIA graphics, 384,000 RAM.
I installed Warty with partial success. Although most applications installed, I was not able to install OpenOffice which was a basic dependency of my Samba install. After following threads on the various forums, I decided to install Hoary to facilitate the OpenOffice installation. However, when it came to the point of updating and upgrading Hoary, I ran into similar problems.

I have included the upgrade process feedback, below. Please note the lines in red font. The following is the feedback on the upgrade process.

Is anyone willing to help me get OpenOffice installed?

If so, thanks in advance.


# apt-get update
Hit [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main Packages
Hit [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main Release
Hit [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/universe Packages
Hit [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/universe Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Release [102B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Release [108B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Release [97B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Release [104B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Release [110B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Release [99B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Release
Fetched 620B in 3s (198B/s)
Reading Package Lists... Done
# apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
openoffice.org: Depends: openoffice.org-bin (> 1.1.1+1.1.2rc3) but it is not installed
openoffice.org-debian-files: Depends: openoffice.org-bin (> 1.1.1+1.1.2rc3) but it is not installed
E: Unmet dependencies. Try using -f.

# apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
openoffice.org-bin
The following NEW packages will be installed:
openoffice.org-bin
0 upgraded, 1 newly installed, 0 to remove and 85 not upgraded.
8 not fully installed or removed.
Need to get 0B/43.9MB of archives.
After unpacking 130MB of additional disk space will be used.
Do you want to continue? [Y/n] y

Preconfiguring packages ...
(Reading database ... 61064 files and directories currently installed.)
Unpacking openoffice.org-bin (from .../openoffice.org-bin_1.1.2-2ubuntu6_i386.deb) ...
d[U]pkg: error processing /var/cache/apt/archives/openoffice.org-bin_1.1.2-2ubuntu6_i386.deb (--unpack):
corrupted filesystem tarfile - corrupted package archive: Success
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/openoffice.org-bin_1.1.2-2ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/U]

---

### Post by alastair on 2005-03-08
Not sure. If this is only a corrupted download, try removing the cached package and retrying :

sudo rm /var/cache/apt/archives/openoffice.org-bin_1.1.2-2ubuntu6_i386.deb

---

### Post by gungaden on 2005-03-09
Got it........much thanks !!!!!  :)

---

