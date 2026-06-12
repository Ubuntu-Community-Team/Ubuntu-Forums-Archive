---
title: "install MPLABX on github ci/cd libusb-1.0.so not found"
date: 2024-04-18
forum: Installation &amp; Upgrades
---

### Post by cedric-air on 2024-04-18
I'm trying to install MPLABX on a github CI/CD pipeline. i get the message libusb-1.0.so, even though libusb-dev has been installed.

Here's the script:
```

name: Revomax
run-name: ${{ github.actor }} is building Revomax
on: [push]
jobs:
  tutorial:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm install -g bats
      - run: bats -v
  tutorial2:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout repo
      uses: actions/checkout@v2
      with:
        submodules: 'recursive'
    - name: Install dependencies
      run: |
        sudo apt-get update && \
        sudo apt-get install -y libc6 libx11-6 libxext6 libstdc++6 libexpat1 libusb-dev && \
        sudo apt-get clean && \
        sudo apt-get autoremove && \
        sudo rm -rf /var/lib/apt/lists/*
    - name: Install XC8
      run: |
        wget https://ww1.microchip.com/downloads/aemDocuments/documents/DEV/ProductDocuments/SoftwareTools/xc8-v2.36-full-install-linux-x64-installer.run &&
        chmod +x xc8-v2.36-full-install-linux-x64-installer.run && \
        sudo ./xc8-v2.36-full-install-linux-x64-installer.run --mode unattended --unattendedmodeui none --netservername localhost --prefix "/opt/microchip-mplabxc8-bin/"
    - name: Install MPLABX
      run: |
        wget -U "Mozilla" https://www.microchip.com/bin/download?f=aHR0cHM6Ly93dzEubWljcm9jaGlwLmNvbS9kb3dubG9hZHMvYWVtRG9jdW1lbnRzL2RvY3VtZW50cy9ERVYvUHJvZHVjdERvY3VtZW50cy9Tb2Z0d2FyZVRvb2xzL01QTEFCWC12Ni4xMC1saW51eC1pbnN0YWxsZXIudGFy -O MPLABX-v6.10-linux-installer.tar &&
        tar -xf MPLABX-v6.10-linux-installer.tar &&
        sudo ./MPLABX-v6.10-linux-installer.sh --nox11 -- --unattendedmodeui none --mode unattended --ipe 0 --collectInfo 0 --installdir /opt/mplabx
    - name: Output results
      run: |
        ls -l

```

Here's the output:
```

$ act
[Revomax/tutorial ] &#128640;  Start image=catthehacker/ubuntu:act-latest
[Revomax/tutorial2] &#128640;  Start image=catthehacker/ubuntu:act-latest
[Revomax/tutorial ]   &#128051;  docker pull image=catthehacker/ubuntu:act-latest platform= username= forcePull=true
[Revomax/tutorial2]   &#128051;  docker pull image=catthehacker/ubuntu:act-latest platform= username= forcePull=true
[Revomax/tutorial ]   &#128051;  docker create image=catthehacker/ubuntu:act-latest platform= entrypoint=["tail" "-f" "/dev/null"] cmd=[]
[Revomax/tutorial ]   &#128051;  docker run image=catthehacker/ubuntu:act-latest platform= entrypoint=["tail" "-f" "/dev/null"] cmd=[]
[Revomax/tutorial ]   &#9729;  git clone 'https://github.com/actions/setup-node' # ref=v4
[Revomax/tutorial2]   &#128051;  docker create image=catthehacker/ubuntu:act-latest platform= entrypoint=["tail" "-f" "/dev/null"] cmd=[]
[Revomax/tutorial2]   &#128051;  docker run image=catthehacker/ubuntu:act-latest platform= entrypoint=["tail" "-f" "/dev/null"] cmd=[]
[Revomax/tutorial2] &#11088; Run Main Checkout repo
[Revomax/tutorial2]   &#128051;  docker cp src=/home/werk/git-werkmap/OptiClimateRevolution_FW/. dst=/home/werk/git-werkmap/OptiClimateRevolution_FW
[Revomax/tutorial2]   &#9989;  Success - Main Checkout repo
[Revomax/tutorial2] &#11088; Run Main Install dependencies
[Revomax/tutorial2]   &#128051;  docker exec cmd=[bash --noprofile --norc -e -o pipefail /var/run/act/workflow/1] user= workdir=
Get:1 https://packages.microsoft.com/ubuntu/22.04/prod jammy InRelease [3632 B]
Get:2 https://ppa.launchpadcontent.net/git-core/ppa/ubuntu jammy InRelease [23.8 kB]
Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]      
Get:4 http://archive.ubuntu.com/ubuntu jammy InRelease [270 kB]                
Get:6 https://packages.microsoft.com/ubuntu/22.04/prod jammy/main amd64 Packages [141 kB]
Get:7 https://packages.microsoft.com/ubuntu/22.04/prod jammy/main all Packages [1035 B]
Get:8 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]        
Get:9 https://ppa.launchpadcontent.net/git-core/ppa/ubuntu jammy/main amd64 Packages [2969 B]
Get:10 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [109 kB]    
Get:11 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [1082 kB]
Get:5 https://packagecloud.io/github/git-lfs/ubuntu jammy InRelease [28.0 kB]  
Get:12 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages [1792 kB]    
Get:13 https://packagecloud.io/github/git-lfs/ubuntu jammy/main amd64 Packages [1842 B]
[Revomax/tutorial ] &#127937;  Job succeeded
Get:14 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [1695 kB]
Get:15 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [2135 kB]
Get:16 http://security.ubuntu.com/ubuntu jammy-security/multiverse amd64 Packages [44.7 kB]
Get:17 http://archive.ubuntu.com/ubuntu jammy/universe amd64 Packages [17.5 MB]
Get:18 http://archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages [266 kB]
Get:19 http://archive.ubuntu.com/ubuntu jammy/restricted amd64 Packages [164 kB]
Get:20 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [1375 kB]
Get:21 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [2242 kB]
Get:22 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [51.1 kB]
Get:23 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [1975 kB]
Get:24 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 Packages [33.3 kB]
Get:25 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 Packages [80.9 kB]
Fetched 31.2 MB in 10s (3009 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
| libxext6 is already the newest version (2:1.3.4-1build1).
| libxext6 set to manually installed.
| libc6 is already the newest version (2.35-0ubuntu3.6).
| libstdc++6 is already the newest version (12.3.0-1ubuntu1~22.04).
| libx11-6 is already the newest version (2:1.7.5-1ubuntu0.3).
| libx11-6 set to manually installed.
| The following additional packages will be installed:
|   libexpat1-dev libusb-0.1-4
| The following NEW packages will be installed:
|   libusb-0.1-4 libusb-dev
| The following packages will be upgraded:
|   libexpat1 libexpat1-dev
| 2 upgraded, 2 newly installed, 0 to remove and 25 not upgraded.
| Need to get 288 kB of archives.
| After this operation, 299 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libexpat1-dev amd64 2.4.7-1ubuntu0.3 [147 kB]
Get:2 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libexpat1 amd64 2.4.7-1ubuntu0.3 [91.0 kB]
Get:3 http://archive.ubuntu.com/ubuntu jammy/main amd64 libusb-0.1-4 amd64 2:0.1.12-32build3 [17.7 kB]
Get:4 http://archive.ubuntu.com/ubuntu jammy/main amd64 libusb-dev amd64 2:0.1.12-32build3 [32.0 kB]
Fetched 288 kB in 1s (441 kB/s)    
| debconf: delaying package configuration, since apt-utils is not installed
(Reading database ... 26642 files and directories currently installed.)
| Preparing to unpack .../libexpat1-dev_2.4.7-1ubuntu0.3_amd64.deb ...
| Unpacking libexpat1-dev:amd64 (2.4.7-1ubuntu0.3) over (2.4.7-1ubuntu0.2) ...
| Preparing to unpack .../libexpat1_2.4.7-1ubuntu0.3_amd64.deb ...
| Unpacking libexpat1:amd64 (2.4.7-1ubuntu0.3) over (2.4.7-1ubuntu0.2) ...
| Selecting previously unselected package libusb-0.1-4:amd64.
| Preparing to unpack .../libusb-0.1-4_2%3a0.1.12-32build3_amd64.deb ...
| Unpacking libusb-0.1-4:amd64 (2:0.1.12-32build3) ...
| Selecting previously unselected package libusb-dev.
| Preparing to unpack .../libusb-dev_2%3a0.1.12-32build3_amd64.deb ...
| Unpacking libusb-dev (2:0.1.12-32build3) ...
| Setting up libexpat1:amd64 (2.4.7-1ubuntu0.3) ...
| Setting up libusb-0.1-4:amd64 (2:0.1.12-32build3) ...
| Setting up libexpat1-dev:amd64 (2.4.7-1ubuntu0.3) ...
| Setting up libusb-dev (2:0.1.12-32build3) ...
| Processing triggers for libc-bin (2.35-0ubuntu3.6) ...
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
| 0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
[Revomax/tutorial2]   &#9989;  Success - Main Install dependencies
[Revomax/tutorial2] &#11088; Run Main Install XC8
[Revomax/tutorial2]   &#128051;  docker exec cmd=[bash --noprofile --norc -e -o pipefail /var/run/act/workflow/2] user= workdir=
| --2024-04-18 10:53:19--  https://ww1.microchip.com/downloads/aemDocuments/documents/DEV/ProductDocuments/SoftwareTools/xc8-v2.36-full-install-linux-x64-installer.run
| Resolving ww1.microchip.com (ww1.microchip.com)... 23.209.233.96
| Connecting to ww1.microchip.com (ww1.microchip.com)|23.209.233.96|:443... connected.
| HTTP request sent, awaiting response... 200 OK
| Length: 71543287 (68M) [application/x-sh]
| Saving to: ‘xc8-v2.36-full-install-linux-x64-installer.run’
| 
xc8-v2.36-full-inst 100%[===================>]  68.23M  3.17MB/s    in 21s     
| 
| 2024-04-18 10:53:40 (3.33 MB/s) - ‘xc8-v2.36-full-install-linux-x64-installer.run’ saved [71543287/71543287]
| 
[Revomax/tutorial2]   &#9989;  Success - Main Install XC8
[Revomax/tutorial2] &#11088; Run Main Install MPLABX
[Revomax/tutorial2]   &#128051;  docker exec cmd=[bash --noprofile --norc -e -o pipefail /var/run/act/workflow/3] user= workdir=
| --2024-04-18 10:54:05--  https://www.microchip.com/bin/download?f=aHR0cHM6Ly93dzEubWljcm9jaGlwLmNvbS9kb3dubG9hZHMvYWVtRG9jdW1lbnRzL2RvY3VtZW50cy9ERVYvUHJvZHVjdERvY3VtZW50cy9Tb2Z0d2FyZVRvb2xzL01QTEFCWC12Ni4xMC1saW51eC1pbnN0YWxsZXIudGFy
| Resolving www.microchip.com (www.microchip.com)... 173.223.115.160, 2a02:26f0:c900:69c::b18, 2a02:26f0:c900:69e::b18
| Connecting to www.microchip.com (www.microchip.com)|173.223.115.160|:443... connected.
| HTTP request sent, awaiting response... 302 Moved Temporarily
| Location: https://ww1.microchip.com/downloads/aemDocuments/documents/DEV/ProductDocuments/SoftwareTools/MPLABX-v6.10-linux-installer.tar [following]
| --2024-04-18 10:54:06--  https://ww1.microchip.com/downloads/aemDocuments/documents/DEV/ProductDocuments/SoftwareTools/MPLABX-v6.10-linux-installer.tar
| Resolving ww1.microchip.com (ww1.microchip.com)... 23.209.233.96
| Connecting to ww1.microchip.com (ww1.microchip.com)|23.209.233.96|:443... connected.
| HTTP request sent, awaiting response... 200 OK
| Length: 999229440 (953M) [application/x-tar]
| Saving to: ‘MPLABX-v6.10-linux-installer.tar’
| 
MPLABX-v6.10-linux- 100%[===================>] 952.94M  2.94MB/s    in 4m 54s  
| 
| 2024-04-18 10:59:00 (3.24 MB/s) - ‘MPLABX-v6.10-linux-installer.tar’ saved [999229440/999229440]
| 
| 64-bit Linux detected.
| Check for 64-bit libraries
| These 64-bit libraries were not found and are needed for MPLAB X to run:
| libusb-1.0.so
| 
| For more information visit http://microchip.wikidot.com/install:mplabx-lin64
| 
[Revomax/tutorial2]   &#10060;  Failure - Main Install MPLABX
[Revomax/tutorial2] exitcode '1': failure
[Revomax/tutorial2] &#127937;  Job failed
Error: The runs.using key in action.yml must be one of: [composite docker node12 node16], got node20

```

---

### Post by Holger_Gehrke on 2024-04-18
I don't know what version (and flavour) of Ubuntu you're using, but on Xubuntu 22.04 there is no libusb-1.0.so; there is a '/usr/lib/x86_64-linux-gnu/libusb-1.0.so.0.3.0' with a symbolic link '/usr/lib/x86_64-linux-gnu/libusb-1.0.so.0'. You might try to set up another symlink named 'libusb-1.0.so' to the same file. 

Also: libusb-dev installs libusb-0.1 through dependencies; if you need libusb-1.0 then you should install libusb-1.0-0-dev.

Holger

---

### Post by cedric-air on 2024-04-18
I'm using ubuntu 22.04: 
[https://packages.microsoft.com/ubuntu/22.04/prod](https://packages.microsoft.com/ubuntu/22.04/prod) jammy InRelease [3632 B]

I'll install that on a virtual machine, and see if the symlink works.
Kind regards,
Cedric

---

### Post by cedric-air on 2024-04-19
I've installed ubuntu 22.04 on a virtual machine. This works wihout any issue (except that my drive is too small)
Check if libusb is present:
```

cedric@cedric-Standard-PC-Q35-ICH9-2009:/usr$ find -iname libusb*
./lib/x86_64-linux-gnu/libusb-1.0.so.0
./lib/x86_64-linux-gnu/libusbmuxd.so.6.0.0
./lib/x86_64-linux-gnu/libusb-1.0.so.0.3.0
./lib/x86_64-linux-gnu/libusbmuxd.so.6
./lib/x86_64-linux-gnu/libusbmuxd-2.0.so.6
./lib/x86_64-linux-gnu/libusbmuxd-2.0.so.6.0.0
./share/doc/libusbmuxd6
./share/doc/libusb-1.0-0
./share/lintian/overrides/libusbmuxd6

```

Install mplabx:
```

:~/Downloads$ wget -U "Mozilla" https://www.microchip.com/bin/download?f=aHR0cHM6Ly93dzEubWljcm9jaGlwLmNvbS9kb3dubG9hZHMvYWVtRG9jdW1lbnRzL2RvY3VtZW50cy9ERVYvUHJvZHVjdERvY3VtZW50cy9Tb2Z0d2FyZVRvb2xzL01QTEFCWC12Ni4xMC1saW51eC1pbnN0YWxsZXIudGFy -O MPLABX-v6.10-linux-installer.tar
--2024-04-19 10:06:25--  https://www.microchip.com/bin/download?f=aHR0cHM6Ly93dzEubWljcm9jaGlwLmNvbS9kb3dubG9hZHMvYWVtRG9jdW1lbnRzL2RvY3VtZW50cy9ERVYvUHJvZHVjdERvY3VtZW50cy9Tb2Z0d2FyZVRvb2xzL01QTEFCWC12Ni4xMC1saW51eC1pbnN0YWxsZXIudGFy
Resolving www.microchip.com (www.microchip.com)... 173.223.115.160, 2a02:26f0:1180:383::b18, 2a02:26f0:1180:39f::b18
Connecting to www.microchip.com (www.microchip.com)|173.223.115.160|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://ww1.microchip.com/downloads/aemDocuments/documents/DEV/ProductDocuments/SoftwareTools/MPLABX-v6.10-linux-installer.tar [following]
--2024-04-19 10:06:26--  https://ww1.microchip.com/downloads/aemDocuments/documents/DEV/ProductDocuments/SoftwareTools/MPLABX-v6.10-linux-installer.tar
Resolving ww1.microchip.com (ww1.microchip.com)... 23.209.233.96
Connecting to ww1.microchip.com (ww1.microchip.com)|23.209.233.96|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 999229440 (953M) [application/x-tar]
Saving to: \u2018MPLABX-v6.10-linux-installer.tar\u2019

MPLABX-v6.10-linux-insta 100%[=================================>] 952,94M  3,34MB/s    in 7m 30s  

2024-04-19 10:13:56 (2,12 MB/s) - \u2018MPLABX-v6.10-linux-installer.tar\u2019 saved [999229440/999229440]

cedric@cedric-Standard-PC-Q35-ICH9-2009:~/Downloads$ chmod +x xc8-v2.36-full-install-linux-x64-installer.run
chmod: cannot access 'xc8-v2.36-full-install-linux-x64-installer.run': No such file or directory
cedric@cedric-Standard-PC-Q35-ICH9-2009:~/Downloads$ tar -xf MPLABX-v6.10-linux-installer.tar
cedric@cedric-Standard-PC-Q35-ICH9-2009:~/Downloads$ sudo ./MPLABX-v6.10-linux-installer.sh --nox11 -- --unattendedmodeui none --mode unattended --ipe 0 --collectInfo 0 --installdir /opt/mplabx
[sudo] password for cedric: 
Sorry, try again.
[sudo] password for cedric: 
64-bit Linux detected.
Check for 64-bit libraries
Verifying archive integrity... All good.
Uncompressing MPLAB X 'v6.10' installer...
Error copying file from packed archive /tmp/selfgz2109/MPLABX-v6.10-linux-installer.run to /opt/mplabx/packs/Microchip/PIC32MZ-EF_DFP/1.3.58/include/proc/p32mz2048efh144.h
:Insufficient Disk Space
Abort

```

---

### Post by cedric-air on 2024-04-19
It also works on the github runner. So this is a problem with act that I run on arch linux to simulate a github run.

Thanks for the help.

---

