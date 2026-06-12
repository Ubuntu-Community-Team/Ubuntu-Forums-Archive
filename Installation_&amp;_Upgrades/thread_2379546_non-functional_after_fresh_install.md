---
title: "non-functional after fresh install"
date: 2017-12-06
forum: Installation &amp; Upgrades
---

### Post by lbernard on 2017-12-06
Computer: Alienware 13 R3
CPU: i7-7700HQ
Optimus: yes (unfortunately)
HDD: 2 NVMe M.2 drives, one stock, one samsung 960pro

Attempting to dual-boot with windows 10

Symptoms are various, but the linux install is unusable.

I installed multiple versions (17.10, 17.04, 16.04.3) on the new nvme drive.  all have similar issues.

The USB install drive works, I can get to the desktop, see the nvme drives in /dev, partition the drive, install, etc.  Reboot or shutdown from the usb drive sometimes fails and I get output like:
```
NMI watchdog: BUG: soft lockup - CPU#<i> stuck for 23s! [plymouthd:6010]
INFO: rcu_sched self-detected stall on CPU
```

BIOS Settings:
updated to latest bios
Sata Operation = AHCI
boot list option = UEFI
Secure Boot = Disabled
legacy option roms = Enabled

Install procedure:
Boot to USB Install drive, Install ubuntu to new nvme drive.
I have tried partitioning the drive and assigning /, /home, and swap, and just letting the installer have its way with the partitions.  I have reformatted and re-installed many times.
Installation completes successfully.
reboot:  this sometimes fails, with the above mentioned cpu soft lockup.

Startup fails:
I have now gone through every type of startup failure I know of.
boot to 'grub>' prompt, and was able to return to the login screen.
boot to (initramfs), rebooting from here sometimes causes the same soft lockup
boot to login screen:
    I am able to ctrl+alt+f1 to get to a command prompt
    I have been unable to connect to wifi to run an apt update/upgrade
    Logging into the desktop results in a hard lockup with no interface.  changing to another tty session fails, ctrl+alt+delete fails, power off fails, must hold power button to force power off.

I suspected bad hardware, but windows boots up without issue, and runs prime95 for 20-30 minutes without any errors.

I'd appreciate any help you can offer.  I'd prefer to get ubuntu 17.04 or 16.04 running (for NVIDIA CUDA toolkit support), but i'll use 17.10 if I must.

---

### Post by oldfred on 2017-12-06
Many Dell with NVMe drives have required both UEFI updates & SSD firmware updates.

 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr)

---

