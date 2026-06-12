---
title: "Ubuntu 12.04.3 Server x64 System Boots to Grub CLI, Not Menu (Using RAID6, EFI)"
date: 2013-11-28
forum: Installation &amp; Upgrades
---

### Post by asayler on 2013-11-28
I have a fresh Ubuntu 12.04.3 Server (x64) install that I can't seem to convince to boot to the grub menu. I've re-installed grub several times at this point, both manually and using a 12.04.3 Desktop LiveCD with boot-repair. Every time I boot however, I land on the grub terminal, never getting to a normal grub boot menu. From the terminal, I'm able to boot the system manually by running:

```

set root=(md/0)
linux /boot/vmlinuz-3.8.0-29-generic root=/dev/md/0
initrd /boot/initrd-3.8.0-29-generic
boot

```

md0 is a 5-drive md raid6 array. It holds root (including /boot). There is a second md1 raid6 array, but it's just used for /srv, so it shouldn't really be relevant here. Each of the five drives has three partitions, a 1 GB fat32 EFI partition, a 25 GB raid partition (used to build md0), and 1 TB raid partition (for md1). The grub EFI executable is installed to the sda1 EFI partition. The UEFI firmware is set to load the Grub executable stored there. I have SecureBoot enabled, so the signed grub shim executable is also in use.

Since I can boot manually, I know grub is capable of doing what I want. But I have no idea why it won't read the config file in /boot/grub and display the normal Grub menu. Like I said, I've re-installed it several time already to no avail. Maybe some extra pairs of eyes will see my issue? This is teh first time I've done the full trifecta of /boot on raid6 + UEFI + SecureBoot, and it does not seem to want to cooperate.

Pre fresh boot-repair run: [http://paste.ubuntu.com/6491565/](http://paste.ubuntu.com/6491565/) (boots to grub terminal)
Post fresh boot-repair run: [http://paste.ubuntu.com/6491595/](http://paste.ubuntu.com/6491595/) (still boots to grub terminal)

Any thoughts?

Cheers,
Andy

P.S. Happy Thanksgiving to those of you in the US.

---

### Post by rackit on 2013-11-28
This may, or may not help: [http://is.gd/tukk5P](http://is.gd/tukk5P)

---

### Post by asayler on 2013-11-29
> **rackit said:**
> This may, or may not help: [http://is.gd/tukk5P](http://is.gd/tukk5P)

I'm using Linux software RAID (md raid). Thus, that article doesn't apply. But thanks for the thought.

Other thoughts?

---

### Post by rackit on 2013-11-29
NP - it had some ainfo bout getting RAID devices to boot.

---

### Post by steeldriver on 2013-11-29
I've never used RAID for a boot partition but iirc it's important to run "update-initramfs -u" after creating / changing the RAID config to write it to the initial RAM image - did you remember that step?

---

### Post by oldfred on 2013-11-29
I do not know RAID.
This also had LVM, but says the issue is an incorrect UUID in the grub.cfg that is in the efi partition. See #5 & 6

[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

---

### Post by asayler on 2013-11-29
> **oldfred said:**
> This also had LVM, but says the issue is an incorrect UUID in the grub.cfg that is in the efi partition. See #5 & 6

[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

This seems to be getting closer to the underlying issue. That bug report references a grub.cfg file located in the EFI directory (i.e. /boot/efi/EFI/ubuntu/grub.cfg). When I setup grub, there was no grub.cfg file in /boot/efi/EFI/ubuntu/, only the grubx64.efi and shimx64.efi files. The only grub.cfg file I could find is the normal primary one located at /boot/grub/grub.cfg.

Thus, I crafted a workaround by manually creating a new grub.cfg file in /boot/efi/EFI/ubuntu/ with the following content:

```

set prefix='(md/0)/boot/grub'
set root='(md/0)'
configfile /boot/grub/grub.cfg

```

This grub.cfg file just serves to bootstrap the loading of the main grub.cfg file located at /boot/grub/grub.cfg.

This seems to solve the problem, although I have no idea why it didn't work be default during the initial grub install or subsequent re-installs. It seems that the grub executable is looking for a grub.cfg file in EFI directory, but the grub installer, etc is not creating this file by default. I don't know if this is a bug in the installer, or something strange about this particular setup.

On my other EFI systems, there also doesn't seem to be a grub.cfg file in the /boot/efi/EFI/ubuntu/ directories, just the grubx64.efi executable. But none of those systems use secure boot or raid, so maybe this only affects secure boot and/or raid systems? I assume the grub executable on those other systems knows to load the /boot/grub/grub.cfg by default, instead of looking for a grub.cfg file in the EFI directory.

Anyone with insight into this? Should I file a bug report against grub?

---

### Post by oldfred on 2013-11-30
Update:
Just found this in checking bugs.
 grub doesn't boot with efi and md raid root

    [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)

Your solution seems a bit different, and you may want to suggest it as an alternative.

nevermind see above.
I might file a bug report. At least someone knowledgeable will look at it. 
If you post bug report here I will try to get others with efi & RAID to also add to report as they often do not do much with only one report.

 bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)
      
 Check bugs
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

---

### Post by asayler on 2013-11-30
> **oldfred said:**
> 
Just found this in checking bugs.
 grub doesn't boot with efi and md raid root

    [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)

Your solution seems a bit different, and you may want to suggest it as an alternative.


Good find. That looks like the same issue I'm having. I globbed onto that bug report and noted my workaround.

I'll mark this as solved since it looks like we're stuck waiting on the bugfix or using the patch or workaround.

Thanks!

---

