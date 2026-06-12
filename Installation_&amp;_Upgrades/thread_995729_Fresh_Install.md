---
title: "Fresh Install"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by sbooder on 2008-11-28
Hi All,
            I am having problems installing ati-driver-installer-8-11-x86.x86_64.run in 8.10 and wondered if installing 8.10 from the live cd rather than the upgrade I have from 8.04 would make a difference.

I have 3 boot set up of Vista, XP PRo and Ubuntu, but do not want to damage the first 2.

Could someone tall me the best way to uninstall Ubuntu 8.10 so I can load 8.10 again on the same directory.

Thanks for any help.

I thought I had better say what the error is when trying to load the ATI driver.

I first use the following

```
/usr/share/ati 
```
then
```
sh ./fglrx-uninstall.sh
```

then I put
```
sudo sh ./ati-driver-installer-8-11-x86.x86_64.run
```

choose the Automatic option in the install programe, and have tried using custom too.

and I get the following error every time.

```
booder@booder-desktop:~$ sudo sh ./ati-driver-installer-8-11-x86.x86_64.run

Created directory fglrx-install.A14427

Verifying archive integrity... All good.

Uncompressing ATI Proprietary Linux Driver-8.552.................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

==================================================

 ATI Technologies Linux Driver Installer/Packager 

==================================================

Detected configuration:

Architecture: i686 (32-bit)

X Server: X.Org 7.4 

DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details

Removing temporary directory: fglrx-install.A14427

booder@booder-desktop:~$ 

```



Simon.

---

