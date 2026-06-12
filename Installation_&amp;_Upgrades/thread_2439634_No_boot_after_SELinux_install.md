---
title: "No boot after SELinux install"
date: 2020-03-30
forum: Installation &amp; Upgrades
---

### Post by John_Rose on 2020-03-30
Hello,
  I have Ubuntu 18.04 running on an ASUS VivoBook with a NVIDIA GeForce MX150 video card.
  
  I wanted to install SELinux and was told that for that I first had to uninstall apparmor which I did without problems. Then when I installed SELinux and rebooted, the system hung up (no boot after 15 minutes, just the little moving dots).
 
  I could reboot in recovery mode and all worked fine except that I only have 800x600 pixels with no choice for screen resolution.

  I tried all of the recovery options (reinitiating grub, fix broken packages, file system check, etc.) but no change, not able to boot normally.
  
  I uninstalled SELinux without problems then ran apt-get autoremove, apt-get dist-upgrade, apt-get upgrade and apt-get update, and reinstalled libgl1-mesa-dri (which seems to have something to do with screen rendering) but still the same problem (system runs in recover mode with reduced screen resolution but won't boot normally).

  The last lines of my "sudo apt install selinux" command (in French) were:

  Traitement des actions différées (« triggers ») pour initramfs-tools (0.130ubuntu3.9) ...
  update-initramfs: Generating /boot/initrd.img-5.3.0-42-generic
  I: The initramfs will attempt to resume from /dev/sda6
  I: (UUID=72f71923-ffe0-45b0-8ba8-cfda78b4d5b7)
  I: Set the RESUME variable to override this.
  
  The device name and UUID for the swap partition (I have a partition rather than a file) were good, but I saw that there was no "/etc/initramfs-tools/conf.d/resume" file so I added it according to  [https://askubuntu.com/questions/1116778/how-to-set-the-resume-variable-to-override-these-issues](https://askubuntu.com/questions/1116778/how-to-set-the-resume-variable-to-override-these-issues) , but still same problem.
  
  I can't see whether this is a resume from swap problem, or a video package problem or something else.
  
  Could someone please help? Thanks and best regards, John

---

### Post by John_Rose on 2020-03-30
I found the answer at
[COLOR=#000080]_[https://askubuntu.com/questions/1180868/after-installed-selinux-system-stuck-not-booting](https://askubuntu.com/questions/1180868/after-installed-selinux-system-stuck-not-booting)_[/COLOR]
  The solution works perfectly - SELinux should not be installed under Ubuntu.
Best regards,
John

---

