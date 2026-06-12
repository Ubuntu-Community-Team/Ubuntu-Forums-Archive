---
title: "New build, lubuntu can't install"
date: 2020-01-30
forum: Installation &amp; Upgrades
---

### Post by crispycat on 2020-01-30
Hey, i'm new to computers and linux and everything, and i'm running into a problem with a pc i've been building. My optiplex 580's cpu broke a while back, so i bought a motherboard, cpu and psu off a friend, and scavenged the hdd (which i later replaced) and the dvd rom from the optiplex. I had ubuntu installed on that, but when i built this new pc i keep getting the same error message when booting from a disc:

Installation Failed
Boost.Python error in job "machineid"
Command 'systemd-machine-id-setup' returned non-zero exit status 127.
systemd-machine-id-setup:error while loading shared libraries: /lib/x86_64-linux-gnu/
libdevmapper.so.1.02.1: invalid ELF header
Traceback
File "/usr/lib/x86_64-linux-gnu/calamares/modules/machineid/main.py", line 64, in run 
check_target_env_call("systemd-machine-id-setup")
File "<string>", line 4, in <module>

Not sure if it matters, but 
- motherboard: Gigabyte GA-970-DS30
- RAM: 4 GB DDR3
- CPU: AMD FX-6300 3.5 GHz
- PSU: 500W
- HDD: 500 GB

(If i did something stupid or wrong i have no idea what im doing really and im lost as hell so any help is appreciated)

---

### Post by CelticWarrior on 2020-01-31
It's not clear what you're trying to do. Are you trying to boot the old installation or are you trying to boot a live session to install from scratch in a new drive (recommended considering the hardware changes)?

---

### Post by crispycat on 2020-01-31
I erased the old hdd, and tried a fresh install, and got nowhere (not sure if it was the same error message), got my new hdd and consistently got that error when trying a fresh install

---

### Post by CelticWarrior on 2020-01-31
If the error is during boot of the live session it suggests serious errors in that media.

Always use a known good USB stick. Check the downloaded ISO for errors. The following tutorials should help you create bootable media properly:

[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

---

### Post by crispycat on 2020-01-31
I'm using a cd boot, could it be a bad download? or is it most likely when i'm burning the cd?

---

### Post by TheFu on 2020-01-31
> **crispycat said:**
> I erased the old hdd, and tried a fresh install, and got nowhere (not sure if it was the same error message), got my new hdd and consistently got that error when trying a fresh install

The disc might be corrupt or scratched.  Which release is it?  Really old Ubuntu isn't supported. Best to start with 18.04 today and probably running XFCE, LXDE, or Mate.  Lubuntu 18.04 is fine.  Be aware that 18.04 Lubuntu is the last LXDE version. That team decided to change to Qt-based GUIs after that point.

[https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)  is usually where I send people really new to Linux to gain a first, basic, intro.

---

### Post by crispycat on 2020-01-31
If my problem is just something with my drive, i'll try re-downloading and re-burning, along with a usb boot

---

### Post by CelticWarrior on 2020-01-31
If you can boot from USB don't think twice, just use a USB stick instead.

---

### Post by yancek on 2020-01-31
Not sure if you meant you are using a DVD since the current Ubuntu iso files you need are more than twice the size of what will fit on a CD.  Before burning to a DVD or writing it to a usb with the appropriate software make sure you verify the download which is explained at the site, link below.  After clicking download for whichever release you use, there will be a link on the page on how to verify the download.

[https://ubuntu.com/download/desktop/thank-you?country=US&version=19.10&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?country=US&version=19.10&architecture=amd64)

You haven't indicated which release, the only supported releases presently available are the 2 with download links at the site above.

---

### Post by oldfred on 2020-01-31
Gigabyte 970 motherboards typically need UEFI update and change to iommu setting in UEFI.
Not sure if you still need iommu boot parameter settings, several have been posted.

 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0 uses this boot parameter: amd_iommu=on iommu=pt  & UEFI settings
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by CelticWarrior on 2020-01-31
> **oldfred said:**
> Gigabyte 970 motherboards typically need UEFI update and change to iommu setting in UEFI.
Not sure if you still need iommu boot parameter settings, several have been posted.

Since 18.04, at least, it installs without the IOMMU boot parameter.
Before, when the parameter was needed, the symptoms were nothing like what OP reported. If I remember correctly it used to be no keyboard/mouse input, no Ethernet...

---

