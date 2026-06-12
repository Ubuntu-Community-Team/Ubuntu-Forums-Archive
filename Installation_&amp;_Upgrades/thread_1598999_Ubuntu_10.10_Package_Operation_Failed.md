---
title: "Ubuntu 10.10: Package Operation Failed"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by dmjones63 on 2010-10-17
I've just installed Ubuntu v10.10 on my laptop that previously had v10.04 installed on it.Now whenever I try to install ANY software, I get a message sayinh that the package operation failed. 

For example, Update Manager stops with the following:

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
tar: Unexpected EOF in archive 
tar: Unexpected EOF in archive 
tar: Error is not recoverable: exiting now 
dpkg-deb: subprocess tar returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.35-22-generic_2.6.35-22.34_i386.deb (--unpack): 
 subprocess dpkg-deb --control returned error exit status 2 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
tar: Unexpected EOF in archive 
tar: Unexpected EOF in archive 
tar: Error is not recoverable: exiting now 
dpkg-deb: subprocess tar returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/tzdata_2010m-0ubuntu0.10.10_all.deb (--unpack): 
 subprocess dpkg-deb --control returned error exit status 2 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-image-2.6.35-22-generic_2.6.35-22.34_i386.deb 
 /var/cache/apt/archives/tzdata_2010m-0ubuntu0.10.10_all.deb 

Unfortunately, I'm not that familiar with these types of messages and I'm having great difficulty trying to track down the cause of the problem.

If there's anyone out there who can offer some assistance, I'd very much appreciate it.

---

### Post by 73ckn797 on 2010-10-17
I was having a similar issue. From terminal enter:
```
sudo apt-get clean
```
That will clear all of the downloaded packages. Then go to "Update Manager" and try again. There is probably a bad package causing the errors.

---

### Post by dmjones63 on 2010-10-17
Thanks for the prompt reply.

I've tried 'sudo apt-get clean' as you suggested. This made now difference.

Having read through the original error, I thought I'd try not installing the 2 packages that seemed to be causing the issue, ie, linux-image-2.6.35-22-generic_2.6.35-22.34_i386.deb and tzdata_2010m-0ubuntu0.10.10_all.deb by removing the 'ticks' from the Update Manager list. However, when I did this and tried again it got this error:

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 118295 files and directories currently installed.) 
Preparing to replace libvte-common 1:0.26.0-0ubuntu1 (using .../libvte-common_1%3a0.26.0-0ubuntu2_all.deb) ... 
Unpacking replacement libvte-common ... 
dpkg: error processing /var/cache/apt/archives/libvte-common_1%3a0.26.0-0ubuntu2_all.deb (--unpack): 
 corrupted filesystem tarfile - corrupted package archive 
No apport report written because MaxReports is reached already
Preparing to replace libvte9 1:0.26.0-0ubuntu1 (using .../libvte9_1%3a0.26.0-0ubuntu2_i386.deb) ... 
Unpacking replacement libvte9 ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
dpkg-deb: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/libvte9_1%3a0.26.0-0ubuntu2_i386.deb (--unpack): 
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libvte.so.9.2600.0' 
No apport report written because MaxReports is reached already
Preparing to replace python-vte 1:0.26.0-0ubuntu1 (using .../python-vte_1%3a0.26.0-0ubuntu2_i386.deb) ... 
Unpacking replacement python-vte ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
dpkg-deb: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/python-vte_1%3a0.26.0-0ubuntu2_i386.deb (--unpack): 
 short read on buffer copy for backend dpkg-deb during `./usr/lib/pyshared/python2.6/gtk-2.0/vtemodule.so' 
No apport report written because MaxReports is reached already
Preparing to replace update-manager 1:0.142.19 (using .../update-manager_1%3a0.142.20_all.deb) ... 
Unpacking replacement update-manager ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
dpkg-deb: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.142.20_all.deb (--unpack): 
 short read on buffer copy for backend dpkg-deb during `./usr/lib/update-manager/check-new-release-gtk' 
No apport report written because MaxReports is reached already
Preparing to replace update-manager-core 1:0.142.19 (using .../update-manager-core_1%3a0.142.20_i386.deb) ... 
Unpacking replacement update-manager-core ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid literal/lengths set' 
dpkg-deb: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.142.20_i386.deb (--unpack): 
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2 
No apport report written because MaxReports is reached already
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
tar: Unexpected EOF in archive 
tar: Unexpected EOF in archive 
tar: Error is not recoverable: exiting now 
dpkg-deb: subprocess tar returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.35-22_2.6.35-22.34_all.deb (--unpack): 
 subprocess dpkg-deb --control returned error exit status 2 
No apport report written because MaxReports is reached already
tar: Skipping to next header 
tar: Exiting with failure status due to previous errors 
dpkg-deb: subprocess tar returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.34_i386.deb (--unpack): 
 subprocess dpkg-deb --control returned error exit status 2 
No apport report written because MaxReports is reached already
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
tar: Unexpected EOF in archive 
tar: Unexpected EOF in archive 
tar: Error is not recoverable: exiting now 
dpkg-deb: subprocess tar returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/linux-libc-dev_2.6.35-1022.34_i386.deb (--unpack): 
 subprocess dpkg-deb --control returned error exit status 2 
No apport report written because MaxReports is reached already
Processing triggers for python-support ... 
Processing triggers for python-central ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libvte-common_1%3a0.26.0-0ubuntu2_all.deb 
 /var/cache/apt/archives/libvte9_1%3a0.26.0-0ubuntu2_i386.deb 
 /var/cache/apt/archives/python-vte_1%3a0.26.0-0ubuntu2_i386.deb 
 /var/cache/apt/archives/update-manager_1%3a0.142.20_all.deb 
 /var/cache/apt/archives/update-manager-core_1%3a0.142.20_i386.deb 
 /var/cache/apt/archives/linux-headers-2.6.35-22_2.6.35-22.34_all.deb 
 /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.34_i386.deb 
 /var/cache/apt/archives/linux-libc-dev_2.6.35-1022.34_i386.deb

HELP!

---

### Post by 73ckn797 on 2010-10-17
Go to the folder that was indicated in:
```
/var/cache/apt/archives/libvte-common_1%3a0.26.0-0ubuntu2_all.deb 
 /var/cache/apt/archives/libvte9_1%3a0.26.0-0ubuntu2_i386.deb 
 /var/cache/apt/archives/python-vte_1%3a0.26.0-0ubuntu2_i386.deb 
 /var/cache/apt/archives/update-manager_1%3a0.142.20_all.deb 
 /var/cache/apt/archives/update-manager-core_1%3a0.142.20_i386.deb 
 /var/cache/apt/archives/linux-headers-2.6.35-22_2.6.35-22.34_all.deb 
 /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.34_i386.deb 
 /var/cache/apt/archives/linux-libc-dev_2.6.35-1022.34_i386.deb
```

Delete those packages manually. You will likely have to open Nautilus via terminal to have root access.
```
sudo nautilus
```

Try that at least. That is what I did with my issue. Many of the things I see in your errors were similar to mine. May want to restart the computer after clearing out the cache.

---

### Post by dmjones63 on 2010-10-17
Once again, thanks for the reply. I have done as you suggested, restarted the laptop, but it has made no difference. Error message once again:

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
tar: Unexpected EOF in archive 
tar: Unexpected EOF in archive 
tar: Error is not recoverable: exiting now 
dpkg-deb: subprocess tar returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.35-22-generic_2.6.35-22.34_i386.deb (--unpack): 
 subprocess dpkg-deb --control returned error exit status 2 
No apport report written because MaxReports is reached already
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
tar: Unexpected EOF in archive 
tar: Unexpected EOF in archive 
tar: Error is not recoverable: exiting now 
dpkg-deb: subprocess tar returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/tzdata_2010m-0ubuntu0.10.10_all.deb (--unpack): 
 subprocess dpkg-deb --control returned error exit status 2 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-image-2.6.35-22-generic_2.6.35-22.34_i386.deb 
 /var/cache/apt/archives/tzdata_2010m-0ubuntu0.10.10_all.deb 


Do you have any more ideas or suggestions?
Thanks

---

### Post by ray-w on 2010-10-17
I had the very same problem with 10.10 and it was caused by my system clock being incorrectly set!

I played around with the date and time settings to correct it and the updates/other software magically installed themselves. (Actually I'm running Ubuntu inside VB and my Windows clock was all out of whack too so I had to fix that one first).

Hope this helps,

---

### Post by dmjones63 on 2010-10-17
Thanks for the post Ray but as my clock is set correctly, I'm still no further forward!

---

### Post by dmjones63 on 2010-10-17
Thanks everyone for all the help - finally got around the issue by re-formatting the hard drive and installing v10.10 from scratch. Everything works fine now. But it doesn't explain why it didn't work first time around. C'est la vie!

---

### Post by AgenT on 2010-10-20
Here is how I solved this problem. 

**1)** Close any package manager, this includes Synaptic, Update Manager and Software Center.
**2)** Open terminal and execute the following commands (press Enter after every line to execute):
```
sudo pkill apt
sudo apt-get clean
sudo pkill apt
```**3)** Start Update Manager and hit "Check".
**3a)** If you have any updates, install the updates.
**4)** Close Update Manager.

WARNING: I received this problem when doing an update, even worse, when doing a kernel update. This problem forced only some of the packages to install so a reboot, as some suggest, would spell disaster in my case. Fix your problem before rebooting!

---

### Post by Crazedpsyc on 2010-11-03
I just fixed that same problem and it was caused by ESET NOD32 antivirus!

---

### Post by RoyAkkerman on 2010-11-24
> **Crazedpsyc said:**
> I just fixed that same problem and it was caused by ESET NOD32 antivirus!

Just verified. ESET NOD32 Antivirus for linux (beta) causing the issue.

After uninstalling av, 
sudo apt-get autoremove -f 
sudo apt-get update
sudo apt-get upgrade
work fine.

You should also try killing esets_daemon instead of uninstalling.

---

### Post by cocoa117 on 2010-11-26
thanx, I had similar issue, and I use nod32 beta for Linux. After uninstall and remove the daemon, system functioning fine.

---

### Post by zr0gee on 2010-12-05
> **Crazedpsyc said:**
> I just fixed that same problem and it was caused by ESET NOD32 antivirus!

This just saved me from a MAJOR re-install headache. I couldn't for the life of me figure out what was messing with my system upgrade, and killing the eset-daemon solved all my problems. Thanks :)

The only reason I was running an anti-virus daemon in the first place was because my workstation is sitting on a network with M$ clients, and I wanted to eliminate the risk of spreading virus onto them, however unlikely that may have been. 

Now I am determined to let these M$ clients fight their own battles, and let the digital evolution run its course, instead of having my beloved linux workstation filter out any nasty coding that might infect their fragile file systems :evil:

---

### Post by deadite66 on 2011-01-12
glad i found this thread, got stung by nod32 too.

---

### Post by deadite66 on 2011-01-12
double post

---

### Post by ch_animesh on 2011-01-22
[FONT="Comic Sans MS"]hi i had same problem when i was trying to install netbeans ide version 6.9 in my laptop i am getting PACKAGE OPERATION FAILED and the following output[/FONT]


installArchives() failed: Selecting previously deselected package netbeans.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 176145 files and directories currently installed.)
Unpacking netbeans (from .../netbeans_6.9-0ubuntu2_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up netbeans (6.9-0ubuntu2) ...
Errors were encountered while processing:
 firmware-b43-installer
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1

---

