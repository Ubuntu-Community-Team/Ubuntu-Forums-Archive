---
title: "Can't install ttf-mscorefonts-installer since SourceForge update"
date: 2018-03-02
forum: Installation &amp; Upgrades
---

### Post by Xero Xenith on 2018-03-02
Hi,

I recently upgraded from zesty to artful, but I'm having a problem with ttf-mscorefonts-installer. I get a popup every few minutes:

> Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

When I run [FONT=Courier New]sudo apt-get install --reinstall ttf-mscorefonts-installer[/FONT] the issue becomes clear:

```
chris@chris-ubuntu:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcuda1-375 nvidia-opencl-icd-375
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 0 not to upgrade.
Need to get 0 B/27.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 182408 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.6ubuntu2_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.6ubuntu2) over (3.6ubuntu2) ...
Processing triggers for update-notifier-common (3.186) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe [652 B]
Err:1 http://downloads.sourceforge.net/corefonts/andale32.exe                  
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:0524fe42951adc3a7eb870e32f0920313c71f170c859b5f770d82b4ee111e970
  Hashes of received file:
   - SHA256:7a07d3f7cca5c0b38ca811984ef8da536da32932d68c1a6cce33ec2462b930bf
   - Filesize:652 [weak]
  Last modification reported: Thu, 01 Mar 2018 05:30:05 +0000
Fetched 652 B in 1s (367 B/s)                                                  
E: Failed to fetch https://downloads.sourceforge.net/#!/corefonts/andale32.exe  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:0524fe42951adc3a7eb870e32f0920313c71f170c859b5f770d82b4ee111e970
   Hashes of received file:
    - SHA256:7a07d3f7cca5c0b38ca811984ef8da536da32932d68c1a6cce33ec2462b930bf
    - Filesize:652 [weak]
   Last modification reported: Thu, 01 Mar 2018 05:30:05 +0000
E: Download Failed
Setting up ttf-mscorefonts-installer (3.6ubuntu2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu2) ...

```

It seems the file on SourceForge was updated yesterday, causing an error. I'm just using official Ubuntu repos, no PPAs:

```
chris@chris-ubuntu:~$ sudo apt-get update
Hit:1 http://gb.archive.ubuntu.com/ubuntu artful InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]   
Get:3 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]    
Hit:4 http://gb.archive.ubuntu.com/ubuntu artful-backports InRelease           
Fetched 157 kB in 0s (220 kB/s)                                                
Reading package lists... Done

```

Anyone know how to fix this or what to do? Thanks in advance :)

---

### Post by ignoremind on 2018-03-03
> **Xero Xenith said:**
> Hi,

I recently upgraded from zesty to artful, but I'm having a problem with ttf-mscorefonts-installer. I get a popup every few minutes:



When I run [FONT=Courier New]sudo apt-get install --reinstall ttf-mscorefonts-installer[/FONT] the issue becomes clear:

```
chris@chris-ubuntu:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcuda1-375 nvidia-opencl-icd-375
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 0 not to upgrade.
Need to get 0 B/27.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 182408 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.6ubuntu2_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.6ubuntu2) over (3.6ubuntu2) ...
Processing triggers for update-notifier-common (3.186) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe [652 B]
Err:1 http://downloads.sourceforge.net/corefonts/andale32.exe                  
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:0524fe42951adc3a7eb870e32f0920313c71f170c859b5f770d82b4ee111e970
  Hashes of received file:
   - SHA256:7a07d3f7cca5c0b38ca811984ef8da536da32932d68c1a6cce33ec2462b930bf
   - Filesize:652 [weak]
  Last modification reported: Thu, 01 Mar 2018 05:30:05 +0000
Fetched 652 B in 1s (367 B/s)                                                  
E: Failed to fetch https://downloads.sourceforge.net/#!/corefonts/andale32.exe  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:0524fe42951adc3a7eb870e32f0920313c71f170c859b5f770d82b4ee111e970
   Hashes of received file:
    - SHA256:7a07d3f7cca5c0b38ca811984ef8da536da32932d68c1a6cce33ec2462b930bf
    - Filesize:652 [weak]
   Last modification reported: Thu, 01 Mar 2018 05:30:05 +0000
E: Download Failed
Setting up ttf-mscorefonts-installer (3.6ubuntu2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu2) ...

```

It seems the file on SourceForge was updated yesterday, causing an error. I'm just using official Ubuntu repos, no PPAs:

```
chris@chris-ubuntu:~$ sudo apt-get update
Hit:1 http://gb.archive.ubuntu.com/ubuntu artful InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]   
Get:3 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]    
Hit:4 http://gb.archive.ubuntu.com/ubuntu artful-backports InRelease           
Fetched 157 kB in 0s (220 kB/s)                                                
Reading package lists... Done

```

Anyone know how to fix this or what to do? Thanks in advance :)

[URL="https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/1607535/comments/17"]https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/1607535/comments/17

[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/webdin32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/webdin32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/verdan32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/verdan32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/trebuc32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/trebuc32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/times32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/times32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/impact32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/impact32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/georgi32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/georgi32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/courie32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/courie32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/comic32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/comic32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/arialb32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/arialb32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/arial32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/arial32.exe/download)
[https://sourceforge.net/projects/corefonts/files/the%20fonts/final/andale32.exe/download](https://sourceforge.net/projects/corefonts/files/the%20fonts/final/andale32.exe/download)

[/URL]
sudo apt-get remove --purge ttf-mscorefonts-installer

Then in a terminal run:


 sudo apt-get install ttf-mscorefonts-installer #(this will fail again most likely)

sudo dpkg-reconfigure ttf-mscorefonts-installer

That should give you a "graphical" interface in the terminal.

Then point to the directory with downloaded files like /home//Downloads/mscorefonts

All 11 fonts downleded and pointed to folder/directory [ mscorefonts ] will be installed.

[URL="https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/1607535/comments/17"]
[/URL]

---

