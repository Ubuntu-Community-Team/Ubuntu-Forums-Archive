---
title: "Ubiquity crashed trying to install"
date: 2019-07-27
forum: Installation &amp; Upgrades
---

### Post by taslayer2 on 2019-07-27
so i downloaded ubuntu today to try and install it side by side with windows like Ive done a million times before... granted it was years ago.
anyway im running a dell xps 8930 and the install gets almost 99% of the way done and ubiquity crashes.
what commands can i use to help resolve this situation ie give you real linux gurus and idea of where to start

i was reading i may need AHCI drivers in windows which are not available apparently at least not on dells website... kind of at a loss here. haven't messed with any of this stuff in years

---

### Post by oldfred on 2019-07-28
Usually Dell does not start an install without AHCI mode. And yes you need the Windows AHCI driver for Windows.
Dell normally needs UEFI update and if a SSD firmware update for SSD.
Windows fast start up must be off. Best to have UEFI fast boot off also.

       Dell 9380 Dell has 18.04 image with correct drivers
[https://askubuntu.com/questions/1136409/new-xps-13-9380-with-ubuntu-18-04-flicker-problems](https://askubuntu.com/questions/1136409/new-xps-13-9380-with-ubuntu-18-04-flicker-problems)
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

General UEFI install instructions in link in my signature below.

      
 Windows AHCI instructions
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
[https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html](https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html)

---

### Post by taslayer2 on 2019-07-28
i can boot into live CD no issue while using uefi
ubuntu can see my windows partition etc etc etc
the install procedure runs just fine but just dies at the end?
would that still have something to do with bios settings?
also noting most of these guides are all laptop based, I'm running a desktop... that dell offers no image for?

---

### Post by oldfred on 2019-07-28
If at end, is it the install of grub?
And then are you installing in UEFI mode?
If UEFI, you need an ESP - efi system partition for grub to correctly install.

Otherwise it may just be a bad download of the ISO, or flash drive has error so not correct for installing. Some re-download, use different tool to create installer, use different USB port or use different flash drive, and then it works. No consistent fix, just one or several of a variety of changes & then it works.

---

### Post by taslayer2 on 2019-07-29
i would assume it to be the install of grub, because if i try to install again it recognizes the ubuntu install
ive tried 18.04 and 19.04
ill try a different flash drive and port.

ive been trying this guide if it helps
[https://hackernoon.com/installing-ubuntu-18-04-along-with-windows-10-dual-boot-installation-for-deep-learning-f4cd91b58557](https://hackernoon.com/installing-ubuntu-18-04-along-with-windows-10-dual-boot-installation-for-deep-learning-f4cd91b58557)

ill post results a little later today

---

### Post by oldfred on 2019-07-29
Guide seems ok.
You do not need swap partition, now as Ubuntu creates a swap file.

Installer should use the ESP - efi system partition that Windows has, unless you installed Windows in BIOS mode and now you are installing Ubuntu in UEFI mode. Pre-installed by Dell would be UEFI as Microsoft has required vendors to install in UEFI mode since Windows 8 released in 2012.

---

### Post by taslayer2 on 2019-07-29
turns out just a crap usb drive. put the same iso i had on a different drive, differet port. installed no issue.
i feel like an idiot for not trying that in the first place. thanks

---

