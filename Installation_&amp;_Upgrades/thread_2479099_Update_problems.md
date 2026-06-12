---
title: "Update problems"
date: 2022-09-14
forum: Installation &amp; Upgrades
---

### Post by boobooboon on 2022-09-14
i got the same problem as above after installing brave browser it will not apt update even at the snap menu it just says internal error send info back if i cannot sort this out the only other way i can sort is to reinstall the whole package

oh yer the ver is 22.04 ubuntu

```

[sudo] password for bernard:
Ign:1 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Release amd64 (20220419) jammy InRelease
Err:2 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Release amd64 (20220419) jammy Release
Please use apt-cdrom to allow APT to recognise this CD-ROM. 'apt-get update' cannot be used to add new CD-ROMs
Hit:3*http://gb.archive.ubuntu.com/ubuntu*jammy InRelease
Ign:5*https://ppa.launchpadcontent.net/web...manager/ubuntu*jammy InRelease
Hit:6*https://brave-browser-apt-release.s3.brave.com*stable InRelease
Err:8*https://ppa.launchpadcontent.net/web...manager/ubuntu*jammy Release
404 Not Found [IP: 185.125.190.52 443]
Ign:4*https://dl.bintray.com/etcher/debian*stable InRelease
Hit:9*https://esm.ubuntu.com/infra/ubuntu*jammy-infra-security InRelease
Hit:10*https://esm.ubuntu.com/infra/ubuntu*jammy-infra-updates InRelease
Ign:7*https://www.virtualbox.org/virtualbox/debian*jammy InRelease
Ign:4*https://dl.bintray.com/etcher/debian*stable InRelease
Err:11*https://www.virtualbox.org/virtualbox/debian*jammy Release
404 Not Found [IP: 137.254.60.32 443]
Ign:4*https://dl.bintray.com/etcher/debian*stable InRelease
Err:4*https://dl.bintray.com/etcher/debian*stable InRelease
Could not handshake: The TLS connection was non-properly terminated. [IP: 18.193.9.131 443]
Reading package lists... Done
N: Ignoring file 'brave-jammy.list#' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: The repository 'cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Release amd64 (20220419) jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://ppa.launchpadcontent.net/webupd8team/y-ppa-manager/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://virtualbox.org/virtualbox/debian jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration de
```

---

### Post by QIII on 2022-09-14
Moved to its own thread from[ here]("https://ubuntuforums.org/showthread.php?t=2479027").

Please do not hijack the threads of other users.  You may think you have the "same problem", but similar symptoms may arise from entirely different underlying causes.

---

### Post by #&amp;thj^% on 2022-09-14
Thanks Qlll
@boobooboon please check that, /etc/apt/sources.list.d/brave-browser-release.list reads as such.
or just show us this please:
```
cat etc/apt/sources.list.d
```

---

### Post by grahammechanical on 2022-09-14
If we install the Brave browser through Ubuntu Software we get a snap packaged version which is not upgraded using the apt command.

We update snap packaged applications by running Software Updater. Snaps are refreshed (updated) automatically at the end of the update/upgrade process. Or, we open Ubuntu Software and the Updates tab will tell us if there are any updates to be downloaded. To update snap apps through the command line we run this command which will update all installed snaps.

```
sudo snap refresh
```

Regards

---

