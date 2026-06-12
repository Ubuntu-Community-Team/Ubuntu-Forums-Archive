---
title: "Need Help Fixing Ubuntu Boot into Grub Issue"
date: 2024-07-13
forum: Installation &amp; Upgrades
---

### Post by magichenry12 on 2024-07-13
I have dual boot of Ubuntu 24.04 and Windows on my laptop. Recently,  ubuntu stopped booting normally and instead it shows the gnu grub and I  have to type 'exit exit' in order to open the boot menu. As such, I have  went to [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) to create a boot  info here: [https://paste.debian.net/hidden/7c3330f6/](https://paste.debian.net/hidden/7c3330f6/). Can somebody help  me to fix my ubuntu boot given my boot info? Thanks! :)

---

### Post by tea for one on 2024-07-13
```
======================== nvme0n1p4/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /[COLOR="#0000FF"]dev/nvme0n1p6[/COLOR] during curtin installation
/dev/disk/by-uuid/bc19799c-062a-4be8-b690-ff733e5cf05a / ext4 defaults 0 1
# /boot/efi was on /dev/nvme0n1p1 during curtin installation
/dev/disk/by-uuid/5A53-8DD8 /boot/efi vfat defaults 0 1
/swap.img	none	swap	sw	0	0
```

What happened to partition nvme0n1p6?

---

### Post by magichenry12 on 2024-07-13
nvme0np6 has never existed in my ubuntu. I remember that I ran fdisk -l when my Ubuntu was working, and there was no nvme0np6

---

### Post by oldfred on 2024-07-13
The UUIDs all look like they now use p4. So ok.

But it now shows UEFI Secure boot is on. 
Was it on when you installed Ubuntu, so you have signed versions of kernel & grub?

Windows update or UEFI firmware update may reset to defaults & turn Secure Boot on.

---

### Post by magichenry12 on 2024-07-13
Secure boot was definitely on when I installed Ubuntu in the dual boot. Also, I am a noob, and while looking at ‘[https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot’](https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot’) I used  ls and my Ubuntu seems normal (with home, boot, root, bin folders in (hd0,gpt4)). So what is the problem that might be causing grub to load instead of the Ubuntu?

---

### Post by oldfred on 2024-07-13
What brand/model system? What video card/chip?

Do you have latest UEFI firmware and NVMe firmware from vendors?
Compare to vendor's support site for your model.
sudo dmidecode -s bios-version
udisksctl status

---

### Post by magichenry12 on 2024-07-14
I am using i7-11390h 16gb ram Honor HGE-WX6 MagicBook V14 (iGPU graphics), with 1tb hdd/ssd? (confused because bios says hdd device and windows says ssd) and InsydeH2O Rev5.0 UEFI bios (locked with only ‘main’ tab available). Yes, my bios is updated to latest version 1.17, NVMe firmware also updated. (Side note: weirdly, after my laptop boot to grub as usual today, using ls lists (hd0,gpt1-4) AND (hd1,gpt1-4), and I have no idea why hd1 popped up.)

---

### Post by oldfred on 2024-07-14
Did you have flash drive or other device installed?
Many systems promote flash drive to first device or hd0.
If then system worked that is then  on hd1, it may just be grub has correct UUID so it finally boots, but starts looking at hd1 when you have no other drives plugged in? 

Your udisksctl status should tell you all about drive.
Mine says this so Samsung and mounted as NVMe drive, not just SSD.
> [FONT=monospace][COLOR=#000000]Samsung SSD 970 EVO Plus 500GB 2B2QEXM7  S4P2NF0M514514L      nvme0n1 [/COLOR]
[/FONT]

---

