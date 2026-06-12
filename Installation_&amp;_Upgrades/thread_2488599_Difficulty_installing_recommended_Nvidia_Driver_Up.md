---
title: "Difficulty installing recommended Nvidia Driver Upgrade - Messy Update - Next Steps?"
date: 2023-07-10
forum: Installation &amp; Upgrades
---

### Post by mokkers on 2023-07-10
Hi there very new to linux. Just wanted to share some trouble I had with an upgrade and seek some advice on best next steps to avoid system breakage. 

An application in ubuntu (update manager I think) recommended I install the latest nvidia drivers. I proceeded.The screen went blank and my system fan went into overdrive... I left it for about an hour hoping the update would complete but eventually I found myself in what seemed like a terminal or recovery mode. I couldn't force a reboot because of updates holding locks from apt and dpkg.

Looking at the logs it seemed that the system was hung around the nvidia driver upgrades due to some dependency issues.

(I later pulled this from the logs:
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.140ubuntu13.1) ...
update-initramfs: Generating /boot/initrd.img-6.2.0-10011-tuxedo
I: The initramfs will attempt to resume from /dev/dm-2
I: (/dev/mapper/system-swap)
I: Set the RESUME variable to override this.
Errors were encountered while processing:
 nvidia-dkms-535
 nvidia-dkms-530
 nvidia-driver-535
nvidia-driver-530
)

I wanted to run dpkg -configure -a but couldn't because of the locks.


I ended up killing the various pid and ran reboot hoping to run dpkg -configure -a once in the terminal again but I just got a black screen and eventually a message:
"INFO: task nv_queue:421 blocked for more than 845 seconds."

Eventually I resorted to hard rebooting the machine, and to my great relief ubuntu loaded as normal.. 

I checked apt upgrade (but didn't press Y) and it reports that those 4 packages are not fully installed or removed... 

I figure I should probably run dpkg -configure -a.. but I am a bit terrified of breaking my install somehow.

I am not sure what is best practice here. I have temporarily switched off all updates, just to avoid me finding myself in this situation again. Any advice on what I should do to clean up this messed up update without compromising my system would be greatly appreciated.

Thank you

lsb_release -a 
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.2 LTS
Release:	22.04
Codename:	jammy

uname -a
Linux sam-laptop 6.2.0-10011-tuxedo #14 SMP PREEMPT_DYNAMIC Wed Jun 28 18:29:09 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ubfan1 on 2023-07-10
What video driver are you running before the upgrade attempt and now?  None of those packages have a phased hold on them (on my machine), but the 535 has superceded the 530 package, yet I still see some Nvidia 530 packages on my Ubuntu 22.04.  Maybe try installing the 530 packages first, then try to install the 535 packages.

---

### Post by #&amp;thj^% on 2023-07-10
I ran into this as well with out the [PPA active ]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa")
I purged all nVidia related packages and rebooted also ran "dpkg -configure -a." and after getting a happy package-manager
EDIT: My removal process runs exactly as this:
```
sudo apt autoremove --purge nvidia*
```
I simply re-installed my Driver version of choice:
```
sudo apt install nvidia-driver-535 nvidia-dkms-535
### or the older version
sudo apt install nvidia-driver-530 nvidia-dkms-530
```
When it get all done and error free I reboot to my new driver
```
apt policy nvidia-driver-535 nvidia-dkms-535
nvidia-driver-535:
  Installed: 535.54.03-0ubuntu0.23.04.2
  Candidate: 535.54.03-0ubuntu0.23.04.2
  Version table:
 *** 535.54.03-0ubuntu0.23.04.2 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/restricted amd64 Packages
        100 /var/lib/dpkg/status
nvidia-dkms-535:
  Installed: 535.54.03-0ubuntu0.23.04.2
  Candidate: 535.54.03-0ubuntu0.23.04.2
  Version table:
 *** 535.54.03-0ubuntu0.23.04.2 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/restricted amd64 Packages
        100 /var/lib/dpkg/status

```
I find the driver straight from "ubuntu lunar-updates/restricted" slightly more buggy. (I just call them as I see them)

---

### Post by mokkers on 2023-07-11
Thanks. I think you might have been right here.

Quick look at sudo apt show nvidia-dkms-530:


Package: nvidia-dkms-530
Version: 535.54.03-0ubuntu0.22.04.1
Priority: optional
Section: restricted/libs
Source: nvidia-graphics-drivers-535
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 32.8 kB
_Depends: nvidia-dkms-535_
Homepage: [http://www.nvidia.com](http://www.nvidia.com)
Download-Size: 10.3 kB
APT-Manual-Installed: yes
APT-Sources: [https://mirrors.tuxedocomputers.com/ubuntu/mirror/security.ubuntu.com/ubuntu](https://mirrors.tuxedocomputers.com/ubuntu/mirror/security.ubuntu.com/ubuntu) jammy-security/restricted amd64 Packages
Description: Transitional package for nvidia-dkms-535
 This is a transitional package for nvidia-dkms-535, and can be
 safely removed after the installation is complete.

Anyway I just ran dpkg --configure -a and it seems to have resolved.

---

