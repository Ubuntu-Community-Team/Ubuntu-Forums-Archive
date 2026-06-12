---
title: "grub loader questions, absolutely not posted anywhere!"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by long6688 on 2012-10-01
Hi guys, i managed to install Lubuntu on an usb device (the idea was to create a portable linux)

1. After i finished the installation and update the system, when i restart, the grub menu present me with current linux and previous linux version as well. How do i clean up this menu? I want to keep the size small so How do i also clean up all trace of previous linux versions on the usb drive? such as backup

2. When i update Grub, i was asked to choose between install grub on SDA (i guess it is MBR) or sda1 (i guess it is boot sector of the active disk).
What should i choose? sda mbr or sda1 boot sector?

I googled the question and the response was mixed. Can the system bootup with a blank MBR and grub installed on sda1 boot sector?

THanks for your response.
Yours sincerely,

---

### Post by darkod on 2012-10-01
Grub almost always goes to the MBR since any computer expects to find the bootloder in the MBR. Put it on a partition (like sda1) and it will never boot, as simple as that. Especially if you want this portable usb to be bootable on any computer, the only correct answer is /dev/sda, the MBR of the usb.
Just make sure you don't put it on the MBR of the computer that you are working on.

The submenu Previous Versions in the boot menu doesn't mean previous linux versions. It means previous kernels from the same installation, they are grouped in a submenu called previous Versions and only one kernel, the latest is shown as a main option to boot from in the grub boot menu. All older kernels are in Previous Versions.
So, unless you installed twice on the stick, don't worry, you only have one single version.

---

### Post by oldfred on 2012-10-01
Welcome to the forums.

+1 on Darko's suggestions.

You can do some housecleaning.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

I always keep two kernels, just in case there is an issue with my current one.

Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
#current install:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
HOWTO: Remove Older Kernels via GUI (or CLI)
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

After running some of the same commands several times I now run a script occasionally with those commands.

---

