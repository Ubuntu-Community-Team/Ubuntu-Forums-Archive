---
title: "How to prevent Ubuntu adding itself to Boot Menu of EFI partition"
date: 2023-05-09
forum: Installation &amp; Upgrades
---

### Post by panijsr on 2023-05-09
I have installed (full installation) Ubuntu 22.04 into external SSD and is working fine. I removed internal HDD during installation. All Ubuntu partitions (boot, EFI, root, home etc.) reside in external SSD. Post Ubuntu installation, I put the internal HDD back in its place. During normal usage, when I upgrade Ubuntu (sudo apt upgrade), it adds entry in the Boot Menu of the UEFI partition of my PC's Internal HDD.  This happens specifically when there is upgradation to newer Ubuntu kernel. How can I prevent Ubuntu to modify Boot Menu of my internal HHD? I do not have BIOS option to disable HDD.

---

### Post by oldfred on 2023-05-09
Is os-prober on?
I thought default now was off. But I turn it off as soon as I install and only add entries I want into 40_custom. I have multiple installs & do not want some of them in boot menu.

Change to true if now false or add line if you do not have it.
sudoedit /etc/default/grub
[FONT=monospace][COLOR=#000000]GRUB_DISABLE_OS_PROBER=true

After any change to grub:
sudo update-grub[/COLOR]


[/FONT]

---

### Post by panijsr on 2023-05-10
Yes OS prober is already OFF. This does not help though.

---

### Post by oldfred on 2023-05-10
With os-prober off, I do not see how it is finding other systems? Lets see details.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tea for one on 2023-05-10
Your internal HDD contains an operating system installed in UEFI mode.
Therefore, there is an EFI system partition on the internal HDD.

I imagine that the only way to prevent external Ubuntu upgrades adding an entry to your internal HDD would be to "hide" the internal ESP.
You will have to remove the boot and esp flags on the internal ESP and then replace them.

Which operating system is installed on the internal HDD?

---

### Post by panijsr on 2023-05-12
You are correct. My internal HDD has Win11 with its own EFI partition. With regard to your suggestion to "hide" the internal ESP, I did that once in the past. But every time removing the flags and re-enabling is a hassle. 
Can I put the question bit differently. Can I completely remove Ubuntu's ability to mount any other storage device? I will never have any requirement to mount  other storage (Thumb drive/ HDD) when working with Ubuntu from external SSD. Can I remove udisks2 and related services?

---

### Post by tea for one on 2023-05-12
> **panijsr said:**
> You are correct. My internal HDD has Win11 with its own EFI partition. With regard to your suggestion to "hide" the internal ESP, I did that once in the past. But every time removing the flags and re-enabling is a hassle
If you have Gparted installed in your external Ubuntu disk, then slightly less hassle to remove and replace flags. 
> **panijsr said:**
> Can I put the question bit differently. Can I completely remove Ubuntu's ability to mount any other storage device? I will never have any requirement to mount  other storage (Thumb drive/ HDD) when working with Ubuntu from external SSD. Can I remove udisks2 and related services?
I have no idea. 
You'll have to be careful because it may affect other parts of the system.

_Suggestions_
Does your UEFI firmware allow you to de-activate your Windows 11 drive before booting into Ubuntu?
If you upgrade Ubuntu via terminal commands ([COLOR="#0000FF"]sudo apt update[/COLOR] followed by [COLOR="#0000FF"]sudo apt upgrade[/COLOR]), you will be given the choice to abort the upgrade if a new kernel were to be installed.
Then, you can change the flags before the upgrade?

---

### Post by oldfred on 2023-05-12
I know that Ubuntu does not find Windows systems with bitlocker on.
And typically fast startup/hibernation also prevents the NTFS driver from mounting NTFS partitions read/write. They can be mounted read only.
They now do not want os-prober on by default, as it scans system and auto mounts every partition to look for operating systems to add to grub menu. That can be a security issue.

You can in fstab mount all the NTFS partitions and set parameters to prevent mounting. May seem a bit backwards but that can work.


# Hide mount template examples with noauto,  you have to make the mount points yourself first
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all, UUID is better than this example with device mount
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
You may also what nofail as if Windows turns fast startup, then fstab entry will fail either waiting to timeout or causing other issues.

---

