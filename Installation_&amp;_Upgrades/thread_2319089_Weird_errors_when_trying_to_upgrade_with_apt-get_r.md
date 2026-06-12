---
title: "Weird errors when trying to upgrade with apt-get regarding avidemux"
date: 2016-04-01
forum: Installation &amp; Upgrades
---

### Post by Grace_Palazzolo on 2016-04-01
Not sure what to make of these errors that occurred while performing an update/upgrade with apt-get. I am still fairly new at this, so I can't quite parse everything, but it sounds like I should remove avidemux, although I don't know what effect that will have on my system overall. Also there seems to be a problem of trying to overwrite an existing file.

Here is  the terminal output:

```
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  gimp libgimp2.0
The following packages will be upgraded:
  avidemux2.6-common
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/425 kB of archives.
After this operation, 1,706 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 703895 files and directories currently installed.)
Preparing to unpack .../avidemux2.6-common_1%3a2.6.12-1~getdeb2~wily_all.deb ...
Unpacking avidemux2.6-common (1:2.6.12-1~getdeb2~wily) over (1:2.6.10-1~ppa+trusty9) ...
dpkg: error processing archive /var/cache/apt/archives/avidemux2.6-common_1%3a2.6.12-1~getdeb2~wily_all.deb (--unpack):
 trying to overwrite '/usr/share/avidemux6/help/QtScriptQT4/class_spin_box_control.png', which is also in package avidemux2.6-plugins-qt4:amd64 1:2.6.12-2~ppa+trusty1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/avidemux2.6-common_1%3a2.6.12-1~getdeb2~wily_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I also got a GUI output for some reason, even though I was working in Terminal. And to be clear, this is why I think I should remove avidemux, though at what risk I do not know. I couldn't copy as text, so I've attached[ATTACH=CONFIG]268095[/ATTACH][ATTACH=CONFIG]268096[/ATTACH][ATTACH=CONFIG]268097[/ATTACH] the screenshots. In the last one, it says to remove avidemux.

---

### Post by Bucky Ball on 2016-04-01
Well, looks like you've added the getdeb repo and that might be attempting to install a newer version, a dependency of which is conflicting. 

You're on 15.10 I presume? For a start, run:

> sudo apt-get autoremove 

... then try again and see if anything changes.

Yea, just had a check of your first screen shot. Are you running Trusty but you have added the Wily getdeb PPA? There is a conflict between avidmux .10 and .12.

---

### Post by Grace_Palazzolo on 2016-04-01
Thanks for you answer. I am running Trusty. I carried out the **autoremove**. Here is the output:

```
$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lib32gcc1 libc6-i386 libcgmanager0:i386 libdrm2:i386 libudev1:i386
0 upgraded, 0 newly installed, 5 to remove and 31 not upgraded.
1 not fully installed or removed.
After this operation, 10.4 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 703894 files and directories currently installed.)
Removing lib32gcc1 (1:4.9.3-0ubuntu4) ...
Removing libc6-i386 (2.19-0ubuntu6.7) ...
Removing libudev1:i386 (204-5ubuntu20.18) ...
Removing libcgmanager0:i386 (0.24-0ubuntu7.5) ...
Removing libdrm2:i386 (2.4.64-1~ubuntu14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Setting up gimp-data (2.8.16-1~getdeb1) ...
Installing new version of config file /etc/gimp/2.0/gimprc ...
W: Duplicate sources.list entry http://ppa.launchpad.net/openjdk-r/ppa/ubuntu/ trusty/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/openjdk-r/ppa/ubuntu/ trusty/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems 
$
```

Since it suggesed that I run** apt-get update** to correct, I did so. Here is the tail end of the output:

```
                    
Fetched 2,886 kB in 21s (133 kB/s)                                             
W: GPG error: https://private-ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E131728675254D99
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
grace@aspire:~$ 

```

Now what?

Regarding your comment about the Wily getdeb PPA, someone suggested I add that, I believe, so that I could install openjdk 8. Yes, actually this seems to be what has started the whole mess, and I don't think I was able to complete the installation of openjdk 8. I had read that it was safe to add the repository in question with 14.04, but perhaps I was mistaken? Should I remove that repository from my list??

And what about avidemux? What do I do next?

Sorry if these questions seem stupid.

---

### Post by Bucky Ball on 2016-04-01
Well, if not the problem, there's a problem:

```
W: GPG error: https://private-ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E131728675254D99
```

Get rid of that repository. Open Software and Updates> Other Software and untick it or remove it completely. Then:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Post back any errors, please.

(PS: If you untick or remove the getdeb repo that should fix the avidmux issue.)

---

### Post by Grace_Palazzolo on 2016-04-01
Well, I think the private-ppa.launchpad.net is not the problem, because that has been there for months and months. I am also loathe to remove it because apparently Software Center added it. Here is the screenshot:

[ATTACH=CONFIG]268126[/ATTACH]


Are you suggesting that I remove wily-getdeb and the openjdk ones? I am actually kind of confused by what you are saying.  Which ones to remove? Well, I will remove what appears to be duplication (openjdk) I unchecked a few things and here's what's left:

[ATTACH=CONFIG]268128[/ATTACH]

---

### Post by Grace_Palazzolo on 2016-04-01
I overlooked your postscript comment to uncheck the wily getdeb stuff, so I did that. Then I did [FONT=courier new]**sudo apt-get update**[/FONT], and there were no errors, except for that GPG error with private-ppa. Then I ran [FONT=courier new]**dist-upgrade**[/FONT], and that got rid of the other errors. No more probs with avidemux.

Can you tell me more what is going on with the private-ppa one? What does 'GPG' mean?

Also, I see that I am still running Java version "1.7.0_95", which is what started this mess because I wanted to install Java 8, and I see have failed in that. :(

---

### Post by Bucky Ball on 2016-04-02
Never seen the 'private.ppa'. Unsure why Ubuntu would have added it. Is it in Other Software tab?

You sound like you have added a few third-party PPAs. Be aware that Canonical cannot vouch for the compatibility of these PPA, they are not officially tested and you use at own risk. If something becomes obsolete in a PPA or the PPA goes down for some reason (which looks like is what's happening which is why I suggested you disable it) it is up to the maintainer of the PPA to rectify, whoever they happen to be.

---

### Post by ian-weisser on 2016-04-02
PPAs are not official, supported Ubuntu software. They are for testing and unofficial distribution.
It seems unlikely that your system magically added a PPA without your instruction to do so.

The large number of non-Ubuntu sources (PPAs) puts you at higher risk of another version conflict.

You can use PPAs all you like, but must the learn the simple skills of recognizing and resolving these conflicts manually.
If you don't want to learn the details of package management, consider migrating from PPA sources to the official,stable, supported versions in the Ubuntu repositories.

---

### Post by Grace_Palazzolo on 2016-04-03
I see. I didn't realize the in's and out's of this. I actually would like to learn the details of package management (I know I can't do it here), especially since there is unsupported software that I probably wouldn't want to remove because I actually use it (although perhaps some of it could go.)

---

### Post by Bucky Ball on 2016-04-04
Well, you've added a lot of stuff there, and conflict could abound. Best remedy is to untick them all in 'Other Software' and add them one by one. When you get a problem update/upgrading or some other noticeable issue, you've found the needle in the haystack. Generally, there is no need to install a million and one PPAs. Best avoided. If there's something specific that you need to get something work or add a needed functionality, fair enough, but if one bungs them in expecting that is going to fix things they could be sadly mistaken. A large collection of PPAs is likely to cause more issues than it solves.

The default install should have what a user needs to get running. If it's the latest and greatest they're after, best to install a new version of the OS than a dozen PPAs ...

---

### Post by ian-weisser on 2016-04-04
Lesson about Sources/Repositories:

Ubuntu isn't a walled garden.
That's one of it's big features.
You can add Official-Ubuntu-Sources...and Dangerous-Malware-Sources...and Break-Your-System-Sources...and PPAs...equally easily.
The responsibility for vetting each new source is up to you. It's your system. You *own* it. You are the one who must fix it if it breaks.

We generally recommend sticking with the Official Ubuntu Repositories, since those are supported, tested, safe, and secure.


Lesson about dependencies:

Each software package may have lots of dependencies, which in turn may have lots more dependencies.
This is a legacy of much smaller storage devices. Lots of duplicate libraries were wasteful and hard to maintain, so Debian standardized.
In each release, all packages that depend on, say, libfoo depend upon the same version of libfoo. Only one copy of libfoo gets installed to a predictable location, and all software uses that.

This works great, as long as everything you install depends upon that version of libfoo.
If you go outside that release of Debian/Ubuntu and install software that requires a different version of libfoo, then you create a problem.
(In fact, this is a version conflict, the very problem you had!)

Unfortunately, some new or unskilled packagers create packages based upon whatever (updated/different) libs are on their system instead of using a stock Debian/Ubuntu release...creating version conflicts. Avoid their sources for obvious reasons.


There are several ways around the problem, but few of them are easy.
You can use the version of the software compatible compatible with the release from the Debain/Ubuntu sources (easiest)
You can change to a distro that does have the software you want already in their repositories
You can install a custom system in a container or VM for that one non-Ubuntu application.
You can recompile the software yourself using the source code and your release's Debian/Ubuntu dependencies.
You can install a second set of properly-versioned-dependencies to  support the application...but you cannot use the package manager to do  this. Manual only.
You can statically compile the software and dependencies into a much larger binary, so it doesn't use the system-provided dependencies.

---

