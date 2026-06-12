---
title: "UEFI Boot problem."
date: 2017-12-05
forum: Installation &amp; Upgrades
---

### Post by lostbuzzard99 on 2017-12-05
I'm a novice to Ubuntu, but loved it during the trial and decided to install dual boots on a couple of older computers. My goal was to have an operating system that required less strain on the hardware and resouces.  I've had success on installing it on two desktops and one had the challenge you mentioned.  I found that the problem was windows had already used 4 partitions.  Since one was solely for recovery, I created recovery discs (DVD or Thumb Drive), then verified which partition was the recovery one and used Partition Assistant to delete the recovery partition.  I then installed Ubuntu and chose a drive size for it that was a little less than half of what I had available.  My only challenge now, is on my laptop, the menu that comes up during the boot process that allows you to select to boot windows or Ubuntu, does not show up.  When the boot is set to Legacy, Ubuntu boots up and when the boot is set to UEFI, Windows boots up.  Rather than hitting escape to change the boot method, I would like to fix things to make that boot option menu come up.  Any help would be appreciated.

---

### Post by howefield on 2017-12-05
Post moved to its own thread.

---

### Post by yancek on 2017-12-05
That is expected behavior when you have one system installed UEFI (windows) and the other in the older MBR/Legacy mode.  Simplest way on a new install is to re-install.  Read the link below before you try to re-install since it is the official Ubuntu documentation on dual booting UEFI.  If you scroll down that page, there is a section on converting to UEFI if you want to try that,

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-12-05
You do not have to have both systems boot in same mode, but much easier.
And generally better to use whatever mode Windows is installed in UEFI or BIOS boot.
And some advantages to UEFI with gpt partitioning. But some vendors make it a bit more difficult as they violate UEFI standard. But we have found work arounds for those issues.

What brand/model system?
What video card/chip?

Most can just use Boot-Repair's advanced mode when booted in UEFI to convert Ubuntu from BIOS boot to UEFI boot. All it really does is uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI) and that reinstall changes some settings in Ubuntu.

How you boot install media UEFI or BIOS, andwhether Windows or Ubuntu is then how it installs. So if UEFI system always boot in UEFI mode.

If you do reinstall, just be sure to boot in UEFI mode and only use Something Else option to choose existing / (root) and if you have it as separate partition, existing /home(but do not check format).

---

### Post by lostbuzzard99 on 2017-12-07
Thank you to all who replied and offered solutions.  As I considered all the solutions offered, I implemented the following with success:
[LIST=1]
[*]I'm installing a dual boot  on to an brand new Acer Aspire 5 (A515-51-50RR)  Laptop running Windows 10, Intel Core i5 7200U 2.5 GHz with Turbo Boost up to 3.1GHz, 8 GB DDR4 Memory, initially 1TB HDD, which I am sharing half that HDD with Ubuntu.
[*]I had already installed Ubuntu under Legacy Mode  
[*]I rebooted and Hit F2 to get to the System Setup Utility menu and changed the mode to UEFI
[*]I inserted the USB boot drive that I had created to boot Ubuntu 16.04.3 LTS, and rebooted and hit F2 to get to the System Setup Utility menu
[*]Under the boot menu, I changed the order of boot OS so that the USB HDD was first on the list, then rebooted and followed the Ubuntu prompts to erase the previous Ubuntu install and reinstall alongside Windows
[*]I rebooted with the USB drive still inserted and I received a Kernel error that I cannot remember, but the computer was stuck with a black screen and two lines of this kernel error.
[*]I removed the USB drive and held the power button to shut down, I then turned on the power and Windows booted up with no problems, but no Ubuntu or Grub menu. 
[*]I used an alternate method to get to the System Setup Utility menu, thinking it would allow me to remove secure boot and assuming that would help (this was an unnecessary step).
[*]I noticed an option to enable F12 (under the main menu) during boot to allow the boot menu to display during the boot process.  I rebooted and this time hit F12 to get to a boot menu that showed (1. Windows and 2. Windows as my options), but I could not change the order of boot from this menu, 
[*]I assumed as before that this meant that each of these choices would boot windows. 
[*]I selected the second Windows option and it didn't boot to windows, but it did boot to Ubuntu Grub Menu that I was trying to get to
[*]I rebooted, selected F2 to get to the System Setup Utility Menu
[*]I changed the boot order so that the second Windows option booted first and now all is well. It booted to the Grub Menu and I can now Use Ubuntu as desired in a dual boot alongside Windows 10. My problem has been solved 
[/LIST]

---

### Post by oldfred on 2017-12-08
Not sure how you have it finally configured UEFI or BIOS.
But that is an UEFI system.

Normally with Acer you have to enable "trust" from with in UEFI of Ubuntu/grub's .efi boot files in ESP - efi system partition.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)

---

### Post by lostbuzzard99 on 2017-12-08
Not sure if the trust is set properly, but it is currently configured to boot Under UEFI mode with no problems. A friend suggested that I could install on a virtual machine, which could allow me to experience several versions of Linux simultaneously. Probably something I’ll explore next.

---

