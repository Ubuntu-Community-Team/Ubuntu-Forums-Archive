---
title: "Booting problems not resolved after boot repair"
date: 2020-02-15
forum: Installation &amp; Upgrades
---

### Post by siachin on 2020-02-15
I installed Ubuntu 18.04 LTS Desktop OS alongside my (originally) Windows 10 laptop. All works well till I boot into Windows. Then Windows boots ok for the first time, but after restart the boot options do not show up and I am unable to boot into either OSes. 

I ran boot repair by using "try Ubuntu" option from a live CD, but it did not seem to fix it. Here is the boot-repair report: [https://paste.ubuntu.com/p/sXxysf4M8B/](https://paste.ubuntu.com/p/sXxysf4M8B/)

I am using a Lenovo ideapad 110, and am only a beginner with Ubuntu.

---

### Post by EuclideanCoffee on 2020-02-16
This might sound funny but when you shut down Windows, do you restart or shutdown? Shutdown will cause your computer to hibernate, and the grub screen won't appear once you start your machine. You'd need to restart Windows 10 to actually shut off the operating system.

---

### Post by siachin on 2020-02-20
Sorry for the late reply, I had to take emergency measures so did a "factory reset" (an option available on my laptop) and now I only have windows. 

To answer your question, I am pretty sure that I lost access to the boot menu whether I restarted, shut down, or hard shut down (by long pressing the power button). I noticed that whenever I logged into windows, the boot order in the BIOS would change, and booting up next time would fail because the system was trying to boot from "EFI network". Each time I can manually change the boot order in BIOS to boot from windows, but it changes again next time. Also, I never do see the grub menu again. 

I have tried disabling the following settings (both individually and collectively) as well without much effect: 

1. "Secure boot" from the BIOS
2. "Fast Boot" from BIOS
3. "Fast Startup" from Windows 10

Yes I am planning to fresh install Ubuntu one more time, but I am pretty sure that I will lose access to Linux if I ever boot into windows again.

---

### Post by oldfred on 2020-02-20
You need to make sure Windows fast start up is off.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Have you updated UEFI from Lenovo for your system?

Lenovo 110s  Experience Installing and Using Linux on Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)
Older versions, may have some of same issues? But had 32 bit UEFI on 64 bit system.
LENOVO Ideapad 100 Laptop 16.04 Dual Boot 
[https://ubuntuforums.org/showthread.php?t=2336544](https://ubuntuforums.org/showthread.php?t=2336544)
LENOVO Ideapad 100S Laptop  32 bit UEFI bootia32.efi
[https://ubuntuforums.org/showthread.php?t=2350606](https://ubuntuforums.org/showthread.php?t=2350606)

---

### Post by dragonfly41 on 2020-02-20
> [COLOR=#000000]but I am pretty sure that I will lose access to Linux if I ever boot into windows again.[/COLOR][COLOR=#000000]

You stand a better chance of avoiding that "bug" by installing Ubuntu in an external drive, rather than co-habiting with Windows in /dev/sda.
It means that you have to place a second drive in a USB container but I consider that it is worth the cost to avoid these hassles. Just switch off the external drive before booting up Windows.[/COLOR]

---

### Post by siachin on 2020-02-21
Thank you all for your suggestions. Installing in an external drive sounds less nerve wrecking to me and something I am willing to live with. I will gladly accept it as an answer. 
:)

---

### Post by dragonfly41 on 2020-02-21
As an added note, refer to [this thread]("https://forums.linuxmint.com/viewtopic.php?t=287353").  Using Gparted in LiveUSB ensure that first partition of the external drive is EFI (500 MB) fat32 mount point /boot/efi with boot flags - boot, esp.  The next partition can be for Ubuntu (ext4). And the next a swap partition.  I also created an NTFS partition at end which allows me to share files with windows (on the rare occasions I use it). For good measure I also installed rEFInd.
I have a 1 TB external SSD so configured.

---

### Post by siachin on 2020-02-22
Thanks and very much appreciated :-)

---

