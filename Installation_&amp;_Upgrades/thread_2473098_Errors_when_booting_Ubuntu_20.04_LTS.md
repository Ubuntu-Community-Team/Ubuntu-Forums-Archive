---
title: "Errors when booting Ubuntu 20.04 LTS"
date: 2022-03-23
forum: Installation &amp; Upgrades
---

### Post by rikuitop on 2022-03-23
Hi,
 I've just got a new laptop (MSI GF76 12UC-019XFR - PCIe 512GB SSD - RTX3050 - I7 12700H) with Free Dos. I want to install Ubuntu 20.04 LTS.
In the BIOS I have changed the following options:
Legacy USB Support -> disabled
Fast Boot -> disabled
Secure Boot Support -> disabled
Intel Speed Shift -> disabled
Intel Virtualization -> disabled

Boot order:
USB CD/DVD
Hard Disk Micron_2450_MTFDKBA512TFK

In the Ubuntu install I have chosen 'Something else' and then the following partitions:
/dev/nvme0n1
  /dev/nvme0n1 p1  efi                     486MB
  /dev/nvme0n1 p2  ext4  /            32000MB    
  /dev/nvme0n1 p3  ext4  /home  479621MB

After removing the USB flash drive and rebooting, I have got a black screen with the following messages:
Bluetooth: hci0: Reading Intel version information failed (-22)
usb 3-10: device descriptor read/64, error -71

If I choose 'Erase disk and install Ubuntu' instead of 'Something else' I have got the same errors.

Any idea to fix this up?

Thank you for your help.

---

### Post by rikuitop on 2022-03-23
Ubuntu 21.10 has solved the issue. In fact I succeeded to get ubuntu from SSD only once. After having updated ubuntu, I have got the same errors after the reboot (Bluetooth: hci0: Reading Intel version information failed (-22) and usb 3-10: device descriptor read/64, error -71).

---

### Post by oldfred on 2022-03-23
Do you have the latest UEFI from MSI?
And latest firmware for SSD?

Very new systems often need very newest release. And sometimes even need newer kernel or drivers than in latest release.

If willing to experiment, you can try 22.04 which will be released in April, about a month.
It will have many updates, and if you install now, best to really houseclean or reinstall otherwise log files may be large.

[https://ubuntuforums.org/forumdisplay.php?f=427](https://ubuntuforums.org/forumdisplay.php?f=427)
[https://discourse.ubuntu.com/t/jammy-jellyfish-release-schedule/23906](https://discourse.ubuntu.com/t/jammy-jellyfish-release-schedule/23906)
One site that often tests newer versions with various hardware.
[https://www.phoronix.com/scan.php?page=news_item&px=XWayland-Xorg-Jammy-Gaming](https://www.phoronix.com/scan.php?page=news_item&px=XWayland-Xorg-Jammy-Gaming)

---

### Post by rikuitop on 2022-03-23
Thank you for your reply.
I have the latest BIOS. As for Micron SSD firmware, 'sudo fwupdmgr refresh' was empty... I will try 22.04.

---

### Post by oldfred on 2022-03-23
Most SSD require you to go to the vendor site and download directly.
I have Samsung and their Magician software does not work, but they also have a downloaded ISO by model & version of NVMe drive.

---

### Post by rikuitop on 2022-03-24
I was able to to boot Ubuntu 21.10 from SSD again.
In the BIOS, I had the following parameters: Intel Speed Shift enabled, Intel Virtualization Technology enabled, XHCI Hand-Off disabled, Fast Boot Disabled, Secure Boot Support disabled, Legacy USB support enabled
 Option of the Ubuntu installer: Minimal Installation, Install third party software and Something Else:
/dev/nvme0n1 p1 1024MB (empty partition)
  /dev/nvme0n1 p2  efi 512MB
  /dev/nvme0n1 p3  ext4  / 48000MB    
  /dev/nvme0n1 p4  ext4  /home  466621MB
Boot Loader on '/dev/nvme0n1 p2'
In the Ubuntu session, the Micron SSD was up to date  (after having downloaded Storage Executive Software from Micron site).
However the system did not power off properly (black screen and power on). So I manually turned off the power.
After turning on the power, I was not able to get the Ubuntu session again (black screen with 'Bluetooth: hci0: Reading Intel version information failed (-22)',
'usb 3-10: device descriptor read/64, error -71').
I went in the BIOS. Under Boot\UEFI two options were present:
Boot Option #1 ubuntu (Micron_2450_MTFDK512TFK)
Boot Option #2 ubuntu (Micron_2450_MTFDK512TFK)

Option #1 was disabled => I ended up with the prompt grub>
Option #2 was disabled => I ended up with the black screen and the error messages
Here are the grub output: ([https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot](https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot))
grub> ls (hd0,gpt2)/efi/boot/
bootx64.efi fbx64.efi mx64.efi
grub> ls (hd0,gpt2)/efi/ubuntu/
grubx64.efi shimx64.efi mmx64.efi bootx64.csv grub.cfg
grub> set prefix=(hd0,gpt2)/efi/ubuntu/grub
grub> set root=(hd0,gpt2)
insmod linux
insmod normal 
normal
boot
error: you need to load the kernel first.
linux /boot/vmlinuz root=/dev/nvme0n1p3
initrd /boot/initrd.img
boot

Again, I have got the error messages...

Conclusion: it seems the boot parameters have changed after the first success (maybe due to the name of the PCIe SSD nvme0n1) and I am not able to find the right parameters.

---

### Post by oldfred on 2022-03-24
Can you boot recovery mode? Or second entry in grub menu.
If only one install, you do not get grub menu by default.
You have to press escape right after vendor UEFI/BIOS screen & before grub menu would normally appear.

What video card/chip do you have?
If nVidia did you use Safe Boot and then select to install proprietary drivers?
If not, you probably need nVidia driver.

Can you use this to boot?
configfile (hd0,2)/boot/grub/grub.cfg

---

### Post by rikuitop on 2022-03-24
Thank you for your reply oldfred. 
Video card: Nvidia GA107M GeForce RTX 3050.
I did not use Safe Boot. I selected the 'install proprietary drivers' option.
I updated the driver.

Excellent! The last command did it. I am now able to get my Ubuntu session for a second time.
configfile (hd0,2)/boot/grub/grub.cfg
You are brilliant.
What should I do next to fix it definitely?

Now, 'inxi -F' gives me the following driver: nvidia 510.54

---

### Post by rikuitop on 2022-03-24
Now it works fine!

---

### Post by oldfred on 2022-03-24
Glad it is working.

With nVidia driver, you must purge before installing a new one or you get conflicts. 
But if working, and Ubuntu should have installed the correct default one, then no change required.

---

### Post by rikuitop on 2022-03-26
In the first Ubuntu session, it is indeed critical to first install the nVidia driver to avoid conflicts (restart, shutdown, boot, ...).
nouveau is the default open-source driver. Do you mean to do it in the following order?

```

sudo apt update
sudo apt upgrade
sudo apt purge nouveau
sudo apt autoremove
sudo apt install nvidia-driver-510
```

---

### Post by oldfred on 2022-03-26
If changing a nVidia driver you purge nVidia.
If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

#What is installed
dpkg -l | grep -i nvidia
dkms status

This is now older as bumblebee is not used anymore.
If you have installed any version, you must purge first, old will  conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by rikuitop on 2022-03-27
Thank for your reply oldfred.  510 is the right nvidia driver.Tomorrow I will try kernel 5.16.
([https://sourcedigit.com/26772-download-install-linux-kernel-5-16-ubuntu-21-10/](https://sourcedigit.com/26772-download-install-linux-kernel-5-16-ubuntu-21-10/))

---

### Post by rikuitop on 2022-03-28
Kernel 5.16 was too high. So here is my system:
Kernel: 5.15.0-051500-generic x86_64 bits: 64 
Desktop: Cinnamon 4.8.6
 Distro: Ubuntu 21.10 (Impish Indri)

Now, wifi and bluetooth are available. Here are the remaining errors present in the logs:
GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
psmouse serio1: synaptics: Unable to query device: -71
cpufreq: cpufreq_online: Failed to initialize policy for cpu: 11 (-19)

Cheers!

---

