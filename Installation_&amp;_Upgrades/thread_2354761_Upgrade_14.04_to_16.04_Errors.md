---
title: "Upgrade 14.04 to 16.04 Errors"
date: 2017-03-06
forum: Installation &amp; Upgrades
---

### Post by ridge1234-au on 2017-03-06
I am unsure what to do after an upgrade from 14.04 to 16.04.2 LTS.  It has notified me that I have an unstable system. At one point I was informed I should create a bug report for packages without scripts in them and not installing correctly. I tried to do a sudo apt-get update to correct the problems but they persist.

Here is the apt-get error output:

The following packages were automatically installed and are no longer required:
lots ...

The following packages will be upgraded:
  ack-grep cpp-doc gcc-doc
3 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
2 not fully installed or removed.
Need to get 0 B/68.0 kB of archives.
After this operation, 18.4 kB disk space will be freed.
Do you want to continue? [Y/n] y
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
(Reading database ... 2300474 files and directories currently installed.)
Preparing to unpack .../cpp-doc_4%3a5.3.1-1ubuntu1_i386.deb ...
install-info: No dir file specified; try --help for more information.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/cpp-doc_4%3a5.3.1-1ubuntu1_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../gcc-doc_4%3a5.3.1-1ubuntu1_i386.deb ...
install-info: No dir file specified; try --help for more information.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/gcc-doc_4%3a5.3.1-1ubuntu1_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../ack-grep_2.14-4_all.deb ...
Unpacking ack-grep (2.14-4) over (2.12-1) ...
dpkg: error processing archive /var/cache/apt/archives/ack-grep_2.14-4_all.deb (--unpack):
 trying to overwrite '/usr/bin/ack', which is the diverted version of '/usr/bin/ack-grep'
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-doc_4%3a5.3.1-1ubuntu1_i386.deb
 /var/cache/apt/archives/gcc-doc_4%3a5.3.1-1ubuntu1_i386.deb
 /var/cache/apt/archives/ack-grep_2.14-4_all.deb
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)

What should I do to check that I have a stable system?

---

### Post by kc1di on 2017-03-06
Hello ridge1234-au and welcome to Ubuntu,

this is one of the reasons that I personally do a fresh install of newer LTS instead of trying to do an upgrade. 
Please list the content of your /etc/apt/sources.list file. 
Also did you have any PPA's enable before you did the upgrade? if so those should have been disabled before doing the upgrade. (Just my personal opinion)
if your system is running ok it's most likely ok.  But It will take some time to get the sources list fixed.

---

### Post by oneleded on 2017-03-18
kc1di; just a quick question or so. how do you prepare partition before fresh install? as in erase, reformat, wipe with 0's, etc.  //Ed

---

### Post by Xiguus on 2017-04-24
Hi ridge1234-au

Wit the single difference that I do not have ack-grep installed, I have exactly the same problem under exactly the same conditions, ie upgrading from 14.04 to 16.04. Specifically, I have grep-doc  and cpp-doc versions 4.8.2-1ubuntu6 installed, and the update manager flags an update to version 5.3.1-1ubuntu1. When I try to run the update I get the same messages that you do. The lines that matter are:
> 
install-info: No dir file specified; try --help for more information.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/cpp-doc_4%3a5.3.1-1ubuntu1_i386.deb (--unpack):
 there is no script in the new version of the package - giving up


I've tried various ways to get a result including dpkg, eg

```

sudo dpkg --force-remove-reisnstreq -r gcc-doc

```,

which tells me I need to update before I can remove.

As I see it the error is undeniably in the update package. Based on my experience I would have tagged the error as eg "16.04, gcc-doc, fails update, no script", but it's still a bit disappointing that after a six weeks or so you still haven't received a fix from the forum. It looks like we might have to contact the maintainer directly who, from synaptic, is [EMAIL="ubuntu-devel-discuss@lists.ubuntu.com"]ubuntu-devel-discuss@lists.ubuntu.com[/EMAIL].

Let's hope they can fix it from their end...

Best Regards,

Xiguus

---

### Post by Xiguus on 2017-05-01
Hi again,

OK, it's been six days since previous post and no action yet. Just to put the task in perspective, gcc-doc and ccp-doc are dummy packages that contain a couple of links to the the most recent versioned packages, which contain the actual files. All it takes to fix them is to change 3 links in /usr/share/doc/gcc-doc to point from ../gcc-4.8-base to ../gcc-5.3-base and 2 links in /usr/share/info similarly, and the same for cpp-doc, and to repackage them.
I now have 42 packages queued in synaptic for update that will not proceed because these two packages break the update script. I post the output:
```

N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
(Reading database ... 624993 files and directories currently installed.)
Preparing to unpack .../cpp-doc_4%3a5.3.1-1ubuntu1_amd64.deb ...
install-info: No dir file specified; try --help for more information.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/cpp-doc_4%3a5.3.1-1ubuntu1_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../gcc-doc_4%3a5.3.1-1ubuntu1_amd64.deb ...
install-info: No dir file specified; try --help for more information.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/gcc-doc_4%3a5.3.1-1ubuntu1_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../apt-utils_1.2.20_amd64.deb ...
Unpacking apt-utils (1.2.20) over (1.2.19) ...
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-doc_4%3a5.3.1-1ubuntu1_amd64.deb
 /var/cache/apt/archives/gcc-doc_4%3a5.3.1-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up apt-utils (1.2.20) ...
dpkg: error processing package gcc-doc (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package cpp-doc (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration

```

You will notice that in my case the failing packages are the 64-bit amd64.deb versions, whereas ridge1234-au had their problem with the 32-bit i386.deb versions.

Hope we can get this sorted soon --- it's a little bit vexing...

BR

Xiguus.

---

