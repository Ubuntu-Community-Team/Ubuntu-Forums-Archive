---
title: "Broken bootloader after installing Ubuntu alongside Windows"
date: 2019-10-17
forum: Installation &amp; Upgrades
---

### Post by herthaner on 2019-10-17
Yesterday I installed Ubuntu 19.04 on my computer. As Windows 10 was already installed on it, I created a partition for Ubuntu and choose to install the Bootloader on /dev/nvme0n1. After doing so my computer booted Ubuntu per default, without showing a dual-boot menu. To boot Windows I had to press F12 when starting my computer and to choose the windows partition as boot partition. 

Then I realized that I had to downgrade to Ubuntu 18.04 because of compatibility issues, so I overwrote the Ubuntu 19.04 partition with an Ubuntu 18.04 installation. After doing this my computer doesn't boot any more unless I press F12 and select the boot partition manually. So I ran the Boot Repair tool according to this manual: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I chose the option "Recommended repair". Boot repair showed an notification "An error occurred during repair" and generated this output: [http://paste.ubuntu.com/p/F7YPZ5FFGn/](http://paste.ubuntu.com/p/F7YPZ5FFGn/).

What can I do to fix the boot loader, so that I can choose between Windows and Ubuntu when my computer is booting?

---

### Post by yancek on 2019-10-17
The boot repair output shows that windows is in "an unsafe state" which means you left it hibernated when you install Ubuntu.  That needs to be turned off and I don't know of any way to do that without booting into windows.  Are you able to boot either windows or Ubuntu now either from the BIOS boot option or the bootloader?  Until you find a way to turn off hibernation in windows, you will not be able to boot if from Grub.  You should mount the efi partition and take a look at the contents and probably post that info here.  It's /dev/nvme0n1p1

You have 2 entries for Ubuntu EFI but it shows a different UUID than the blkid output.  Did you do the last Ubuntu install UEFI?

---

### Post by oldfred on 2019-10-17
See line #204:
> Windows is hibernated, refused to mount.
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.

Windows fast start up sets hibernation flag and prevents grub from booting Windows.
Turn off fast start up in Windows & rerun grub2's os-prober.
It also looks like you still are using the open source nouveau driver, not the nVidia driver.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

The run this:
sudo update-grub


If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by herthaner on 2019-10-18
Thank you for your replies. I booted Windows from the BIOS and disabled fast startup option. Afterwards I booted Ubuntu from the BIOS and ran sudo update-grub. Unfortunately, after shutting down my computer is still not able do boot.

---

### Post by herthaner on 2019-10-18
Reinstalling Ubuntu solved my problem.

---

