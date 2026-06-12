---
title: "GRUB can't find my Window 10 HDD"
date: 2018-09-07
forum: Installation &amp; Upgrades
---

### Post by jdeiros on 2018-09-07
Hello,

To explain my situation simply, I have installed Ubuntu to a separate HDD on my PC and after install, GRUB can not find my Windows 10 partition; I can still open my BIOS and pick where I want to boot, but that's not convenient.

I have an SSD with Windows 10, partitioned as MBR and residing on /dev/sda with the boot information in /dev/sda1
I also have a second HDD with Ubuntu 18.04.1, partitioned as GPT, residing on /dev/sdb and my ESP in /dev/sdb1 (GRUB is installed here)

If you need more information, let me know and I will get it to you ASAP.

Things I have tried so far:
I have tried os-probe, but it doesn't find it.
I have tried to setup "chainloaders" but since I'm so new I am a little overwhelmed?? But I am not a quitter!! I got as far as having GRUB show "Windows 10" but error after you press that option to load the OS in GRUB.
I have also read that I can change my Windows installed HDD from MBR to GPT? Then re-run the os-prober but I have a lot of data and not so much back up storage should things go wrong.

I just want GRUB to show my Windows 10 HDD and also allow me to boot. 

I welcome all advice! Thanks.


UPDATE: [http://paste.ubuntu.com/p/gjdXPTzqXG/](http://paste.ubuntu.com/p/gjdXPTzqXG/) !Boot Repair paste bin link!

---

### Post by yancek on 2018-09-07
Go to the site below and use the 2nd option on Ubuntu to get the ppa for boot repair.  Download and run it as instructed using only the Create BootInfo Summary option.  Do NOT try to make any repairs.  When it finishes, it will give you a link which you can post here and more experienced users will be able to view it and will likely have suggestions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jdeiros on 2018-09-08
[http://paste.ubuntu.com/p/gjdXPTzqXG/](http://paste.ubuntu.com/p/gjdXPTzqXG/)

---

### Post by jdeiros on 2018-09-08
> **yancek said:**
> Go to the site below and use the 2nd option on Ubuntu to get the ppa for boot repair.  Download and run it as instructed using only the Create BootInfo Summary option.  Do NOT try to make any repairs.  When it finishes, it will give you a link which you can post here and more experienced users will be able to view it and will likely have suggestions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://paste.ubuntu.com/p/gjdXPTzqXG/](http://paste.ubuntu.com/p/gjdXPTzqXG/)

---

### Post by yancek on 2018-09-08
The boot repair output clearly shows that you left windows hibernated when you installed Ubuntu.  No Linux system will mount a hibernated filesystem partition so that is why your windows is not detected by Grub.  You will need to boot windows and  turn off hibernation/fast boot in windows.

---

### Post by Mark Phelps on 2018-09-09
With Win10, a system goes into hibernation BY DEFAULT unless you go to the trouble to disable Fast Startup (NOT the same as Fast Boot).  When that is the case, Linux can't mount the Windows filesystem volumes, so it basically, does not "see" them.

---

### Post by jdeiros on 2018-09-11
> **yancek said:**
> The boot repair output clearly shows that you left windows hibernated when you installed Ubuntu.  No Linux system will mount a hibernated filesystem partition so that is why your windows is not detected by Grub.  You will need to boot windows and  turn off hibernation/fast boot in windows.

Don't know why I just hit the brakes so hard and didn't bother to read; I must have been really frustrated, and wanted help at that point. Thank you thought, I'll remember this as to always read logs even if you yourself think you will not understand them.

---

### Post by jdeiros on 2018-09-11
> **Mark Phelps said:**
> With Win10, a system goes into hibernation BY DEFAULT unless you go to the trouble to disable Fast Startup (NOT the same as Fast Boot).  When that is the case, Linux can't mount the Windows filesystem volumes, so it basically, does not "see" them.

I have never heard of this until today; always thought "Shut Down" was just that, a total shut down. I had only disabled Fast Boot in my BIOS and not Fast Startup in Windows. 

I will make the changes to my personal PC after work, and post the results. Thank you again.

---

### Post by yancek on 2018-09-11
Some info on the fast startup in windows 10, particularly the last paragraph.

[https://www.zdnet.com/article/windows-10-tip-startup-and-shutdown-secrets/](https://www.zdnet.com/article/windows-10-tip-startup-and-shutdown-secrets/)

---

### Post by oldfred on 2018-09-11
You also installed Windows in BIOS/MBR and Ubuntu in UEFI/gpt.
UEFI and BIOS are not compatible. Once you start booting in one mode, you cannot switch modes. They write the hardware configuration differently onto hard drive for operating system to use. 
So once you boot to grub in UEFI mode, you cannot switch boot modes.

You can continue to use UEFI boot menu. Reinstall Windows in UEFI boot mode. Or convert your Ubuntu install to BIOS boot mode.  How you boot install media UEFI or BIOS, is then how it installs for both Windows & Ubuntu.

If you want to convert Ubuntu to BIOS boot on gpt partitioned drive you need a tiny 1 or 2MB unformatted partition with the bios_grub flag (right  click in gparted). You can shrink any partition as long as it is in first 2TiB of drive.
Then use Boot-Repair booted in BIOS mode, to totally uninstall the UEFI version of grub, and install grub-pc the BIOS boot version. Run sudo-update grub to add Windows to grub menu.
Grub only boots working Windows. It cannot be hibernated nor need chkdsk. Best to have Windows repair disk or installer with repair console. You be able to directly boot Windows like you do now, and use f8 to get into internal repair console, but best to have repair flash drive for installed version of every operating system you have installed.

You also do not need as large of a swap. Hibernation is not recommended. And ubuntu normally boots fast enough that hibernation does not save much if anything. And the only reason for large swap is hibernation. Default installs now use 2GB and swapfile, not a swap partition, but will use a swap partition if you have one.

---

