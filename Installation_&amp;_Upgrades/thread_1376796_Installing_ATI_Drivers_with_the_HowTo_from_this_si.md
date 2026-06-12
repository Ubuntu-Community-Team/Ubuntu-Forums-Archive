---
title: "Installing ATI Drivers with the HowTo from this site .. Error."
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by iceache on 2010-01-09
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Following that guide.. on a fresh install of Ubuntu 9.10, with ATI Catalyst 9.12 drivers. Here is my error after I type "sudo dpkg -i *"

```
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up xorg-driver-fglrx-dev (2:8.681-0ubuntu1) ...
Setting up fglrx-amdcccle (2:8.681-0ubuntu1) ...
Processing triggers for desktop-file-utils ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ati-driver-installer-9-12-x86.x86_64.run
 fglrx-installer_8.681-0ubuntu1_i386.changes
iceache@iceache-desktop:~/Desktop$ 

```

---

### Post by jocko on 2010-01-09
> **iceache said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Following that guide.. on a fresh install of Ubuntu 9.10, with ATI Catalyst 9.12 drivers. Here is my error after I type "[COLOR=Red]sudo dpkg -i *[/COLOR]"

```
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up xorg-driver-fglrx-dev (2:8.681-0ubuntu1) ...
Setting up fglrx-amdcccle (2:8.681-0ubuntu1) ...
Processing triggers for desktop-file-utils ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
[COLOR=Red] ati-driver-installer-9-12-x86.x86_64.run
 fglrx-installer_8.681-0ubuntu1_i386.changes[/COLOR]
iceache@iceache-desktop:~/Desktop$ 

```
That's because you use a too open wild card (*) in the command, so dpkg tries to install files that are not .deb files.
Just use:```
sudo dpkg -i **[COLOR=Blue]*.deb[/COLOR]**
```But your install is already done, the errors are harmless and simply means that dpkg can't use files that are not proper .deb files (like the .run and .changes files it complains about).

---

### Post by iceache on 2010-01-09
> **jocko said:**
> That's because you use a too open wild card (*) in the command, so dpkg tries to install files that are not .deb files.
Just use:```
sudo dpkg -i **[COLOR=Blue]*.deb[/COLOR]**
```But your install is already done, the errors are harmless and simply means that dpkg can't use files that are not proper .deb files (like the .run and .changes files it complains about).

Oh ok, cool.. But when I reboot, I get an error when I run fglrxinfo, i'll post that when I reboot this time.


> 
iceache@iceache-desktop:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
iceache@iceache-desktop:~$ 




---

### Post by iceache on 2010-01-09
Ok, it works now :D

---

