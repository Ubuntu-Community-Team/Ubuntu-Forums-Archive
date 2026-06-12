---
title: "Dell XPS upgrade"
date: 2022-07-16
forum: Installation &amp; Upgrades
---

### Post by zkab on 2022-07-16
I have just received my Dell XPS 13 Plus (9320) with Ubuntu 20.04 LTS preinstalled.
What I did whas to upgrade it to 22.04 LTS and followed [https://askubuntu.com/questions/1341276/no-dell-linux-assistant-program-upgrade](https://askubuntu.com/questions/1341276/no-dell-linux-assistant-program-upgrade)
The upgrade went OK and I rebooted.
When I then remote SSH to XPS there was messages.
```

2 devices have a firmware upgrade available.
Run `fwupdmgr get-upgrades` for more information.

oden@rk-dell:~$ fwupdmgr get-upgrades
Devices with no available firmware updates: 
 • VEN 04F3:00 04F3:31D1
 • TPM 2.0
 • UEFI Device Firmware
 • UEFI Device Firmware
 • UEFI dbx
 • USB4 Retimer
 • USB4 host controller
 • USB4 host controller
Devices with the latest available firmware version:
 • RTS5413 in Dell dock
 • RTS5********************************************************487 in Dell dock
 • VMM5331 in Dell dock
 • PM9A1 NVMe Samsung 1024GB
 • System Firmware
 • Thunderbolt controller in Dell dock
XPS 9320
&#9474;
&#9500;&#9472;Package level of Dell dock:
&#9474; &#9474;   Device ID:          073624c16dd99abe01ba1da223a70321e4f29beb
&#9474; &#9474;   Summary:            A representation of dock update status
&#9474; &#9474;   Current version:    01.00.25.00
&#9474; &#9474;   Vendor:             Dell Inc. (USB:0x413C)
&#9474; &#9474;   Install Duration:   5 seconds
&#9474; &#9474;   GUID:               8ceeeffd-51b6-580c-9b75-69143227aff8
&#9474; &#9474;   Device Flags:       • Updatable
&#9474; &#9474;                       • Supported on remote server
&#9474; &#9474;                       • Device can recover flash failures
&#9474; &#9474;                       • Device is usable for the duration of the update
&#9474; &#9474; 
&#9474; &#9492;&#9472;WD19/WD22/HD22 Series Dock:
&#9474;       New version:      01.00.25.01
&#9474;       Remote ID:        lvfs
&#9474;       Release ID:       13766
&#9474;       Summary:          Firmware package version for WD19 Series Dock
&#9474;       License:          Proprietary
&#9474;       Size:             24 bytes
&#9474;       Created:          2022-06-08
&#9474;       Urgency:          High
&#9474;       Vendor:           Dell
&#9474;       Duration:         5 seconds
&#9474;       Release Flags:    • Is upgrade
&#9474;       Description:      
&#9474;       -Update the firmware package version of Dell docking station's composite devices.
&#9474;     
&#9492;&#9472;WD19TB:
  &#9474;   Device ID:          570867f4ddda9915445da59bd85cd0e0e507270e
  &#9474;   Summary:            High performance dock
  &#9474;   Current version:    01.00.00.05
  &#9474;   Vendor:             Dell Inc. (USB:0x413C)
  &#9474;   Install Duration:   1 minute
  &#9474;   GUID:               cd357cf1-40b2-5d87-b8df-bb2dd82774aa
  &#9474;   Device Flags:       • Updatable
  &#9474;                       • Supported on remote server
  &#9474;                       • Device stages updates
  &#9474;                       • Device can recover flash failures
  &#9474;                       • Device is usable for the duration of the update
  &#9474; 
  &#9492;&#9472;WD19/WD22 EC:
        New version:      01.01.00.03
        Remote ID:        lvfs
        Release ID:       13769
        Summary:          Firmware update for WD19/WD22 EC
        License:          Proprietary
        Size:             131,0 kB
        Created:          2022-06-08
        Urgency:          High
        Vendor:           Dell
        Duration:         1 minute
        Release Flags:    • Is upgrade
        Description:      
        -Improved the display compatibility between systems and monitors.

```

I also made 'sudo apt update' and got some errors:
```
oden@rk-dell:~$ sudo apt update
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dell.archive.canonical.com jammy InRelease                                                                
Hit:3 http://oem.archive.canonical.com jammy InRelease                                                                 
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease                                           
Hit:5 http://archive.ubuntu.com/ubuntu jammy-updates InRelease             
Hit:6 http://archive.ubuntu.com/ubuntu jammy-backports InRelease           
Hit:7 http://security.ubuntu.com/ubuntu jammy-security InRelease           
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
W: Skipping acquire of configured file 'oem/binary-i386/Packages' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/binary-amd64/Packages' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/i18n/Translation-en' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/i18n/Translation-en_US' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/Components-amd64.yml' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/icons-48x48.tar' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/icons-64x64.tar' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/icons-64x64@2.tar' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/cnf/Commands-amd64' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)

```

So I am lost ... can this be fixed or is it a Dell problem?

---

### Post by Xian on 2022-07-16
Somewhere in your /etc/apt/sources.list you have the addition of "oem" content that doesn't exist of the server. 
Apt searches for that content and then complains that it's not there.

For example: deb [http://oem.archive.canonical.com](http://oem.archive.canonical.com) jammy multiverse oem partner
Just remove the offending "oem" notation. 

Or post the content of your /etc/apt/sources.list for review.

---

### Post by zkab on 2022-07-17
Thanks ... OK here comes my /etc/apt/sources.list & sources.d

```
oden@rk-dell:/etc/apt$ cat /etc/apt/sources.list

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ jammy main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jammy universe
# deb-src http://archive.ubuntu.com/ubuntu/ focal universe
deb http://archive.ubuntu.com/ubuntu/ jammy-updates universe
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jammy multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal multiverse
deb http://archive.ubuntu.com/ubuntu/ jammy-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu jammy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security universe
# deb-src http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu jammy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse

oden@rk-dell:/etc/apt/sources.list.d$ l
.rw-r--r-- 102 root 15 jul 16:02 focal-oem.list
.rw-r--r-- 102 root 15 jul 16:02 focal-oem.list.distUpgrade
.rw-r--r-- 102 root 15 jul 15:56 focal-oem.list.save
.rw-r--r-- 191 root 16 jul 16:52 google-chrome.list
.rw-r--r-- 190 root 15 jul 16:02 google-chrome.list.distUpgrade
.rw-r--r-- 190 root 15 jul 15:56 google-chrome.list.save
.rw-r--r-- 256 root 15 jul 16:02 oem-somerville-tentacool-meta.list
.rw-r--r-- 256 root 15 jul 16:02 oem-somerville-tentacool-meta.list.distUpgrade
.rw-r--r-- 256 root 15 jul 15:56 oem-somerville-tentacool-meta.list.save
.rw-r--r-- 230 root 15 jul 16:02 somerville-dla-team-ubuntu-ppa-bionic.list
.rw-r--r-- 230 root 15 jul 16:02 somerville-dla-team-ubuntu-ppa-bionic.list.distUpgrade
.rw-r--r-- 228 root 15 jul 15:56 somerville-dla-team-ubuntu-ppa-bionic.list.save
.rw-r--r-- 181 root 15 jul 16:02 somerville-dla-team-ubuntu-ppa-focal.list
.rw-r--r-- 148 root 15 jul 16:02 somerville-dla-team-ubuntu-ppa-focal.list.distUpgrade
.rw-r--r-- 148 root 15 jul 15:56 somerville-dla-team-ubuntu-ppa-focal.list.save

oden@rk-dell:/etc/apt/sources.list.d$ cat focal-oem.list
deb http://oem.archive.canonical.com/ jammy oem
# deb-src http://oem.archive.canonical.com/ focal oem
oden@rk-dell:/etc/apt/sources.list.d$ cat focal-oem.list.distUpgrade 
deb http://oem.archive.canonical.com/ focal oem
# deb-src http://oem.archive.canonical.com/ focal oem
oden@rk-dell:/etc/apt/sources.list.d$ cat focal-oem.list.save 
deb http://oem.archive.canonical.com/ focal oem
# deb-src http://oem.archive.canonical.com/ focal oem
oden@rk-dell:/etc/apt/sources.list.d$ 

oden@rk-dell:/etc/apt/sources.list.d$ cat oem-somerville-tentacool-meta.list
deb http://dell.archive.canonical.com/ jammy somerville
# deb-src http://dell.archive.canonical.com/ focal somerville
deb http://dell.archive.canonical.com/ jammy somerville-tentacool
# deb-src http://dell.archive.canonical.com/ focal somerville-tentacool
oden@rk-dell:/etc/apt/sources.list.d$ cat oem-somerville-tentacool-meta.list.distUpgrade 
deb http://dell.archive.canonical.com/ focal somerville
# deb-src http://dell.archive.canonical.com/ focal somerville
deb http://dell.archive.canonical.com/ focal somerville-tentacool
# deb-src http://dell.archive.canonical.com/ focal somerville-tentacool
oden@rk-dell:/etc/apt/sources.list.d$ cat oem-somerville-tentacool-meta.list.save 
deb http://dell.archive.canonical.com/ focal somerville
# deb-src http://dell.archive.canonical.com/ focal somerville
deb http://dell.archive.canonical.com/ focal somerville-tentacool
# deb-src http://dell.archive.canonical.com/ focal somerville-tentacool
oden@rk-dell:/etc/apt/sources.list.d$ 

oden@rk-dell:/etc/apt/sources.list.d$ cat somerville-dla-team-ubuntu-ppa-bionic.list
# deb http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
oden@rk-dell:/etc/apt/sources.list.d$ cat somerville-dla-team-ubuntu-ppa-bionic.list.distUpgrade 
# deb http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
oden@rk-dell:/etc/apt/sources.list.d$ cat somerville-dla-team-ubuntu-ppa-bionic.list.save 
deb http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
oden@rk-dell:/etc/apt/sources.list.d$ 

oden@rk-dell:/etc/apt/sources.list.d$ cat somerville-dla-team-ubuntu-ppa-focal.list
# deb http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu jammy main # disabled on upgrade to jammy
# deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu focal main
oden@rk-dell:/etc/apt/sources.list.d$ cat somerville-dla-team-ubuntu-ppa-focal.list.distUpgrade 
deb http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu focal main
# deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu focal main
oden@rk-dell:/etc/apt/sources.list.d$ cat somerville-dla-team-ubuntu-ppa-focal.list.save 
deb http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu focal main
# deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu focal main
oden@rk-dell:/etc/apt/sources.list.d$ 

```

---

### Post by mIk3_08 on 2022-07-17
> **zkab said:**
> I have just received my Dell XPS 13 Plus (9320) with Ubuntu 20.04 LTS preinstalled.
What I did whas to upgrade it to 22.04 LTS and followed [https://askubuntu.com/questions/1341276/no-dell-linux-assistant-program-upgrade](https://askubuntu.com/questions/1341276/no-dell-linux-assistant-program-upgrade)
The upgrade went OK and I rebooted.
When I then remote SSH to XPS there was messages.
```

2 devices have a firmware upgrade available.
Run `fwupdmgr get-upgrades` for more information.

oden@rk-dell:~$ fwupdmgr get-upgrades
Devices with no available firmware updates: 
 &#8226; VEN 04F3:00 04F3:31D1
 &#8226; TPM 2.0
 &#8226; UEFI Device Firmware
 &#8226; UEFI Device Firmware
 &#8226; UEFI dbx
 &#8226; USB4 Retimer
 &#8226; USB4 host controller
 &#8226; USB4 host controller
Devices with the latest available firmware version:
 &#8226; RTS5413 in Dell dock
 &#8226; RTS5********************************************************487 in Dell dock
 &#8226; VMM5331 in Dell dock
 &#8226; PM9A1 NVMe Samsung 1024GB
 &#8226; System Firmware
 &#8226; Thunderbolt controller in Dell dock
XPS 9320
&#9474;
&#9500;&#9472;Package level of Dell dock:
&#9474; &#9474;   Device ID:          073624c16dd99abe01ba1da223a70321e4f29beb
&#9474; &#9474;   Summary:            A representation of dock update status
&#9474; &#9474;   Current version:    01.00.25.00
&#9474; &#9474;   Vendor:             Dell Inc. (USB:0x413C)
&#9474; &#9474;   Install Duration:   5 seconds
&#9474; &#9474;   GUID:               8ceeeffd-51b6-580c-9b75-69143227aff8
&#9474; &#9474;   Device Flags:       &#8226; Updatable
&#9474; &#9474;                       &#8226; Supported on remote server
&#9474; &#9474;                       &#8226; Device can recover flash failures
&#9474; &#9474;                       &#8226; Device is usable for the duration of the update
&#9474; &#9474; 
&#9474; &#9492;&#9472;WD19/WD22/HD22 Series Dock:
&#9474;       New version:      01.00.25.01
&#9474;       Remote ID:        lvfs
&#9474;       Release ID:       13766
&#9474;       Summary:          Firmware package version for WD19 Series Dock
&#9474;       License:          Proprietary
&#9474;       Size:             24 bytes
&#9474;       Created:          2022-06-08
&#9474;       Urgency:          High
&#9474;       Vendor:           Dell
&#9474;       Duration:         5 seconds
&#9474;       Release Flags:    &#8226; Is upgrade
&#9474;       Description:      
&#9474;       -Update the firmware package version of Dell docking station's composite devices.
&#9474;     
&#9492;&#9472;WD19TB:
  &#9474;   Device ID:          570867f4ddda9915445da59bd85cd0e0e507270e
  &#9474;   Summary:            High performance dock
  &#9474;   Current version:    01.00.00.05
  &#9474;   Vendor:             Dell Inc. (USB:0x413C)
  &#9474;   Install Duration:   1 minute
  &#9474;   GUID:               cd357cf1-40b2-5d87-b8df-bb2dd82774aa
  &#9474;   Device Flags:       &#8226; Updatable
  &#9474;                       &#8226; Supported on remote server
  &#9474;                       &#8226; Device stages updates
  &#9474;                       &#8226; Device can recover flash failures
  &#9474;                       &#8226; Device is usable for the duration of the update
  &#9474; 
  &#9492;&#9472;WD19/WD22 EC:
        New version:      01.01.00.03
        Remote ID:        lvfs
        Release ID:       13769
        Summary:          Firmware update for WD19/WD22 EC
        License:          Proprietary
        Size:             131,0 kB
        Created:          2022-06-08
        Urgency:          High
        Vendor:           Dell
        Duration:         1 minute
        Release Flags:    &#8226; Is upgrade
        Description:      
        -Improved the display compatibility between systems and monitors.

```

I also made 'sudo apt update' and got some errors:
```
oden@rk-dell:~$ sudo apt update
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dell.archive.canonical.com jammy InRelease                                                                
Hit:3 http://oem.archive.canonical.com jammy InRelease                                                                 
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease                                           
Hit:5 http://archive.ubuntu.com/ubuntu jammy-updates InRelease             
Hit:6 http://archive.ubuntu.com/ubuntu jammy-backports InRelease           
Hit:7 http://security.ubuntu.com/ubuntu jammy-security InRelease           
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
W: Skipping acquire of configured file 'oem/binary-i386/Packages' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/binary-amd64/Packages' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/i18n/Translation-en' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/i18n/Translation-en_US' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/Components-amd64.yml' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/icons-48x48.tar' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/icons-64x64.tar' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/icons-64x64@2.tar' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/cnf/Commands-amd64' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)

```

So I am lost ... can this be fixed or is it a Dell problem?

Please run the script on this url page below and post the information or pastebin link in this thread. Regards and cheers.
```
https://github.com/UbuntuForums/system-info
```

---

### Post by grahammechanical on 2022-07-17
Have you upgraded the firmware? I do not think that those messages have anything to do with Ubuntu but everything to do with Dell.

When we purchase a machine with Ubuntu pre-installed we often get a Linux kernel that has been modified by the supplier. It is called an OEM kernel and it is hosted on Ubuntu servers, In time Ubuntu developers merge the differences in the OEM kernel into Ubuntu's generic Linux kernel.

[https://wiki.ubuntu.com/Kernel/OEMKernel](https://wiki.ubuntu.com/Kernel/OEMKernel)

You may find that in 20.04 you had an OEM kernel and now in 22.04 you have a generic kernel. Is the hardware still working?

I think that you upgraded to 22.04 too early. The official upgrade path does not open until late july/early August. And this is why you are seeing those error messages about 

> repository 'http://oem.archive.canonical.com jammy InRelease'

That repository exists in 20.04 (focal) but not yet in 22.04 (jammy). In my best guess opinion.

I shall not be upgrading my pre-installed Ubuntu 20.04 until near its end of support life. I am allowing my OEM supplier the time to put in place the things it needs to do to allow an upgrade to the next Ubuntu LTS. They surely are familiar with the Ubuntu upgrade schedule.

I have installed Ubuntu 22.04 on a separate partition as a dual boots so I can see how things develop as this is the first time I have purchased a machine with Ubuntu pre-installed.

Regards

---

### Post by Xian on 2022-07-17
> **zkab said:**
> 
[COLOR=#000000][FONT=&amp]oden@rk-dell:/etc/apt/sources.list.d$ cat focal-oem.list[/FONT][/COLOR]deb 
[http://oem.archive.canonical.com/](http://oem.archive.canonical.com/) jammy oem


There is no oem content on this server for jammy.
Apt complains when searching and does not find the component.

Comment out this line.

---

### Post by zkab on 2022-07-18
Thanks for your input ... now I understand how Dell OEM Ubuntu works.
I guess the best way to go is to restore Dell to factory settings and wait for the upgrade path to 22.04 from Dell

---

