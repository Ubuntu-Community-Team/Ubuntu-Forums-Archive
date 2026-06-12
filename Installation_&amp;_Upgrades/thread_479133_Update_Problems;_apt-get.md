---
title: "Update Problems; apt-get"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by yano on 2007-06-20
Alright I've been getting some error messages lately and it's a looping process everytime I do what it tells me to do, to fix it.

When I run the update manager I get this: 
> It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

When I rollover the orange thingy in the corner for the update-manger I get this: 
**' Error: BrokenCount > 0 '**

Here is the terminal pasting of what the update-manager told me to do.

> root@YanoDesktop:/home/yano# apt-get
apt 0.6.46.4ubuntu10 for linux i386 compiled on Mar 14 2007 17:43:24
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
root@YanoDesktop:/home/yano# apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mjpegtools: Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installed
E: Unmet dependencies. Try using -f.
root@YanoDesktop:/home/yano# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmjpegtools0
The following NEW packages will be installed:
  libmjpegtools0
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0B/209kB of archives.
After unpacking 537kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 142214 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@YanoDesktop:/home/yano# 


Any way to fix this? Besides not being able to update, any ideas? Could me sources.list be causing problems. I went here and got a fresh new sources.list: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

EDIT: In the Synpatic manager I updated my sources (just reloaded them) and I get this: 
> W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466


Also I can't get Shareaza to open (it's using Wine). I think I might have to re-install wine.

Also I clicked Edit > Fix Broken Packages: Then apply.

I get this (to be installed):** libmjpegtools0 (version 1:1.8.0-0.4) will be installed**
Unchanged: **transcode** and **wine**

Then I click ok, and get this error message
> E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a

---

### Post by yano on 2007-06-25
Ok I found a fix! 

$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb

Then do a couple of more commands to clean up:

$ sudo dpkg --configure -a
$ sudo apt-get -f install

Got the answer from another forum (after doing some more googling).

---

### Post by directcharitycontribution on 2007-08-30
Thank You.

---

### Post by sharjeelsayed on 2007-09-28
Run
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

More Info on [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

