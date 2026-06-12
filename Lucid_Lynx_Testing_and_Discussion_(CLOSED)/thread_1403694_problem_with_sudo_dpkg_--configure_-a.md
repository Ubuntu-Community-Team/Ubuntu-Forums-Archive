---
title: "problem with sudo dpkg --configure -a"
date: 2010-02-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-10
i have downloaded a few updates and something did go right i tried apt-get and some more things but no luck what can i do to fix it now? 

sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1
[COLOR=#009900]
[COLOR=black]i alsot tried sudo apt-get upgrade and got this
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)

how can i remove [/COLOR][/COLOR][COLOR=#009900][COLOR=black]/initrd.img-2.6.32-12-generic? maybe an apptitide command?[/COLOR][/COLOR]

---

### Post by tad1073 on 2010-02-10
[http://ubuntuforums.org/showthread.php?t=1403446](http://ubuntuforums.org/showthread.php?t=1403446)

---

### Post by aviramof on 2010-02-10
thanks and by the way why the reposetories have the latest version?
Debian -- Package Download Selection -- initramfs-tools_0.93.4_all.deb.url

> **Rallg said:**
> My system complained that
./lib/udev/firmware.sh
was not there. So I used
sudo nautilus
to go into
/lib/udev/
and located the firmware file (which had no .sh extension), and created a  link to it, named
firmware.sh.
Then, running
sudo dpkg --configure -a
solved the problem.

---

