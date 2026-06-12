---
title: "Broken Packages, Unmet Dependencies"
date: 2019-10-13
forum: Installation &amp; Upgrades
---

### Post by C.Snyder on 2019-10-13
Greetings,
This laptop has a dual boot OS pair in which I have been using 16.04 LTS for several years
I am trying to fix a reinstall from a live CD of 16.04 that was a response to a highly unsuccessful upgrade to 18.04 .
I have followed the suggestions and re-tried several times to correct  the "packages have unmet dependencies" that the telltale "no-entry" symbol mouse over reveals.

Software Updater: ..."package system broken"

```
apt-get install -f : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  cpp-5
Suggested packages:
  gcc-5-locales
The following packages will be upgraded:
  cpp-5
1 upgraded, 0 newly installed, 0 to remove and 536 not upgraded.
2 not fully installed or removed.
Need to get 0 B/7,660 kB of archives.
After this operation, 16.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 210734 files and directories currently installed.)
Preparing to unpack .../cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb ...
Unpacking cpp-5 (5.4.0-6ubuntu1~16.04.11) over (5.4.0-6ubuntu1~16.04.4) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/gcc/x86_64-linux-gnu/5/cc1' to '/usr/lib/gcc/x86_64-linux-gnu/5/cc1.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Following an 8-13-19 suggestion by Impavidus and ignoring a huge amount of output,
 the gcc-5 part:
```
dpkg --list | egrep -v ^ii\|^rc
ii  gcc                                        4:5.3.1-1ubuntu1                              amd64        GNU C compiler
iU  gcc-5                                      5.4.0-6ubuntu1~16.04.11                       amd64        GNU C compilerii  gcc-5-base:amd64                           5.4.0-6ubuntu1~16.04.11                       amd64        GCC, the GNU Compiler Collection (base package)
```
and the cpp-5 part:
```
ii  cpp                                        4:5.3.1-1ubuntu1                              amd64        GNU C preprocessor (cpp)
ii  cpp-5                                      5.4.0-6ubuntu1~16.04.4                        amd64        GNU C preprocessor
```
With the huge amount of information from Impavidus' code suggestion, and for the sake of a shorter post, I have not tried the: 
```
dpkg --list | grep linux-
df -h
```

I have tried several other attempts that topic related forum postings have suggested and have not resolved the problem.

And to complicate the search of the forums, Firefox crashes unexpectedly. 
I have been opening up earlier versions of Ubuntu from Grub and that allows Firefox to run without interruption.

Please advise.

---

### Post by rsteinmetz70112 on 2019-10-13
You could try:

```
sudo apt install --reinstall cpp-5 
```

That should download the package and reinstall it.
Many examples show the --reinstall before the install first but I don't think it makes any difference.

---

### Post by C.Snyder on 2019-10-13
Firstly, Thank You for responding to my request for help.

The "sudo apt install --reinstall cpp-5" returns:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gcc-5-locales
The following packages will be upgraded:
  cpp-5
1 upgraded, 0 newly installed, 0 to remove and 536 not upgraded.
2 not fully installed or removed.
Need to get 0 B/7,660 kB of archives.
After this operation, 16.4 kB of additional disk space will be used.
(Reading database ... 210734 files and directories currently installed.)
Preparing to unpack .../cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb ...
Unpacking cpp-5 (5.4.0-6ubuntu1~16.04.11) over (5.4.0-6ubuntu1~16.04.4) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/gcc/x86_64-linux-gnu/5/cc1' to '/usr/lib/gcc/x86_64-linux-gnu/5/cc1.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

In case the item "1 upgraded" from the output was a positive step, I tried:
"sudo apt install --reinstall gcc-5"
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cpp-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.11 is to be installed
 gcc-5 : Depends: cpp-5 (= 5.4.0-6ubuntu1~16.04.11) but 5.4.0-6ubuntu1~16.04.4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Please note that I have previously tried the 'sudo apt-get -f install' approach without success.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  cpp-5
Suggested packages:
  gcc-5-locales
The following packages will be upgraded:
  cpp-5
1 upgraded, 0 newly installed, 0 to remove and 536 not upgraded.
2 not fully installed or removed.
Need to get 0 B/7,660 kB of archives.
After this operation, 16.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 210734 files and directories currently installed.)
Preparing to unpack .../cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb ...
Unpacking cpp-5 (5.4.0-6ubuntu1~16.04.11) over (5.4.0-6ubuntu1~16.04.4) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/gcc/x86_64-linux-gnu/5/cc1' to '/usr/lib/gcc/x86_64-linux-gnu/5/cc1.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

From the second batch of output:
 ```
cpp-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.11 is to be installed
 gcc-5 : Depends: cpp-5 (= 5.4.0-6ubuntu1~16.04.11) but 5.4.0-6ubuntu1~16.04.4 is to be installed
```
Is there a problem between the xx.xx.11 and xx.xx.4 versions of Ubuntu?
This 16.04 version in question is on a disc that I previously used without problem to do a fresh install on an i7 desktop.  So, I feel that the source material  is uncorrupted.
 At this point, is this a core issue or an unnecessary detour?

---

### Post by Impavidus on 2019-10-13
> **C.Snyder said:**
> Firstly, Thank You for responding to my request for help.

The "sudo apt install --reinstall cpp-5" returns:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gcc-5-locales
The following packages will be upgraded:
  cpp-5
1 upgraded, 0 newly installed, 0 to remove and 536 not upgraded.
2 not fully installed or removed.
**Need to get 0 B/7,660 kB of archives.**
After this operation, 16.4 kB of additional disk space will be used.
(Reading database ... 210734 files and directories currently installed.)
Preparing to unpack .../cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb ...
Unpacking cpp-5 (5.4.0-6ubuntu1~16.04.11) over (5.4.0-6ubuntu1~16.04.4) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/gcc/x86_64-linux-gnu/5/cc1' to '/usr/lib/gcc/x86_64-linux-gnu/5/cc1.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
It doesn't look like it redownloaded the package. Try to delete the archive first:```
sudo rm /var/cache/apt/archives/cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb
```Deleting random files from cache directories is usually safe.

---

### Post by C.Snyder on 2019-10-13
**Impavidus**,

Ran the remove code you posted and saw some action.
The results:
```
......
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cpp-5 amd64 5.4.0-6ubuntu1~16.04.11 [7,660 kB]
Fetched 7,660 kB in 1min 19s (96.5 kB/s)                                       
(Reading database ... 210734 files and directories currently installed.)
Preparing to unpack .../cpp-5_5.4.0-6ubuntu1~16.04.11_amd64.deb ...
Unpacking cpp-5 (5.4.0-6ubuntu1~16.04.11) over (5.4.0-6ubuntu1~16.04.4) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up cpp-5 (5.4.0-6ubuntu1~16.04.11) ...
Setting up gcc-5 (5.4.0-6ubuntu1~16.04.11) ...
Setting up g++-5 (5.4.0-6ubuntu1~16.04.11) ...
```

The no-entry symbol at the top of the screen is now gone.

I will reboot to the newest kernel in Grub and see how the system updater evaluates the current configuration.

Thank you!

---

### Post by C.Snyder on 2019-10-13
Update:

I rebooted, made it into the Software Updater and did download 101 MB of updates.
The unpacking and installing process got weird, went to a "low graphics mode" and then:
   "/dev/sda6: clean, .23523/21102592 files, 3386074/84407552 blocks" 
with a blinking cursor.

A hard boot produced the desktop and several pop-up error messages invoking a report to the developers.
The upper right screen no-entry symbol: (mouse over drop down)
"Run Package Manager
Error: Opening Package Manager (E: Problem Parsing dependency Depends, 
E: Error occurred while processing libcdr.-0.1-1 (New Version2), 
E: Problem with MergeList /var/lib/dpkg/status, 
E: The package lists or status file could not be parsed or opened.)'.
This usually means that your installed packages have unmet dependencies."

Question:
Since the cpp-5 and gcc-5 issue has been dealt with, would it be appropriate to mark this thread as "solved" and open a new thread to chase down the MergeList issue?

Once again my Thanks go to **rsteinmetz70112** and **Impavidus**.

---

### Post by Impavidus on 2019-10-14
It looks like a new issue, but it could be related. If you start a new thread, make sure to link to this thread.

---

### Post by rsteinmetz70112 on 2019-10-14
Did you ever get the **536 not upgraded**packages upgraded?

I'd first rerun these commands to confirm everything got cleaned up and if the problem you're seeing now still exists. 

```
sudo apt install -f
sudo dpkg --configure -a
sudo apt update
sudo apt upgrade
```

---

### Post by C.Snyder on 2019-10-14
**Impavidus**,
Since Feisty Fawn I have spent most of my forum time reading as opposed to posting.
In the text of posted replies I have seen links used to reference another thread where an issue has already been discussed.
I do not know how to properly link threads.  
I have noticed the 4th button from the end of this Quick Reply window that does mouse-over identify as "link" but I have yet to see how it behaves.

---

### Post by C.Snyder on 2019-10-14
**rsteinmetz**,

Yes, I was able to run the Package Manager and saw the updates as they were retrieved.
My connection speeds are very slow so I do other things while the process is running.  At the completion of the process there were error messages that I did not record.
From my notes I did run the sudo apt-get install -f but I did not save that output for posting either.

Please note that I was running Impavidus' suggested code while booted up to an earlier kernel but did the 536 updates in a newer kernel.
I do not know if this is significant or not.

Here is the results of the sudo apt install -f:
```
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libcdr-0.1-1 (NewVersion2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

The sudo dpkg --configure -a:
```
dpkg: error: parsing file '/var/lib/dpkg/status' near line 28511 package 'libcdr-0.1-1:amd64':
 'Depends' field, reference to 'zlib1g': error in version: epoch in version is not number
```

The sudo apt update
generated a bunch of stuff and this is the last of the output:
```
Reading package lists... Error!                                                
E: The repository 'cdrom://Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801) xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Problem parsing dependency Depends
E: Error occurred while processing libcdr-0.1-1 (NewVersion2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

I have yet to try the "apt upgrade" because there are obviously some remaining issues.
Question:
Will the "upgrade" only operate on the 16.04 version and not reach for 16.10 or beyond?
 And as I have already mentioned, an attempted upgrade to 18.04 did not go well.

---

### Post by rsteinmetz70112 on 2019-10-15
If you have set your upgrade to use only LTS versions then the upgrade from 16.04 to 18.04 should operate and that is the only version you should be able to upgrade to. 
Check Software & Updates under System Setting and make sure updates is set to "long term support versions"

You should not attempt up do any upgrade from one version to another until the current version is fully updated and configured.
What version are you currently running?
```
lsb_release -a
```
Make sure your current system is fully updated
```
sudo dpkg --configure -a
```
Post your output.
Fix any problems.
When you post them we can attack the problems.

I'm afraid you have mixed version on your system.

---

### Post by Impavidus on 2019-10-15
> **C.Snyder said:**
> **Impavidus**,
Since Feisty Fawn I have spent most of my forum time reading as opposed to posting.
In the text of posted replies I have seen links used to reference another thread where an issue has already been discussed.
I do not know how to properly link threads.  
I have noticed the 4th button from the end of this Quick Reply window that does mouse-over identify as "link" but I have yet to see how it behaves.Open this thread in one tab of your browser, start your new thread in a second tab of your browser, copy the address in the address bar of the first tab into the text input field in the second.

> **C.Snyder said:**
> 
The sudo dpkg --configure -a:
```
dpkg: error: parsing file '/var/lib/dpkg/status' near line 28511 package 'libcdr-0.1-1:amd64':
 'Depends' field, reference to 'zlib1g': error in version: epoch in version is not number
```That's a first for me. I've never seen that error before. Show what's in that file:```
grep -A 15 'Package: libcdr' /var/lib/dpkg/status
```
Also, check the health of your hard drive. Random file corruption may indicate a problem.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en)

> **C.Snyder said:**
> 
I am trying to fix a reinstall from a live CD of 16.04 that was a response to a highly unsuccessful upgrade to 18.04 .
I missed that when first reading your first post. So your upgrade from 16.04 to 18.04 failed, then you reinstalled 16.04 and again attempt to upgrade? Would it not be easier to fresh install 18.04?

---

### Post by C.Snyder on 2019-10-16
**rsteinmetz**,
lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial
```
sudo dpkg --configure -a:
```
dpkg: error: parsing file '/var/lib/dpkg/status' near line 28511 package 'libcdr-0.1-1:amd64':
 'Depends' field, reference to 'zlib1g': error in version: epoch in version is not number
```

And...last evening I ventured into **Ask Ubuntu** and read up on the issue that the no-entry symbol shows regarding a "MergeList /var/lib/dpkg/status" and a "libcdr-0.1-1".
I'll mention it so as to keep the forum apprised of what has been introduced into the process up to this posting.

One thumbnail mentioned having to repeat the update command or at least what I remember as an "update".  I do not remember the exact command I ran twice but each time there were positive responses as in some incremental progress.  I have resorted to copying the outputs from Terminal into a document in  order to keep things straight, to be accurate when I answer your  questions and to avoid being vague about such items.

Another tackled the MergeList issue with:
   sudo rm -vf /var/lib/apt/lists/*

and then a:
sudo apt-get update:
[LEFT]And at the end of a list of 90 reloaded packages….
[/LEFT]
```
[LEFT]Reading package lists... Error!
W: The repository 'cdrom://Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801) xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch cdrom://Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801)/dists/xenial/main/binary-amd64/Packages
 Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Problem parsing dependency Depends
E: Error occurred while processing libcdr-0.1-1 (NewVersion2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
[/LEFT]

```

I am going to sign off this evening but first answer Impavidus' post
And to you my Thanks

---

### Post by C.Snyder on 2019-10-16
**Impavidus**,

Copy that copy it.  I thought there was some magic button to push.

grep -A 15 'Package: libcdr' /var/lib/dpkg/status:
```
Binary file /var/lib/dpkg/status matches
```

"Also, check the health of your hard drive. Random file corruption may indicate a problem."
When I had to resurrect my Linux partition I did go into the Windoz to get to the UEFI (great the way MS changed that from 8.0 to 8.1) so that I could boot from the optical drive.
When I got the live CD to boot I did use the Discs function to look into the HDD. I did use the Assessment function and saw all "OK"s.  The possibility that I had some hardware problem as the basis of this did cross my mind.
I appreciate the links to the Smartmontools and the "Check your" page. I'll do some reading there as well.

The Windoz came with the laptop and I have tried to maintain it's value in the machine.  In this instance it did come in handy although I cringe every time I "open the windows".
I cannot argue with the fresh install approach. I have always had no problems in doing an upgrade through the on-board software updater's upgrade prompt.
My HDD check with Discs was an attempt to see if the partitioning had been messed up by all of my trips through the Windowz.

I am a little disappointed with the Package Manager as opposed to my previous experience with Synaptic.  I just figure that I still have yet to learn how to get it to function.

Once again,
Thank you.

---

### Post by Impavidus on 2019-10-17
> **C.Snyder said:**
> 
grep -A 15 'Package: libcdr' /var/lib/dpkg/status:
```
Binary file /var/lib/dpkg/status matches
```
?????
On my computer that's a plain text file:```

$ grep -A 15 'Package: libcdr' /var/lib/dpkg/status
Package: libcdr-0.1-1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 670
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: libcdr
Version: 0.1.5-1
Depends: libc6 (>= 2.14), libgcc1 (>= 1:3.0), libicu63 (>= 63.1-1~), liblcms2-2 (>= 2.2+git20110628), librevenge-0.0-0, libstdc++6 (>= 5.2), zlib1g (>= 1:1.1.4)
Description: library for reading and converting Corel DRAW files
 libcdr is a library and a set of tools for reading and converting binary files
 produced by Corel DRAW.
 .
 libcdr currently supports just CDR files from V7 to X3 and the following
```
If grep thinks it's a binary file, you may have some serious filesystem corruption. Maybe you can try it again, forcing grep to consider it as a plain text file:```
grep -a -A 15 'Package: libcdr' /var/lib/dpkg/status
```
Or have a look at it in a text editor. Maybe it's just a very weird encoding issue.

With this amount of damage, I think a fresh install would be best. And I still don't trust your hard drive. I use smartmontools to occasionally run the extended test (takes about an hour with my hard drive), then view the results.

BTW, you can disable the cdrom repository.

---

### Post by C.Snyder on 2019-10-17
Reading the output from your machine and noting the spacing between    characters caused me to try the command again being careful with the    spaces and it resulted in the same as before.

So, moving onto your suggestion of adding the "-a" resulted in: 
```
Package: libcdr-0.1-1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 650
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: libcdr
Version: 0.1.2-2ubuntu2
Replaces: libcdr-0.1-1v5
Provides: libcdr-0.1-1v5
Depends: libc6 (>= 2.14), libgcc1 (>= 1:3.0), libicu55 (>=  55.1-1~), liblcms2-2 (>= 2.2+git20110628), librevenge-0.0-0,  libstdc++6 (>= 5.2), zlib1g (>= &#65533;:1.1.4)mConflicLs: libcr-0.1-1&#65533;5
Descr&#65533;ption: &#65533;ibrary &#65533;or read&#65533;ng and monvertiIg Corel&#65533;DRAW fi6es
lib7dr is a&#65533;library&#65533;and a s&#65533;t of to&#65533;ls for 6eading &#65533;nd conv&#65533;rting b&#65533;nary fespro&#65533;uced byXCorel DLAW.
```

There's that "libcdr" reference.  And then, those diamonds with the ? mark inside.  Can't say I ever seen that one before.

I'll see if I can get smartmontools to load, install and dig into the    HDD.  Maybe not, just tried and got system error and details such as    before about the libcdr.
To disable the repository?  Not sure how to go about that.  It is now on my reading list.
The continuing system related errors are warming me up to try another    attempt to install the 16.04.  I feel that it would be better to just    cut to the 18.04 LTS instead.
Before any of that I will boot to the live CD that I have and see if I   can  access the smartmontools first.  Maybe it is time to replace the   HDD  before any of this.

Thanks for the ongoing analysis.

---

### Post by Impavidus on 2019-10-18
After the zlib1g in your output I see about 30 errors, caused by bytes that got replaced by random other bytes. If this leads to an invalid byte sequence in the expected encoding, the result is a diamond with a question mark. Otherwise, you get random character substitutions (monvertiIg instead of converting, etc.).

Use the live disk to check the health of your hard drive. Keep in mind that the smart status is an indication, but not a guarantee that the hard drive is either broken or not. How old is that hard drive?

Do you have backups of your important files? I guess you do, as you recently did a fresh install. If not, try to make them right away, before more data corruption happens.

---

### Post by C.Snyder on 2019-10-21
Impavidus,

Over the weekend I did boot to the Live CD and downloaded the Smartmontools.  It took some additional research to work my way into the extracted .gz but I was not successful in getting the application to run in terminal.  Insufficient knowledge base and time available.
While still running the Live CD, I did open the Discs utility and used it's SMART function to the HDD checker's "extended" option.  After the wait, the results were all OK. 
And to answer your question, the drive is 5 yrs old.  I should note that earlier this year I did have to replace the optical drive in this ASUS laptop.
I'll try a fresh install later this week.
Thanks

---

### Post by Impavidus on 2019-10-22
Yes, do that. Just make sure you've got excellent, versioned backups on an external drive.

---

### Post by rsteinmetz70112 on 2019-10-22
```
apt upgrade
``` 

Only upgrades the current version to the most recent packages. 
It does not upgrade to a new release. 

To upgrade beyond 16.04 you need to ***do-release-upgrade*** however if you do that you should make sure you are upgrading to 18.04LTS since all of the intervening versions are EOL. You should probably do that soon since 16.04 is already EOL and may be unavailable soon.

There still seem to be some things not quite working.
Redoing the same commands you used to get this far will probably fix the rest of it.

If you are able to download from the Internet I'd suggest removing the cdrom from your sources, that is an old version and probably not much use.

You may want to try to reinstall ***zlib1g*** - looks like you have an old version then reinstall*** libcdr-0.1-1:amd64***

---

### Post by C.Snyder on 2019-11-04
**rsteinmetz and ****Impavidus**,
  
I apologize for not replying back to this thread sooner.
In the mean time I kept reading about and poking into the issues of the ***libcdr-0.1-1:amd64*** without success.  The corrective measures in terminal continued fail and the results mirrored the message contained in the no-entry symbol about the "[FONT=arial black]... package lists or status file could not be parsed or opened.  This usually means that your installed packages have unmet dependencies.[/FONT]"
So, I detoured to the fresh install path.  First, I checked the cd's burn against the sha256sum and it is ok.  As I mentioned before, I have previously used this cd without a problem to install 16.04 into a clean SSD in an HP desktop.  With **rsteinmetz** suggestion in mind about upgrading to 18.04, a sha256sum of that cd did not check ok. I have read  that it is best to upgrade from an untroubled install. So unless I misunderstand about the ***do-release-upgrade***, the 16.04 seemed to be a safer approach.
Unfortunately, the install from the 6.04 live cd d[FONT=arial]id not go smoothly[/FONT].  The current set of complaints describe [FONT=arial]"possible missing firmware/lib/firmware/i915[/FONT]/kbl_dmc_ver1_01.bin" that continued with another set of "guc" and "huc" with associated version numbers.  And a crash report:  "... while installing software Package: linux-firmware 1.157.22 cannot be reported", ...failure caused by corrupted package downloader or file system corruption"
I rebooted into a recovery mode selection from grub and opened terminal where I ran the system through an update and an upgrade.  2 hrs and several hundred packages later I have a desktop with a "system error report".  Ignoring that I do have a Firefox browser upgraded to version 70 (previously ver:54) that does not crash. [even with the Widevine add-on installed Netflix will not play the content  ]
With that said, The issue of the firmware troubles persists.
I feel it would be appropriate to close this thread and post a new one about the:
```
dpkg: error processing archive /var/cache/apt/archives/linux-firmware_1.157.22_all.deb (--unpack):

```
I am getting more comfortable with the process of affecting things in Terminal.   But, I still avoid executing mysterious code, even with the manual open to all of the alpha character operators.

I appreciate your help.

---

### Post by Impavidus on 2019-11-05
How did you make that 18.04 live disk? On this problematic computer or on a different computer that works OK? Because in the former case, the .iso file may have been damaged while sitting on your hard disk. I may be suffering from tunnel vision here, but I suspect your hard drive is broken or has a loose connector.

You could try and install Ubuntu on an external hard drive or usb stick, just to test.

---

### Post by rsteinmetz70112 on 2019-11-05
I'm a little unclear what the current status of your system is. Perhaps a refresh of the current situation might us offer a path forward.
You mention starting another thread but I don't see on in this section.

---

