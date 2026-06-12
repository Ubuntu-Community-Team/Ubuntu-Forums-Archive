---
title: "Kernel update, can't install latest version"
date: 2024-08-12
forum: Installation &amp; Upgrades
---

### Post by drumone on 2024-08-12
This last week I started having problems after Livepatch tried to do updates to the latest kernel version. If I allow the system to boot up normally, it goes to a black/blank screen and won't do anything else. If I boot into Linux 6.8.0-39 generic, everything is fine. I keep receiving warnings that installation or removal of packages has failed. Anyone have any ideas what's going on? I'm stumped.

I should add that I've tried to manually update and upgrade. My latest attempt to do so can be seen below.
```

drumone@Linux-Desktop-2021:~$ sudo apt-get update
[sudo] password for drumone: 
Hit:1 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu noble InRelease                                
Hit:3 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease                        
Hit:4 https://packages.microsoft.com/repos/code stable InRelease                         
Hit:5 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease                      
Hit:6 https://esm.ubuntu.com/infra/ubuntu noble-infra-updates InRelease
Hit:7 https://esm.ubuntu.com/infra/ubuntu noble-infra-security InRelease
Hit:8 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu noble InRelease
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://packages.microsoft.com/repos/code stable InRelease' doesn't support architecture 'i386'
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
N: Missing Signed-By in the sources.list(5) entry for 'https://packages.microsoft.com/repos/code'
drumone@Linux-Desktop-2021:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following upgrades have been deferred due to phasing:
  gnome-shell gnome-shell-common
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-6.8.0-40-generic (6.8.0-40.40) ...
Setting up linux-headers-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)

Building module:
Cleaning build area...
'make' all KVER=6.8.0-40-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for btusb: 4.0 not found
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/btusb/4.0/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for btusb(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-40-generic (--configure):
 installed linux-headers-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-6.8.0-40-generic; however:
  Package linux-headers-6.8.0-40-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.8.0-40.40); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                No apport report written because the error message indicates its a followup error from a previous failure.
                                Processing triggers for linux-image-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)

Building module:
Cleaning build area...
'make' all KVER=6.8.0-40-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for btusb: 4.0 not found
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/btusb/4.0/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for btusb(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.8.0-40-generic (--configure):
 installed linux-image-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-6.8.0-40-generic
 linux-headers-generic
 linux-generic
 linux-image-6.8.0-40-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by deadflowr on 2024-08-12
That's a very old kernel and no longer supported.
What version of Ubuntu is it?

---

### Post by drumone on 2024-08-12
My apologies, I should have added that too. I was incorrect about the kernel version (which I corrected above - 6.8.0-39). The OS is 24.04. I've been using Ubuntu for years, usually without problem. This one has me at a bit of a loss.

---

### Post by deadflowr on 2024-08-12
FTR, the kernel version posted in the original post was 6.0.39, so others won't think I'm nuts.

---

### Post by #&amp;thj^% on 2024-08-12
> **deadflowr said:**
> FTR, the kernel version posted in the original post was 6.0.39, so others won't think I'm nuts.

No one thinks your nuts, I currently have that title.....LOL
@drumone, if it were me I would also remove duplicate sources: in "/etc/apt/sources.list.d/"
```
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://packages.microsoft.com/repos/code stable InRelease' doesn't support architecture 'i386'
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
N: Missing Signed-By in the sources.list(5) entry for 'https://packages.microsoft.com/repos/code'
```

---

### Post by drumone on 2024-08-12
> **1fallen said:**
> 
@drumone, if it were me I would also remove duplicate sources: in "/etc/apt/sources.list.d/"


I would be happy to... if I knew how. ](*,) I saw that info, but wasn't quite sure what to do with it. I don't normally go around tweaking things without instructions from someone far more knowledgeable than myself. How would I go about safely identifying and removing the duplicates mentioned?

---

### Post by #&amp;thj^% on 2024-08-12
> **drumone said:**
> I would be happy to... if I knew how. ](*,) I saw that info, but wasn't quite sure what to do with it. I don't normally go around tweaking things without instructions from someone far more knowledgeable than myself. How would I go about safely identifying and removing the duplicates mentioned?

EDIT:LOL I made a mistake LOL
Use this please:
```
cd /etc/apt/sources.list.d && ls

```

---

### Post by drumone on 2024-08-12
```
drumone@Linux-Desktop-2021:~$ cd /etc/apt/sources.list.d && ls
amdgpu.list.distUpgrade
amdgpu.list.save
amdgpu-proprietary.list.distUpgrade
amdgpu-proprietary.list.save
amdgpu-proprietary.sources
amdgpu-proprietary.sources.save
amdgpu.sources
amdgpu.sources.save
archive_uri-https_repos_codelite_org_ubuntu_-jammy.list
archive_uri-https_repos_codelite_org_ubuntu_-jammy.list.save
deadsnakes-ubuntu-ppa-jammy.list.distUpgrade
deadsnakes-ubuntu-ppa-jammy.list.save
deadsnakes-ubuntu-ppa-jammy.sources
deadsnakes-ubuntu-ppa-jammy.sources.save
git-core-ubuntu-ppa-jammy.list.distUpgrade
git-core-ubuntu-ppa-jammy.list.save
git-core-ubuntu-ppa-jammy.sources
git-core-ubuntu-ppa-jammy.sources.save
gitlab_gitlab-ce.list.distUpgrade
gitlab_gitlab-ce.list.save
google-chrome.list.distUpgrade
google-chrome.list.save
google-chrome.sources
google-chrome.sources.save
rocm.list.distUpgrade
rocm.list.save
rocm.sources
rocm.sources.save
runner_gitlab-runner.list.distUpgrade
runner_gitlab-runner.list.save
teejee2008-ubuntu-timeshift-jammy.list.distUpgrade
teejee2008-ubuntu-timeshift-jammy.list.save
teejee2008-ubuntu-timeshift-jammy.sources
teejee2008-ubuntu-timeshift-jammy.sources.save
third-party.sources
third-party.sources.save
thopiekar-ubuntu-openrgb-jammy.list
thopiekar-ubuntu-openrgb-jammy.list.save
ubuntu-esm-infra.list.distUpgrade
ubuntu-esm-infra.list.save
ubuntu-esm-infra.sources
ubuntu-esm-infra.sources.save
ubuntu.sources
ubuntu.sources.save
vscode.list
vscode.list.distUpgrade
vscode.list.save
vscode.sources
vscode.sources.save
yannubuntu-ubuntu-boot-repair-noble.sources
yannubuntu-ubuntu-boot-repair-noble.sources.save


```

---

### Post by #&amp;thj^% on 2024-08-12
I haven't been on jammy for a few years now, so lets prepare for the worst, and back up that /directory first.
```
 sudo cp -a /etc/apt/sources.list.d  /etc/apt/sources.list.d.bk

```
Now will you please run this and tell me it works as in your first thread:
```
sudo apt update
```
I don't need to see it, just you confirm it is still identical to your first post.

---

### Post by drumone on 2024-08-12
Yup. It all looks the same as before. Lots of things configured multiple times.

---

### Post by #&amp;thj^% on 2024-08-12
Ok run this:
```
sudo rm -f /etc/apt/sources.list.d vscode.list.distUpgrade vscode.list.save vscode.sources vscode.sources.save 
```
Now I would like to see this please:
```
sudo apt clean && sudo apt update
```

---

### Post by drumone on 2024-08-12
No luck! See the output below:

```
drumone@Linux-Desktop-2021:~$ sudo rm -f /etc/apt/sources.list.d vscode.list.distUpgrade vscode.list.save vscode.sources vscode.sources.save
[sudo] password for drumone: 
rm: cannot remove '/etc/apt/sources.list.d': Is a directory
drumone@Linux-Desktop-2021:~$ 

sudo apt clean && sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu noble InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]               
Hit:3 http://security.ubuntu.com/ubuntu noble-security InRelease                         
Hit:4 https://packages.microsoft.com/repos/code stable InRelease                         
Hit:5 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease                      
Hit:6 https://esm.ubuntu.com/infra/ubuntu noble-infra-updates InRelease
Hit:7 https://esm.ubuntu.com/infra/ubuntu noble-infra-security InRelease
Hit:8 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu noble InRelease
Fetched 126 kB in 1s (156 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://packages.microsoft.com/repos/code stable InRelease' doesn't support architecture 'i386'
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/vscode.list:3 and /etc/apt/sources.list.d/vscode.sources:1
N: Missing Signed-By in the sources.list(5) entry for 'https://packages.microsoft.com/repos/code'

```

---

### Post by #&amp;thj^% on 2024-08-12
My God, I'm in rare form today, I have a pounding headache so not myself today.
Give me sec to fix that too...lol

---

### Post by drumone on 2024-08-12
@1fallen - You're helping *me*, so take care of yourself first! This problem can wait. I appreciate your help!

---

### Post by #&amp;thj^% on 2024-08-12
try this now:
```
sudo rm -f '/etc/apt/sources.list.d/vscode.list.' '/etc/apt/sources.list.d/distUpgrade vscode.list.save' '/etc/apt/sources.list.d/vscode.sources' '/etc/apt/sources.list.d/vscode.sources.save' 
```

---

### Post by drumone on 2024-08-12
No errors for the multi-config issue. I still can't get it to install 6.8.0-40. Next ideas?

```
drumone@Linux-Desktop-2021:~$ sudo rm -f '/etc/apt/sources.list.d/vscode.list.' '/etc/apt/sources.list.d/distUpgrade vscode.list.save' '/etc/apt/sources.list.d/vscode.sources' '/etc/apt/sources.list.d/vscode.sources.save'
[sudo] password for drumone: 
drumone@Linux-Desktop-2021:~$ sudo apt clean && sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://security.ubuntu.com/ubuntu noble-security InRelease                         
Hit:3 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease                        
Hit:4 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease                      
Hit:5 https://packages.microsoft.com/repos/code stable InRelease                         
Get:6 https://esm.ubuntu.com/infra/ubuntu noble-infra-updates InRelease [7,461 B]        
Get:7 https://esm.ubuntu.com/infra/ubuntu noble-infra-security InRelease [7,462 B]       
Hit:8 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu noble InRelease             
Fetched 14.9 kB in 2s (7,665 B/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
drumone@Linux-Desktop-2021:~$ apt list --upgradeable
Listing... Done
gnome-shell-common/noble-updates,noble-updates 46.0-0ubuntu6~24.04.1 all [upgradable from: 46.0-0ubuntu5.1]
gnome-shell/noble-updates 46.0-0ubuntu6~24.04.1 amd64 [upgradable from: 46.0-0ubuntu5.1]
drumone@Linux-Desktop-2021:~$ sudo apt-get update
Hit:1 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu noble InRelease                                
Hit:3 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease                        
Hit:4 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease                      
Hit:5 https://packages.microsoft.com/repos/code stable InRelease                         
Hit:6 https://esm.ubuntu.com/infra/ubuntu noble-infra-updates InRelease                  
Hit:7 https://esm.ubuntu.com/infra/ubuntu noble-infra-security InRelease             
Hit:8 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu noble InRelease
Reading package lists... Done
drumone@Linux-Desktop-2021:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following upgrades have been deferred due to phasing:
  gnome-shell gnome-shell-common
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-6.8.0-40-generic (6.8.0-40.40) ...
Setting up linux-headers-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)

Building module:
Cleaning build area...
'make' all KVER=6.8.0-40-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for btusb: 4.0 not found
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/btusb/4.0/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for btusb(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-40-generic (--configure):
 installed linux-headers-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-6.8.0-40-generic; however:
  Package linux-headers-6.8.0-40-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.8.0-40.40); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                No apport report written because the error message indicates its a followup error from a previous failure.
                                Processing triggers for linux-image-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)

Building module:
Cleaning build area...
'make' all KVER=6.8.0-40-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for btusb: 4.0 not found
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/btusb/4.0/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for btusb(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.8.0-40-generic (--configure):
 installed linux-image-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-6.8.0-40-generic
 linux-headers-generic
 linux-generic
 linux-image-6.8.0-40-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by #&amp;thj^% on 2024-08-12
what will this show:
```
apt policy linux-headers-generic 

```
Hell while we're here also this please:
```
apt list --installed | grep -e linux-image -e linux-headers -e linux-modules

```

---

### Post by drumone on 2024-08-12
```
drumone@Linux-Desktop-2021:~$ 

apt policy linux-headers-generic
linux-headers-generic:
  Installed: 6.8.0-40.40
  Candidate: 6.8.0-40.40
  Version table:
 *** 6.8.0-40.40 500
        500 http://us.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages
        100 /var/lib/dpkg/status
     6.8.0-31.31 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
drumone@Linux-Desktop-2021:~$ 

```

```
drumone@Linux-Desktop-2021:~$ apt list --installed | grep -e linux-image -e linux-headers -e linux-modules

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-headers-6.8.0-39-generic/noble-updates,noble-security,now 6.8.0-39.39 amd64 [installed,automatic]
linux-headers-6.8.0-39/noble-updates,noble-updates,noble-security,noble-security,now 6.8.0-39.39 all [installed,automatic]
linux-headers-6.8.0-40-generic/noble-updates,noble-security,now 6.8.0-40.40 amd64 [installed,automatic]
linux-headers-6.8.0-40/noble-updates,noble-updates,noble-security,noble-security,now 6.8.0-40.40 all [installed,automatic]
linux-headers-generic/noble-updates,noble-security,now 6.8.0-40.40 amd64 [installed,automatic]
linux-image-6.8.0-39-generic/noble-updates,noble-security,now 6.8.0-39.39 amd64 [installed,automatic]
linux-image-6.8.0-40-generic/noble-updates,noble-security,now 6.8.0-40.40 amd64 [installed,automatic]
linux-image-generic/noble-updates,noble-security,now 6.8.0-40.40 amd64 [installed,automatic]
linux-modules-6.8.0-39-generic/noble-updates,noble-security,now 6.8.0-39.39 amd64 [installed,automatic]
linux-modules-6.8.0-40-generic/noble-updates,noble-security,now 6.8.0-40.40 amd64 [installed,automatic]
linux-modules-extra-6.8.0-39-generic/noble-updates,noble-security,now 6.8.0-39.39 amd64 [installed,automatic]
linux-modules-extra-6.8.0-40-generic/noble-updates,noble-security,now 6.8.0-40.40 amd64 [installed,automatic]

```

---

### Post by #&amp;thj^% on 2024-08-13
Well, the REMAKE_INITRD variable is deprecated, and that's correct, but this means you have some particular configuration file which is still using it, and not dkms_autoinstaller itself. 
Please show this:
```
cd /usr/src/ && ls
```

I need to see whats is here:
```
 cd /var/lib/dkms/ && ls

```

Also do you why this is needed?
```
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/[COLOR="#FF0000"]btusb/4[/COLOR].0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/[COLOR="#FF0000"]btusb/4.0[/COLOR]/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
```
And one more:
```
dkms status

```

---

### Post by drumone on 2024-08-13
Replying in order of the code requests:

```
btusb-4.0        linux-headers-6.8.0-39-generic    linux-headers-6.8.0-40-generic
linux-headers-6.8.0-39    linux-headers-6.8.0-40        python3.12

```

```
cd /var/lib/dkms/ && ls
```

As for the deprecated stuff... I just figured out what it's related to!!! Bluetooth! I came across a code fix when I was having issues getting bluetooth to work. This is what I found/used:
```
   	 	 	 	  [LEFT] sudo rfkill unblock all  [/LEFT] [LEFT] sudo hciconfig hci0 down
[/LEFT] [LEFT]sudo rmmod btusb
[/LEFT] [LEFT]sudo modprobe btusb
[/LEFT] [LEFT]sudo hciconfig hci0 up
[/LEFT]  
```

I am more than happy to get rid of anything related to Bluetooth at this point. It doesn't work consistently and I no longer need it.

```
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
btusb/4.0, 6.5.0-35-generic, x86_64: installed (WARNING! Diff between built and installed module!)
btusb/4.0, 6.5.0-41-generic, x86_64: installed (WARNING! Diff between built and installed module!)
btusb/4.0, 6.8.0-36-generic, x86_64: installed (WARNING! Diff between built and installed module!)
btusb/4.0, 6.8.0-38-generic, x86_64: installed (WARNING! Diff between built and installed module!)
btusb/4.0, 6.8.0-39-generic, x86_64: installed (WARNING! Diff between built and installed module!)

```

---

### Post by #&amp;thj^% on 2024-08-13
For myself if I wanted to ensure a good upgrade 
```
sudo apt-get purge blueman bluez-utils bluez bluetooth && sudo apt autoremove && sudo apt autoclean
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'bluez-utils' is not installed, so not removed
Package 'bluetooth' is not installed, so not removed
The following packages will be REMOVED:
  blueman* bluez*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 


```
Please look real good at what is being removed first. :)

---

### Post by drumone on 2024-08-13
Tried that... see below. I think the brick wall is getting thicker. ](*,)

```
sudo apt-get purge blueman bluez-utils bluez bluetooth && sudo apt autoremove && sudo apt autoclean

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'bluez-utils' is not installed, so not removed
The following package was automatically installed and is no longer required:
  indicator-common
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  blueman* bluetooth* bluez* bluez-btsco* gnome-bluetooth* gnome-bluetooth-sendto*
  indicator-bluetooth*
0 upgraded, 0 newly installed, 7 to remove and 2 not upgraded.
4 not fully installed or removed.
After this operation, 8,832 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 268077 files and directories currently installed.)
Removing blueman (2.3.5-3build1) ...
Removing bluetooth (5.72-0ubuntu5) ...
Removing indicator-bluetooth (0.0.6+17.10.20170605-0ubuntu5) ...
Removing bluez-btsco (1:0.50-0ubuntu9) ...
Removing gnome-bluetooth (42~3.34.5-13build3) ...
Removing gnome-bluetooth-sendto (46.0-1build1) ...
Removing bluez (5.72-0ubuntu5) ...
Setting up linux-image-6.8.0-40-generic (6.8.0-40.40) ...
Setting up linux-headers-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)

Building module:
Cleaning build area...
'make' all KVER=6.8.0-40-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for btusb: 4.0 not found
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/btusb/4.0/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for btusb(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-40-generic (--configure):
 installed linux-headers-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-6.8.0-40-generic; however:
  Package linux-headers-6.8.0-40-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.8.0-40.40); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                No apport report written because the error message indicates its a followup error from a previous failure.
                                Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for libglib2.0-0t64:amd64 (2.80.0-6ubuntu3.1) ...
Processing triggers for dbus (1.14.10-4ubuntu4) ...
Processing triggers for desktop-file-utils (0.27-2build1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
Errors were encountered while processing:
 linux-headers-6.8.0-40-generic
 linux-headers-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by #&amp;thj^% on 2024-08-13
Nah we will get past it. :)
let me see this please:
```
less /var/lib/dkms/btusb/4.0/source/dkms.conf

```

---

### Post by drumone on 2024-08-13
```
MAKE="'make' all KVER=${kernelver}"
CLEAN="make clean"
BUILT_MODULE_NAME=btusb
BUILT_MODULE_NAME[1]=ath3k
DEST_MODULE_NAME="btusb"
DEST_MODULE_NAME[1]="ath3k"
DEST_MODULE_LOCATION="/updates"
DEST_MODULE_LOCATION[1]="/updates"
PACKAGE_NAME=btusb
PACKAGE_VERSION=4.0
REMAKE_INITRD=yes
AUTOINSTALL=yes

```

---

### Post by #&amp;thj^% on 2024-08-13
Here it is>>"AUTOINSTALL=yes"
Before I start swinging any hammers here, first give this a try:
```
sudo nano /var/lib/dkms/btusb/4.0/source/dkms.conf
```
Change that line I show to:
```
AUTOINSTALL=no
```
Save and exit, now upgrade with:
```
sudo apt install -f
```
Fingers Crossed

---

### Post by drumone on 2024-08-13
Ummm.... nope.  I even double checked the file to make sure it was changed properly.

```
drumone@Linux-Desktop-2021:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  indicator-common
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-headers-6.8.0-40-generic (6.8.0-40.40) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)

Building module:
Cleaning build area...
'make' all KVER=6.8.0-40-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for btusb: 4.0 not found
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/btusb/4.0/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for btusb(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-40-generic (--configure):
 installed linux-headers-6.8.0-40-generic package post-installation script subprocess returned error exit status 11
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-6.8.0-40-generic; however:
  Package linux-headers-6.8.0-40-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.8.0-40.40); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a p
revious failure.
                No apport report written because the error message indicates its a followu
p error from a previous failure.
                                Processing triggers for linux-image-6.8.0-40-generic (6.8.
0-40.40) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-40-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/btusb/4.0/source/dkms.conf)

Building module:
Cleaning build area...
'make' all KVER=6.8.0-40-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for btusb: 4.0 not found
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/btusb/4.0/build/make.log for more information.
dkms autoinstall on 6.8.0-40-generic/x86_64 failed for btusb(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-40-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.8.0-40-generic (--configure):
 installed linux-image-6.8.0-40-generic package post-installation script subprocess return
ed error exit status 11
No apport report written because MaxReports is reached already
                                                              Errors were encountered whil
e processing:
 linux-headers-6.8.0-40-generic
 linux-headers-generic
 linux-generic
 linux-image-6.8.0-40-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by #&amp;thj^% on 2024-08-13
please show me this:
```
apt policy btusb
```
if nothing try this:
```
apt search btusb
```
If there is still nothing shown,,,,Hammer Time...LOL
```
sudo rm -rf /var/lib/dkms/btusb/4.0/source/dkms.conf
```

---

### Post by drumone on 2024-08-13
Well, in keeping with the music theme.... Sledge Hammer! Rebooting now and hoping it worked.

---

### Post by drumone on 2024-08-13
Aaaaaaaaaand... Success!! \\:D/=d>  Thank you @1fallen!!!  I greatly appreciate your time and effort to help me with this.

---

### Post by #&amp;thj^% on 2024-08-13
Go Team! :)
lets not forget to clean up a bit:
```
sudo rm -f /etc/apt/sources.list.d.bk
```
You now seem to have a good source list so the back-up can be trashed

And you can if(?) you want re-install bluetooth again

---

### Post by drumone on 2024-08-13
The system response to cleaning up.  

```
rm: cannot remove '/etc/apt/sources.list.d.bk': Is a directory
```

LOL Oh well. I think I'm done with Bluetooth for a while. I don't need it for the wireless headphones now that I have a separate office space.

---

### Post by #&amp;thj^% on 2024-08-13
Weird mine:
```
&#9492;&#9472;> sudo rm -f /etc/apt/sources.list.d.bk
[sudo] password for me: 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> 

```

---

### Post by drumone on 2024-08-13
No big deal for me. If I can't see it and it doesn't screw with anything else, I'm good. :P

---

### Post by firetiger1234 on 2024-09-13
Following the AMDGPU uninstall steps on this site solved my 6.8.0-44-generic install issue.


[https://amdgpu-install.readthedocs.io/en/latest/install-installing.html#uninstalling-the-amdgpu-stack](https://amdgpu-install.readthedocs.io/en/latest/install-installing.html#uninstalling-the-amdgpu-stack)

---

### Post by chrisnd2 on 2024-10-20
Hi, Just for the record I have much the same problem with the 'Black Screen of Death' since the Kernel updated from 6.8.0-45 to -47.
I get very similar error messages. Like you I can get the machine to boot if I use 6.8.0-44 from grub.  (For some reason -45 is not in the list.  I don't know why - it appears as a 'leftover' if I look at things with Symantec. However, I can't remove anything without getting in the same loop as yours)

If I could remove 6.8.0-47 and revert permanently to my previous version I would be happy - but I haven't found a way to do this. Yet.

Chris

---

