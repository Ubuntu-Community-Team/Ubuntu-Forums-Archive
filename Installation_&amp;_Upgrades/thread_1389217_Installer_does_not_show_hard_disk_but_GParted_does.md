---
title: "Installer does not show hard disk but GParted does"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by DeadMetal on 2010-01-24
I try to install Ubuntu on my new HTPC. I start Ubuntu with the Live CD and it boots fine. Then I want to start installing Ubuntu on my hard disk.

Unfortunately the installer does not see my hard disk which has 1 empty ext4 partition. However, it can be seen and managed in GParted. Please see the attachment.

What should I do now?

---

### Post by darkod on 2010-01-24
I can't be sure, but this usually happens if there are raid settings on the hdd. You are not running raid right?
First double check in BIOS whether any raid settings are enabled. Even with only one hdd that can put raid settings on it and 9.10 can detect that.
Second, while booted in the live desktop, in terminal execute (only if you are not running raid):

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

Reboot and start the installer again. See if that helped.

---

### Post by DeadMetal on 2010-01-24
It worked, thanks a lot! Indeed, now I remember having used this disk in the past in a RAID setup in another computer.

---

### Post by darkod on 2010-01-24
No problem. Glad you got it sorted. Enjoy ubuntu now. :)

---

### Post by jkonrad on 2010-02-03
I have a smiliar issue, but it is not solved by the process explained above, nor checking the BIOS. I have no RAID settings enabled at all. I have three SATA Drives. One for Win7, One is empty, One for data.

The all show in Win7. They all show on the live disk under gparted, but none of them show up when attempting an install of Ubuntu.

This is with the x64 9.10 Install CD. Can anyone help me? Thanks.

---

### Post by sbrus on 2011-04-04
Well, it work for me smoothly. I had one old hard disk and wanted to put it on old PIII for fake and test server. But I had problem that was mentioned above. After suggested commands everything worked perfect. I even did not restarted computer!

Thanks a lot darkod ):P

---

