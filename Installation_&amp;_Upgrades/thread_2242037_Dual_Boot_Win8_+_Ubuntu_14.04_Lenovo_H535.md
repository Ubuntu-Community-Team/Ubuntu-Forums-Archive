---
title: "Dual Boot Win8 + Ubuntu 14.04 Lenovo H535"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by howdy-ratzlaff on 2014-08-30
I've been trying for days and days to get dual boot working on my Lenovo H535.

I know this is possible because I've done it in the past with Ubuntu 10

No matter what I try after installing Ubuntu 14.04 from the live USB I boot straight to Win8 and any bootloader entries I create for Ubuntu even after attempting boot-repair and easybcd point to the root partition just give me a Windows stop error of 0x0..07b

I'm tearing my hair out over this.

Secure boot is disabled, quick-boot, fast-boot also disabled.

I've tried to force the entry with easyBCD I've also tried to get it fixed via the liveUSB and boot-repair recommended.

My pastebin is as follows: [http://paste.ubuntu.com/8186316/](http://paste.ubuntu.com/8186316/)

Any help at all on this is greatly appreciated.
I would install Ubuntu by itself, but my understanding is that the H535 may have a bootloader whitelist in it's firmware for Win8 and Win7 bootloaders, so I have to get to Ubuntu through the Win8 bootloader, GRUB or standalone Ubuntu installs even on drives that verify working to boot Ubuntu in other computers will not boot on this thing and I get a 1962 no OS found error.

I tried talking to Lenovo's support engineers about it, but my question gets brushed off for more pressing matters, because their H535 isn't Ubuntu or Linux certified at all.
They sent me free Win8 recovery media, so I can't hate them for it, but I've had Ubuntu working on this machine before through the Win8 bootloader. (The way it worked is the Win8 Bootloader had an Ubuntu entry, when selected, would boot GRUB and then I'd have to select Ubuntu in GRUB to actually boot up.

I don't mind that setup if it's the only way to get Ubuntu working, but I can't even get that functionality going.
I'm begging you guys, anything, I've even asked on IRC and read pages and hours of online fixes and blogs.

---

### Post by howdy-ratzlaff on 2014-08-30
I fixed it. So here's what I had to do.

I had to do a clean install of Windows 8.

Then in the BIOS I turned Secure Boot Off, but I left UEFI boot ON (AKA CSM Enabled option in the startup tab)

I installed Ubuntu by booting the liveUSB

Using the free space on the drive I made a /, /home, and swap area.
Then I installed.

After reboot, GRUB worked, had Ubuntu as an option and a Windows Bootloader option.

Ubuntu boots 14.04 just fine, I rebooted and tested and Windows Bootloader loaded Win8 just fine.

Fantabulous.

---

