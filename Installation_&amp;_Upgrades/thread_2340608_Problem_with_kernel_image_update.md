---
title: "Problem with kernel image update"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by SamInside on 2016-10-20
**Solution: I had not enough space on /boot partition.**

---

I'm using *Xubuntu 16 LTS* up to date, but I guess this could be Ubuntu-general.
The very last update gave me crash reports after each login, related to the kernel image 4.0.something.
Every login I got these errors, so I did:
```
sudo apt-get remove
```
and it uninstalled old unused kernel images (I guess?)

Right now everything works fine again, and if I launch the update utility it says my system is updated... 0.o
Shouldn't it attempt to install those updates again? Sorry, quite lost here, I don't know much about *apt-get*, automatic updates always worked fine by themselves up to this point.

[B]Are there any known problems with some recent updates regarding kernel images?
[/B]Is my system now "corrupted" and do I have to do something to fix it?

[SIZE=5]**UPDATE**[/SIZE]
It happened again, see new post:
[https://ubuntuforums.org/showthread.php?t=2340608&p=13577344#post13577344](https://ubuntuforums.org/showthread.php?t=2340608&p=13577344#post13577344)

---

### Post by howefield on 2016-10-20
What version of the kernel are you using ?

```
uname -a
```

---

### Post by SamInside on 2016-10-20
Good question. Looks like I'm using
```
Linux PC 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by howefield on 2016-10-20
That seems to be the latest kernel version, so if everything is working fine I'd suggest leaving it be.

```
apt-cache policy linux-generic
linux-generic:
  Installed: 4.4.0.45.48
  Candidate: 4.4.0.45.48
  Version table:
 *** 4.4.0.45.48 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     4.4.0.21.22 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
``` 

Wouldn't harm to try these commands from the terminal and if any error, post back.

```
sudo apt update
```
```
sudo apt upgrade
```

---

### Post by SamInside on 2016-10-20
> **howefield said:**
> Wouldn't harm to try these commands...
(output manually translated from my language)
```

$ sudo apt update
[...]
6 packets can be upgraded: run "apt list --upgradable" to list them.

$ sudo apt upgrade
[...]
The following packets will be upgraded:
  distro-info-data gnome-software gnome-software-common systemd-sysv xserver-common
  xserver-xorg-core
6 updated, 0 installed, 0 to remove and 0 not updated.
3.874 kB of archives to download
[...]
```
No errors / warnings.
On *apt upgrade* I've chosen "n" (no) because I'm not sure if I'll encounter the same problems as in my OP.

---

### Post by SamInside on 2016-12-01
[SIZE=5][B]UPDATE
[/B][/SIZE]
It happened again.
Today I booted the PC and upon login I got some errors again. I did "send report" just to read more information about these errors:
```

(Translating from my language)
A problem happened during the installation of the software.
Package: linux-image-generic 4.5.0.51.54
package linux-image-generic 4.5.0.51.54 failed to install/upgrade: run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1

```

Note: In these past days I didn't do anything particular with my PC, just usual browsing.

```

$ uname -a
Linux PC 4.4.0-51-generic #72-Ubuntu SMP Thu Nov 24 18:29:54 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by ian-weisser on 2016-12-01
Run again: sudo apt upgrade
This time, hit 'y'.

If there are any errors, the copy-and-paste the entire output here. Don't edit anything out.

---

### Post by SamInside on 2016-12-02
```

(translating from my language)
Continue? [Y/n] Y
Configuration of linux-image-extra-4.4.0-51-generic (4.4.0-51.72)...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic

gzip: stdout: No space left on device (not sure what it means here, since I have 40 GB left on the HDD)
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-51-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing the packet linux-image-extra-4.4.0-51-generic (--configure):
 the installed subprocess script of post-installation returned error status 1
dpkg: dependencies problems makes impossible to configure linux-image-generic:
 linux-image-generic depends from linux-image-extra-4.4.0-51-generic; however:
  the packet linux-image-extra-4.4.0-51-generic is not yet configured.

dpkg: error processing the packet linux-image-generic (--configure):
 dependencies problems - left not configured
dpkg: dependencies problems makes impossible to configure linux-generic:
 linux-generic depends from linux-image-generic (= 4.4.0.51.54); however:
  the packet linux-image-generic is not yet configured.

dpkg: error processing the packet linux-generic (--configure):
 dependencies problems - left not configured
"Apport" warning not written because the error message indicates a previous fail.
            "Apport" warning not written because the error message indicates a previous fail.
       There have been errors processing:
 linux-image-extra-4.4.0-51-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2016-12-02
> **SamInside said:**
> ```
gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
```

Out-of-space is one of the most common reasons for the problem you describe.

Please show us the complete output of:
```
df
df -i
ls -l /boot
dpkg -l | grep linux-image
```

---

### Post by SamInside on 2016-12-02
Oh, my bad, I now remember and realize that I have a separate boot partition due to the Ubuntu encryption. And that's only 250MB.
So I deleted old kernels and now it works.
Thanks.

---

