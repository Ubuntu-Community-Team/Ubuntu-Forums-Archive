---
title: "Unmet dependencies when installing ubuntu-desktop on Ubuntu Server 22.04 (ARM64)"
date: 2022-06-16
forum: Installation &amp; Upgrades
---

### Post by tomacco81 on 2022-06-16
Hello,
I have an Ubuntu 22.04 instance installed on my M1 Mac with  multipass. 
Now when I try to install ubuntu-desktop I get the following  error message:

 ```
ubuntu@primary:~$ sudo apt update && sudo apt upgrade
Hit:1 http://ports.ubuntu.com/ubuntu-ports jammy InRelease
Hit:2 http://ports.ubuntu.com/ubuntu-ports jammy-updates InRelease
Hit:3 http://ports.ubuntu.com/ubuntu-ports jammy-backports InRelease
Hit:4 http://ports.ubuntu.com/ubuntu-ports jammy-security InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

ubuntu@primary:~$ sudo apt install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-properties-gtk : Depends: python3-software-properties (= 0.99.22) but 0.99.22.1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Does anyone have any idea how I can install ubuntu-desktop?

---

### Post by ActionParsnip on 2022-06-16
Could try:
```

wget -O /tmp/python3-software-properties_0.99.22_all.deb http://ports.ubuntu.com/pool/main/s/software-properties/python3-software-properties_0.99.22_all.deb
sudo apt install /tmp/python3-software-properties_0.99.22_all.deb
sudo apt -f install
sudo apt install ubuntu-desktop

```

---

### Post by tomacco81 on 2022-06-18
After running 
```
sudo apt update && sudo apt upgrade 
``` 
again today, the desktop environment now installs without errors.
Thanks for the tip anyway!

---

