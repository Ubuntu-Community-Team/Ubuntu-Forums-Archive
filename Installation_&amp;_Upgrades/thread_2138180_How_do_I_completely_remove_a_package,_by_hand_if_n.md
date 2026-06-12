---
title: "How do I completely remove a package, by hand if need be?"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by jonathanhayward on 2013-04-23
I have a libssl-dev package installed, possibly because I am not sure if I bypassed the package manager, and it's visible from the package manager but won't go away.

root@li393-189:/home/jonathan/python-amazon-product-api-0.2.5# aptitude purge l
ibssl-dev
The following packages will be REMOVED:  
  libssl-dev{p} 
The following partially installed packages will be configured:
  apt 
0 packages upgraded, 0 newly installed, 1 to remove and 84 not upgraded.
Need to get 0 B of archives. After unpacking 4,929 kB will be freed.
Do you want to continue? [Y/n/?] Y
Setting up apt (0.8.16~exp12ubuntu10.10) ...
gpg: Invalid option "--primary-keyring"
gpg: [don't know]: invalid packet (ctb=03)
gpg: read_keyblock: read error: invalid packet
gpg: enum_keyblocks(read) failed: invalid keyring
gpg: WARNING: nothing exported
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up apt (0.8.16~exp12ubuntu10.10) ...
gpg: Invalid option "--primary-keyring"
gpg: [don't know]: invalid packet (ctb=03)
gpg: read_keyblock: read error: invalid packet
gpg: enum_keyblocks(read) failed: invalid keyring
gpg: WARNING: nothing exported
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 apt
                                         
root@li393-189:/home/jonathan/python-amazon-product-api-0.2.5# 

I want the presently installed libssl-dev to be replaced with a fresh package installation. No configuration of aptitude I've seen yet will remove it.

How can I remove the existing package to be able to reinstall it from scratch?

--EDIT--

I had tried with aptitude rather than just apt-get, but apt-get gives what looks to me like an apparent equivalent:

root@li393-189:/home/jonathan/python-amazon-product-api-0.2.5# apt-get remove l
ibssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libssl-dev
0 upgraded, 0 newly installed, 1 to remove and 84 not upgraded.
1 not fully installed or removed.
After this operation, 4,929 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Setting up apt (0.8.16~exp12ubuntu10.10) ...
gpg: gpg: Invalid option "--primary-keyring"
[don't know]: invalid packet (ctb=03)
gpg: read_keyblock: read error: invalid packet
gpg: enum_keyblocks(read) failed: invalid keyring
gpg: WARNING: nothing exported
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@li393-189:/home/jonathan/python-amazon-product-api-0.2.5# 

--EDIT--

Here is the output to the suggested sh -x /usr/bin/apt-key update.

Thanks,

root@li393-189:~# sh -x /usr/bin/apt-key update
+ set -e
+ unset GREP_OPTIONS
+ mktemp
+ SECRETKEYRING=/tmp/tmp.yKRn2OqlH3
+ trap rm -f '/tmp/tmp.yKRn2OqlH3' 0 HUP INT QUIT ILL ABRT FPE SEGV PIPE TERM
+ GPG_CMD=gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.yKRn2OqlH3
+ id -u
+ [ 0 -eq 0 ]
+ GPG_CMD=gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.yKRn2OqlH3 --trustdb-name /etc/apt/trustdb.gpg
+ GPG=gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.yKRn2OqlH3 --trustdb-name /etc/apt/trustdb.gpg
+ MASTER_KEYRING=/usr/share/keyrings/ubuntu-master-keyring.gpg
+ ARCHIVE_KEYRING=/usr/share/keyrings/ubuntu-archive-keyring.gpg
+ REMOVED_KEYS=/usr/share/keyrings/ubuntu-archive-removed-keys.gpg
+ ARCHIVE_KEYRING_URI=http://archive.ubuntu.com/ubuntu/project/ubuntu-archive-keyring.gpg
+ TMP_KEYRING=/var/lib/apt/keyrings/maybe-import-keyring.gpg
+ [ update = --keyring ]
+ TRUSTEDFILE=/etc/apt/trusted.gpg
+ apt-config shell TRUSTEDFILE Apt::GPGV::TrustedKeyring
+ eval
+ apt-config shell TRUSTEDFILE Dir::Etc::Trusted/f
+ eval TRUSTEDFILE='/etc/apt/trusted.gpg'
+ TRUSTEDFILE=/etc/apt/trusted.gpg
+ [ -r /etc/apt/trusted.gpg ]
+ GPG=gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.yKRn2OqlH3 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg
+ GPG=gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.yKRn2OqlH3 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg
+ TRUSTEDPARTS=/etc/apt/trusted.gpg.d
+ apt-config shell TRUSTEDPARTS Dir::Etc::TrustedParts/d
+ eval TRUSTEDPARTS='/etc/apt/trusted.gpg.d/'
+ TRUSTEDPARTS=/etc/apt/trusted.gpg.d/
+ [ -d /etc/apt/trusted.gpg.d/ ]
+ run-parts --list /etc/apt/trusted.gpg.d/ --regex ^.*\.gpg$
+ command=update
+ [ -z update ]
+ shift
+ [ update != help ]
+ which gpg
+ update
+ [ ! -f /usr/share/keyrings/ubuntu-archive-keyring.gpg ]
+ requires_root
+ id -u
+ [ 0 -ne 0 ]
+ gpg --ignore-time-conflict --no-options+  --no-default-keyring --secret-keyring /tmp/tmp.yKRn2OqlH3gpg --trustdb-name /etc/apt/trustdb.gpg --ignore-time-conflict --no-options --no-default-keyring --quiet --batch --secret-keyring /tmp/tmp.yKRn2OqlH3 --keyring --trustdb-name /etc/apt/trustdb.gpg /usr/share/keyrings/ubuntu-archive-keyring.gpg --keyring /etc/apt/trusted.gpg --export --primary-keyring /etc/apt/trusted.gpg
 --import
gpg: Invalid option "--primary-keyring"
gpg: [don't know]: invalid packet (ctb=03)
gpg: read_keyblock: read error: invalid packet
gpg: enum_keyblocks(read) failed: invalid keyring
gpg: WARNING: nothing exported
+ rm -f /tmp/tmp.yKRn2OqlH3

---

### Post by slickymaster on 2013-04-23
[How to completely remove or uninstall a package]("http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-completely-uninstallremove-a-packagesoftwareprogram")

---

### Post by diesch on 2013-04-23
Your version of GPG is too old for your version of APT (or apt-key, at least).

What version of Ubuntu are you using?
What's do you get if you run
 ```
apt-get --version
gpg --version
```

---

### Post by jonathanhayward on 2013-04-23
I explored that, but the list of packages included such things as Apache that looked like they would cause mayhem if removed.

What should I do from there?

---

### Post by ibjsb4 on 2013-04-23
10.10 reached end of life a year ago.  This may help.

[https://help.ubuntu.com/community/EOLUpgrades#Requirements](https://help.ubuntu.com/community/EOLUpgrades#Requirements)

---

### Post by jonathanhayward on 2013-04-23
> **diesch said:**
> Your version of GPG is too old for your version of APT (or apt-key, at least).

What version of Ubuntu are you using?
What's do you get if you run
 ```
apt-get --version
gpg --version
```

```
root@li393-189:/etc/apt# apt-get --version
apt 0.8.16~exp12ubuntu10.10 for i386 compiled on Mar 13 2013 21:23:56
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 Pkg:  Debian APT solver interface (Priority -1000)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file
 Idx: EDSP scenario file
```

/etc/motd lists 12.04 as the version of Ubuntu.

---

### Post by oldos2er on 2013-04-23
> Setting up apt (0.8.16~exp12ubuntu10.10)

Is there some particular reason you're using the Ubuntu Security Team PPA? I'd consider filing a bug against the package apt_0.8.16~exp12ubuntu10.10_i386.deb

---

### Post by diesch on 2013-04-23
> **jonathanhayward said:**
> ```
root@li393-189:/etc/apt# apt-get --version
apt 0.8.16~exp12ubuntu10.10 for i386 compiled on Mar 13 2013 21:23:56

```

/etc/motd lists 12.04 as the version of Ubuntu.

Ok, that matches your version of APT. What does
```
 apt-cache policy gnupg
```
print?

---

### Post by diesch on 2013-04-23
> **oldos2er said:**
> Is there some particular reason you're using the Ubuntu Security Team PPA?

It's the current version from precise-updates, see [http://packages.ubuntu.com/precise-updates/apt](http://packages.ubuntu.com/precise-updates/apt)

> **oldos2er said:**
> 
 I'd consider filing a bug against the package apt_0.8.16~exp12ubuntu10.10_i386.deb

I don't think there's something wrong with APT. The problem seems to be that *gpg* doesn't accept the *--primary-keyring* option.

---

### Post by oldos2er on 2013-04-24
Ok, thanks diesch.

---

