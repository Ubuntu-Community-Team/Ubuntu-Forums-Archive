---
title: "Fresh install boot problem"
date: 2018-07-20
forum: Installation &amp; Upgrades
---

### Post by thomas_j_marshall2 on 2018-07-20
I previously dual-booted uibuntu with windows 10 on a 240gb SSD.  I have a spare 120 ssd so removed ubuntu from the 240 and installed on the 120 but can't get ubuntu to boot.  I get grub with instructions to tab for possible commands.  I can still boot windows if I change in uefi but the ubuntu boot won't work.  I had /, home and swap and it gave an error that I needed a uefi bios boot partition which I ignored.  When it didn't boot I created said partition but still no boot.  Any idaes?

---

### Post by oldfred on 2018-07-20
Is your Windows 10 install UEFI? If from manufacturer it will be UEFI. But if you installed it yourself, it will only depend on whether you booted install media in UEFI or BIOS boot mode.

UEFI installs to second drives with Ubuntu use the ESP - efi system partition on drive seen as sda, or first drive if NVMe type.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by thomas_j_marshall2 on 2018-07-20
> **oldfred said:**
> Is your Windows 10 install UEFI? If from manufacturer it will be UEFI. But if you installed it yourself, it will only depend on whether you booted install media in UEFI or BIOS boot mode.

UEFI installs to second drives with Ubuntu use the ESP - efi system partition on drive seen as sda, or first drive if NVMe type.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)Yes, uefi, I installed w10 myself.  S

---

### Post by thomas_j_marshall2 on 2018-07-20
[http://paste.ubuntu.com/Vp75vR7vRN/](http://paste.ubuntu.com/Vp75vR7vRN/)

---

### Post by oldfred on 2018-07-20
Link to pastebin does not work.

If at grub>
Can you do this?
       manual boot, change hd0, gpt8 to yours, probably hd1 or hd2 and then partition with install, but depends on how UEFI sees drives which often depends on SATA port used:
grub> set root=(hd0,gpt8)
grub> configfile /boot/grub/grub.cfg
[https://ubuntuforums.org/showthread.php?t=2396045](https://ubuntuforums.org/showthread.php?t=2396045)
$ sudo apt-get install grub-efi-amd64
$ sudo update-grub

---

### Post by thomas_j_marshall2 on 2018-07-22
Well I abandoned ubuntu on the separate ssd.  I have installed mint alongside w10 on one ssd and it had the same problem.  I managed to boot with a grub rescue disc and was able to boot mint and update grub.  The boot menu shows ubuntu rather than mint, obviously boots mint, how can I change this?

---

### Post by Dennis N on 2018-07-22
As an explanation, the main Linux Mint editions use the Ubuntu ubiquity installer, so the OS is labeled 'Ubuntu' in the UEFI boot menu, even if the grub menu entry is titled "Linux Mint ....". Also, the grub folder in the EFI system partition will be 'Ubuntu' as well. That's so it stays compatible with Ubuntu path names for updates from Ubuntu repositories.

---

### Post by oldfred on 2018-07-22
If you still have Ubuntu SSD connected, run this:
sudo update-grub

If not run the Boo-Repair summary report again and post link. Check it works also.

---

### Post by thomas_j_marshall2 on 2018-07-26
Hi guys, thanks for all your help and suggestions, greatly appreciated.  I just want to update you.  I re-installed ubuntu on the separate 120 ssd and specified an efi partition and that has worked.  I didn't even have to update grub, after installing the reboot showed the grub menu  with windows 10 so happy days.  Thanks again for all your help.

I have another problem though, it's what started me re-installing in the first place.  I have on-board radeon graphics and a recent update left me with a very low resolution, couldn't use the radeon set up at all so I bought and installed a nvidia card.  Initially Ubuntu was running x-org so I installed the nvidia proprietary and it crashed Ubuntu.  It worked to a certain version but an update made it unusable.  In my new installation now I am on x-org but at login the mouse freezes and entering password using tab is soooo slow.  Once in everything is OK.  This happened on my old install using both x-org and nvidia.  Any ideas?

---

### Post by oldfred on 2018-07-26
Best to post that in new thread with the video issue as the title.
Post brand/model system and which nVidia card.
Also what kernel as there seem be issues with 18.04 and -24 kernel.

---

