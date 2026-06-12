---
title: "Nvidia/Envy Problems"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by krj81 on 2010-02-15
Hi folks.  I'm banging my head with this problem.  I can't get my nvidia drivers working.

Trying to install Envyng after failing to activate drivers via the Administration -> Hardware Drivers menu, I get this:

```
krjackson@home:~$ sudo apt-get install envyng-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  envyng-core
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/122kB of archives.
After this operation, 930kB of additional disk space will be used.
Selecting previously deselected package envyng-core.
(Reading database ... 198339 files and directories currently installed.)
Unpacking envyng-core (from .../envyng-core_2.0.1ubuntu3_all.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Setting up nvidia-173-kernel-source (173.14.20-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing nvidia-173-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of nvidia-glx-173:
 nvidia-glx-173 depends on nvidia-173-kernel-source (>= 173.14.20); however:
  Package nvidia-173-kernel-source is not configured yet.
dpkg: error processing nvidia-glx-173 (--configure):
 dependency problems - leaving unconfigured
Setting up envyng-core (2.0.1ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Errors were encountered while processing:
 nvidia-173-kernel-source
 nvidia-glx-173
E: Sub-process /usr/bin/dpkg returned an error code (1)
krjackson@home:~$ sudo dpkg --configure nvidia-173-kernel-source
Setting up nvidia-173-kernel-source (173.14.20-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing nvidia-173-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-173-kernel-source
```Being an idiot when I get under the hood with Linux, I have no idea how to fix this.  After searching the forums and Google, I'm still at a loss.  I can't remove the packages with Synaptic or the command-line. 

Any assistance you gurus can offer will be much appreciated.

Thanks.

---

### Post by ahso4271 on 2010-02-16
Read.....[FONT=monospace]something is not installed[/FONT] 
nvidia-173-kernel-source

---

### Post by krj81 on 2010-02-16
> Read.....[FONT=monospace]something is not installed[/FONT] 
nvidia-173-kernel-source     Well, that is only partially true.  It sees it as not installed, but when I try to install that package it fails because of the post-installation script error.  It is partially installed though.  I can't remove it through apt or Synaptic for the same error.  However, it is all moot at this point.

In an aggravated and rum-induced moment of bravery/stupidity, I just manually searched for and deleted every file with 'nvidia' in the file name.  I then installed envy, but it encountered an error too, probably because of the indiscriminate nvidia file deletion.

So, I downloaded (again) the nvidia driver installer and ran it.  It encountered no error and works great.  I'd still like to know what went wonky before though...

---

