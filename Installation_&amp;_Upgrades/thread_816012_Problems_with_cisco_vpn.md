---
title: "Problems with cisco vpn"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by shotos on 2008-06-02
Hi am trying to install cisco vpn but upon issuing the command, this is what i get. help will be appreciated since i need it in my work.

[COLOR="Sienna"]kwasi@60-84Kwasi:~/Desktop/vpnclient$ sudo ./vpn_install[/COLOR]
[COLOR="DarkOliveGreen"]
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code []

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-14-server/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "" will be used to build the module.

Is the above correct [y]

Making module
./driver_build.sh
Cisco Systems VPN Client Version BUILDVER_STRING
Copyright (C) 1998-2001 Cisco Systems, Inc. All Rights Reserved.

usage:
    ./driver_build.sh 'kernel_src_dir'

'kernel_src_dir' is the directory containing the linux kernel sour 
ce

[/COLOR]
[COLOR="DarkRed"]Failed to make module "cisco_ipsec.ko".[/COLOR]

---

### Post by el-mar01 on 2008-06-02
Try the VPN Connection Manager (vpnc) .. avaliable in the repos .. search for "cisco" in Add/Remove Programs (Applications > Add/Remove)

---

