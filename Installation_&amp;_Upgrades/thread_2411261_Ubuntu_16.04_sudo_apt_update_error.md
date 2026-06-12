---
title: "Ubuntu 16.04 sudo apt update error"
date: 2019-01-28
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2019-01-28
While installing "picocom", I encountered the following issue. 

```
$ picocom --help
The program 'picocom' is currently not installed. You can install it by typing:
sudo apt install picocom
$ sudo apt install picocom
[sudo] password for username: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  teeworlds-data ttf-dejavu-core
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  picocom
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 19.9 kB of archives.
After this operation, 61.4 kB of additional disk space will be used.
Err:1 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 picocom amd64 1.7-2build0.16.04.1
  Could not open file /var/cache/apt/archives/partial/picocom_1.7-2build0.16.04.1_amd64.deb - open (30: Read-only file system) [IP: 91.189.88.161 80]
Err:1 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 picocom amd64 1.7-2build0.16.04.1
  Could not open file /var/cache/apt/archives/partial/picocom_1.7-2build0.16.04.1_amd64.deb - open (30: Read-only file system) [IP: 91.189.88.161 80]
W: Not using locking for read only lock file /var/lib/dpkg/lock-frontend
W: Not using locking for read only lock file /var/lib/dpkg/lock
W: chown to _apt:root of directory /var/cache/apt/archives/partial failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chmod 0700 of directory /var/cache/apt/archives/partial failed - SetupAPTPartialDirectory (30: Read-only file system)
W: Not using locking for read only lock file /var/cache/apt/archives/lock
W: Problem unlinking the file /var/cache/apt/archives/partial/.apt-acquire-privs-test.kzbSwL - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/cache/apt/archives/partial/picocom_1.7-2build0.16.04.1_amd64.deb - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/cache/apt/archives/partial/picocom_1.7-2build0.16.04.1_amd64.deb - PrepareFiles (30: Read-only file system)
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/p/picocom/picocom_1.7-2build0.16.04.1_amd64.deb  Could not open file /var/cache/apt/archives/partial/picocom_1.7-2build0.16.04.1_amd64.deb - open (30: Read-only file system) [IP: 91.189.88.161 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```


Thereafter, I ran "apt-get update" and encountered more errors:

```
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Ign:4 http://security.ubuntu.com/ubuntu xenial-security InRelease                                                                                                               
Ign:5 http://sg.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                                                   
Hit:6 http://archive.canonical.com/ubuntu xenial InRelease                                                                                                  
Err:6 http://archive.canonical.com/ubuntu xenial InRelease                                     Couldn't create tempfiles for splitting up /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_xenial_InRelease
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Ign:7 http://sg.archive.ubuntu.com/ubuntu xenial-backports InRelease                           
Hit:8 http://ppa.launchpad.net/git-core/ppa/ubuntu xenial InRelease 
0% [8 InRelease gpgv 23.8 kB] [Connecting to sg.archive.ubuntu.com (91.189.88.162)] [Waiting for headers] [Connecting to ppa.launchpad.net (91.189.95.83)]Couldn't create tempfiles for splitting up /var/lib/apt/lists/ppa.launchpad.net_git-coreErr:8 http://ppa.launchpad.net/git-core/ppa/ubuntu xenial InRelease                                                                                       
  Could not execute 'apt-key' to verify signature (is gnupg installed?)

```
and also:


```
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_i18n_Translation-en.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_Components-amd64.yml.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_icons-64x64.tar.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-amd64_Packages.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-i386_Packages.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-all_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_i18n_Translation-en%5fSG - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_i18n_Translation-en.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_Components-amd64.yml.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_icons-64x64.tar - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-amd64_Packages.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-i386_Packages.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-all_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_i18n_Translation-en%5fSG - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_i18n_Translation-en.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_dep11_Components-amd64.yml.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_dep11_icons-64x64.tar.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-amd64_Packages.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-i386_Packages.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-all_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_i18n_Translation-en%5fSG - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_i18n_Translation-en.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_dep11_Components-amd64.yml.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_dep11_icons-64x64.tar.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_source_Sources.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_source_Sources - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_source_Sources - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_source_Sources - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_icons-64x64.tar - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_icons-64x64.tar - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_icons-64x64.tar - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_source_Sources.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_source_Sources - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_binary-amd64_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_binary-i386_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_binary-all_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_i18n_Translation-en%5fSG - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_i18n_Translation-en - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_icons-64x64.tar - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_binary-amd64_Packages.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_source_Sources - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_source_Sources - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_source_Sources - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_source_Sources - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_source_Sources - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_icons-64x64.tar - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_dep11_icons-64x64.tar - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_dep11_icons-64x64.tar - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_source_Sources - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_source_Sources - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_source_Sources - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-amd64_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-i386_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_i18n_Translation-en - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_Components-amd64.yml - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_icons-64x64.tar - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-amd64_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-i386_Packages - PrepareFiles (30: Read-only file system)
W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch https://download.virtualbox.org/virtualbox/debian/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/elementary-add-team/icons/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/git-core/ppa/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/inkscape.dev/stable/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/moka/daily/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/noobslab/icons/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/noobslab/icons2/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/noobslab/macbuntu/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/noobslab/themes/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/numix/ppa/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/openshot.developers/libopenshot-daily/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/oranchelo/oranchelo-icon-theme/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/snwh/pulp/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/tista/adapta/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/restricted/source/Sources  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_source_Sources.xz - open (30: Read-only file system) [IP: 91.189.91.23 80]
E: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/xenial-backports/restricted/source/Sources  Could not open file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_source_Sources.xz - open (30: Read-only file system) [IP: 91.189.88.161 80]
E: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/xenial-updates/restricted/source/Sources  Could not open file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_source_Sources.xz - open (30: Read-only file system) [IP: 91.189.88.161 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (30: Read-only file system)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (30: Read-only file system)

```
Below is /tmp 's permission, seems alright. 

```
ls -ld /tmp
drwxrwxrwt 15 root root 4096 Jan 28 10:54 /tmp

```
Also, gnupg is installed.
$ dpkg -l | grep gnupg
ii  gnupg                                       1.4.20-1ubuntu3.3                                amd64        GNU privacy guard - a free PGP replacement
ii  gnupg-agent                                 2.1.11-6ubuntu2.1                                amd64        GNU privacy guard - cryptographic agent
ii  gnupg2                                      2.1.11-6ubuntu2.1                                amd64        GNU privacy guard - a free PGP replacement (new v2.x)



**At the moment, command `sudo apt update` can't work. How can i fix this issue?**

---

### Post by deadflowr on 2019-01-28
You're output is spamming read only file system errors.
Look at
```
mount
```
and 
```
dmesg
```
Those should tell what's going on to some degree.
It might possibly require an fsck run.
[https://askubuntu.com/a/197468]("https://askubuntu.com/a/197468")

---

### Post by sunbear-c22 on 2019-01-28
In dmesg, I found this issue in red color:

```

[41263.136938] EXT4-fs error (device nvme0n1p3): ext4_ext_check_inode:510: inode #546840: comm updatedb.mlocat: pblk 0 bad header/extent: invalid extent entries - magic f30a, entries 1, max 4(4), depth 2(2)
[41263.138123] Aborting journal on device nvme0n1p3-8.
[41263.139247] EXT4-fs (nvme0n1p3): Remounting filesystem read-only

```

These are the related info from mount:

```

$ mount | grep nvme0n1
/dev/nvme0n1p3 on / type ext4 (ro,noatime,errors=remount-ro,data=ordered)
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p4 on /home type ext4 (rw,noatime,data=ordered)

```


The system had suffered a power trip earlier and i believe this is the first time a "sudo apt-get install" was done since the power trip. 

What should I do next?

---

### Post by sunbear-c22 on 2019-01-28
I tried rebooting the system and instead got a blank screen after boot-up.

Based on dmesg error output ( [COLOR=#000000][FONT=&amp]EXT4-fs error (device nvme0n1p3) ),[/FONT][/COLOR] I realised that my issue was due to a filesystem error in the 3rd partition of my SSD i.e. [COLOR=#000000][FONT=&amp]/dev/nvme0n1p3[/FONT][/COLOR]. I managed to fix this issue via 
 1. Booting up another OS on the same machine which did not mount device  [COLOR=#000000][FONT=&amp]/dev/nvme0n1p3, and[/FONT][/COLOR]
 2. running the "sudo fsck -y  [COLOR=#000000][FONT=&amp]/dev/nvme0n1p3".
[/FONT][/COLOR]

---

