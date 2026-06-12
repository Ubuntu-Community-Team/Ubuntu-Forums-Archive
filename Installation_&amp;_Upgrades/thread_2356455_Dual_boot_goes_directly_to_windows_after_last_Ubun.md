---
title: "Dual boot goes directly to windows after last Ubuntu update"
date: 2017-03-23
forum: Installation &amp; Upgrades
---

### Post by rgara on 2017-03-23
I've been running a dual boot Ubuntu/windows laptop fine for several months. Yesterday, I installed the most recent updates (see below). On the next reboot, the laptop booted directly to windows. The only way I can get to the Ubuntu bootloader is to press F11 during start-up to get to the windows bootloader prompt. I've tried to reset grub using grub-customizer, and then boot-repair. Neither worked. boot-repair created this boot repair summary ([http://paste2.org/xAgHHHWZ](http://paste2.org/xAgHHHWZ)).  Not sure what to do from here. The boot repair summary mentions something about the ubuntu boot files being far from the start of the disk? I'm wary about attempting to resolve because everything's been working fine with no changes by me, save the normal Ubuntu installs. 

history.log output from updates I installed yesterday:


```
Start-Date: 2017-03-22  08:45:43
Commandline: /usr/bin/unattended-upgrade
Upgrade: libc6-dbg:amd64 (2.23-0ubuntu5, 2.23-0ubuntu6), libc6-dev:amd64 (2.23-0ubuntu5, 2.23-0ubuntu6), libc6:amd64 (2.2
3-0ubuntu5, 2.23-0ubuntu6), libc6:i386 (2.23-0ubuntu5, 2.23-0ubuntu6), locales:amd64 (2.23-0ubuntu5, 2.23-0ubuntu6), libc
-bin:amd64 (2.23-0ubuntu5, 2.23-0ubuntu6), firefox-locale-en:amd64 (52.0+build2-0ubuntu0.16.04.1, 52.0.1+build2-0ubuntu0.
16.04.1), libc6-i386:amd64 (2.23-0ubuntu5, 2.23-0ubuntu6), libc-dev-bin:amd64 (2.23-0ubuntu5, 2.23-0ubuntu6), libxml2:amd
64 (2.9.3+dfsg1-1ubuntu0.1, 2.9.3+dfsg1-1ubuntu0.2), multiarch-support:amd64 (2.23-0ubuntu5, 2.23-0ubuntu6), libfreetype6
:amd64 (2.6.1-0.1ubuntu2, 2.6.1-0.1ubuntu2.1), firefox:amd64 (52.0+build2-0ubuntu0.16.04.1, 52.0.1+build2-0ubuntu0.16.04.
1)
End-Date: 2017-03-22  08:46:01

Start-Date: 2017-03-22  16:24:24
Commandline: aptdaemon role='role-commit-packages' sender=':1.135'
Upgrade: init:amd64 (1.29ubuntu3, 1.29ubuntu4), init-system-helpers:amd64 (1.29ubuntu3, 1.29ubuntu4), gir1.2-gtk-3.0:amd6
4 (3.18.9-1ubuntu3.1, 3.18.9-1ubuntu3.2), libc6-dbg:amd64 (2.23-0ubuntu6, 2.23-0ubuntu7), libc6-dev:amd64 (2.23-0ubuntu6,
 2.23-0ubuntu7), libgtk-3-common:amd64 (3.18.9-1ubuntu3.1, 3.18.9-1ubuntu3.2), grub-common:amd64 (2.02~beta2-36ubuntu3.7,
 2.02~beta2-36ubuntu3.8), libgtk-3-0:
amd64 (3.18.9-1ubuntu3.1, 3.18.9-1ubuntu3.2), flatpak:amd64 (0.8.3-0alexlarsson1~xenial, 0.9.1-0alexlarsson1~xenial), gnome-software:amd64 (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1, 3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1), slack-desktop:amd64 (2.5.1, 2.5.2), google-chrome-stable:amd64 (56.0.2924.87-1, 57.0.2987.110-1), libc6:amd64 (2.23-0ubuntu6, 2.23-0ubuntu7), libc6:i386 (2.23-0ubuntu6, 2.23-0ubuntu7), grub2-common:amd64 (2.02~beta2-36ubuntu3.7, 2.02~beta2-36ubuntu3.8), locales:amd64 (2.23-0ubuntu6, 2.23-0ubuntu7), grub-efi-amd64-bin:amd64 (2.02~beta2-36ubuntu3.7, 2.02~beta2-36ubuntu3.8), libgtk-3-bin:amd64 (3.18.9-1ubuntu3.1, 3.18.9-1ubuntu3.2), libc-bin:amd64 (2.23-0ubuntu6, 2.23-0ubuntu7), ubuntu-software:amd64 (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1, 3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1), libc6-i386:amd64 (2.23-0ubuntu6, 2.23-0ubuntu7), libgail-3-0:amd64 (3.18.9-1ubuntu3.1, 3.18.9-1ubuntu3.2), grub-efi-amd64:amd64 (2.02~beta2-36ubuntu3.7, 2.02~beta2-36ubuntu3.8), libc-dev-bin:amd64 (2.23-0ubuntu6, 2.23-0ubuntu7), grub-efi-amd64-signed:amd64 (1.66.7+2.02~beta2-36ubuntu3.7, 1.66.8+2.02~beta2-36ubuntu3.8), multiarch-support:amd64 (2.23-0ubuntu6, 2.23-0ubuntu7), libexiv2-14:amd64 (0.25-2.1, 0.25-2.1ubuntu16.04.1), gnome-software-common:amd64 (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1, 3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1)
End-Date: 2017-03-22  16:25:01
```

---

### Post by oldfred on 2017-03-23
Ignore warning on too far from start of drive, that is for very old IDE systems in BIOS mode. Never seen it as an issue on newer UEFI systems.
We need to file a bug report on Boot-Repair to suppress that warning on new systems.
We also need more info on NVMe drives as they are not fully parsed.

Grub says it reinstalled ok.
Your UEFI shows Windows as first or default boot. 
See line207, and grub reinstall did make Ubuntu first as per line 738
Does Ubuntu now boot?

Windows updates will make Windows first in boot order. And those may be hidden updates, so just booting Windows may change your boot order.
You can change back with efibootmgr.

You can just run the UEFI boot list:
sudo efibootmgr -v

       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok. 2,1 is just an example, use correct entries show by the efibootmgr -v.
sudo efibootmgr -o 2,1
see also 
man efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

---

### Post by rgara on 2017-03-23
I really appreciate the reply!

I don't think a windows update could have changed anything because I barely boot to windows. The only time in the last month I've booted to windows was after I installed the last Ubuntu update and the following reboot took me directly to windows.

I can boot to Ubuntu, but I have to press F11 during start-up to get to what I believe is the windows boot manager. If I power up and do nothing, boot goes directly to windows. I don't see the typical Grub boot manager at all.

Just so I get this right ... with this output

```
efibootmgr -v
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0000,0001
Boot0000* Windows Boot Manager	HD(1,GPT,7fd6e48c-1910-480d-b861-c20d6813ed6b,0x800,0x96000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...5................
Boot0001* ubuntu	HD(1,GPT,7fd6e48c-1910-480d-b861-c20d6813ed6b,0x800,0x96000)/File(\EFI\UBUNTU\SHIMX64.EFI)
```

Assuming I don't need to specify hex values, I would execute:

```
sudo efibootmgr -o 1, 0
```

To put Ubuntu first?

---

### Post by oldfred on 2017-03-23
Spaces can be an issue. I do not think there is a space after comma.

What brand/model system?
Some have modified UEFI to only boot by description. That is specifically not allowed in UEFI standard, but description seems to always be "Windows Boot Manager" for some reason.
For those systems we have multiple work arounds depending on configuration.
Most dual booting use the fallback or hard drive boot entry that still seems to work. That is the same UEFI entry used for booting all external devices or /EFI/Boot/bootx64.efi. We just make that be shimx64.efi to boot Ubuntu/grub.

Even though I do not dual boot Windows I add a hard drive entry using efibootmgr and have no issues directly booting the ubuntu entry with my system:

```
Boot0001* UEFI hard drive    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\BOOT\BOOTX64.EFI)
```

The bootx64.efi is shimx64.efi or possibly grubx64.efi that only works if secure boot is off. I have used both, but have secure boot off.

---

### Post by rgara on 2017-03-23
It is an MSI Gaming Stealth Pro.

I executed sudo efibootmgr -o 1,0 The command showed success, but on a reboot it went directly into Windows again.

Like I mentioned above, the dual boot has  been working fine for several months. I do recall setting Fast Boot to Disabled when I first in stalled Ubuntu. I just checked BIOS and noticed a setting called "UEFI HARD DISK DRIVE BBS PRIORITIES". When I selected that, I noticed the windows boot manager was listed first and Ubuntu second. I switched those and now it is back to working fine.

Have no idea what would have caused that to change?

At any rate, I'm back to normal. Thanks for help!

---

