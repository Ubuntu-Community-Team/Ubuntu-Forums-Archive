---
title: "Dual Systems problem, ubuntu 14.04 and windows 8"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by evilanir on 2014-09-18
Hi,
I bought lenovo u410 with dwo discs - 500gb HDD and 24GB SSD with Windows 8, and I want install Ubuntu 14.04 alongside them.

I've just installed Ubuntu on HDD, but a bootloader is probably installed on SSD. Now, when I turn on computer I must launch Boot manager and choose HDD to start windows, or SSD to start ubuntu. On which partition must I install ubuntu, so as not to loose Windows recovery partition?

---

### Post by jakeblackburn6 on 2014-09-18
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2014-09-18
May be best to see details. Run the Boot info report and post the link. Do not run any auto repairs until someone has reviewed your install.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did you install Ubuntu in UEFI mode or BIOS boot mode. Above report will confirm that.

---

### Post by evilanir on 2014-09-18
Here is boot-repair info

[http://paste.ubuntu.com/8374691/](http://paste.ubuntu.com/8374691/)

When I installed, I have set the priority boot (USB first), boot mode to UEFI - not legacy support

---

### Post by oldfred on 2014-09-18
You have an Intel SRT system. That uses the SSD as cache to make Windows boot faster.
It shows the SSD as sda & hard drive as sdb.

Desktops usually do not need the separate /boot. It just adds another partition to manage. Since kernels are not auto deleted with updates you will have to regularly houseclean as if /boot gets full you have major issues. (many threads on that issue). But you should house clean kernels even if you do not have a separate /boot.

It looks like you left Windows fast boot or always on hibernation on. That will potentially lead to many issues when dual booting.  But then you may not be using SSD at all?

It used to be with Intel SRT, that Ubuntu would not install at all. But now with 14.04 it does seem to install, but grub may not correctly install. And in your case you show no grub boot files in the efi partition.

If you set UEFI/BIOS to AHCI and then boot Boot-Repair in UEFI mode, you should be able to reinstall grub. You do not need to upgrade to secure boot kernels unless you want to. Grub currently does not boot Windows 8.1 from grub menu when secure boot is on. If you want secure boot, you can install signed kernels but have to choose which system to boot from UEFI menu or perhaps one time boot key like f12 but varies by vendor.

Some other threads on Lenovo:
 Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)
      
Note that the editing with bkpbootmfgw.efi is from a Boot-Repair rename, better to rename bootx64.efi see link below where a user did that.
 Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.
Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED - other issues
[http://ubuntuforums.org/showthread.php?t=2170099](http://ubuntuforums.org/showthread.php?t=2170099)
[https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)


 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not any other entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

---

### Post by evilanir on 2014-12-02
I just update my windows to 8.1 and grub was overwritten. What should I do, to have two systems, and one Boot menu. I will reinstall Ubuntu, If is necessary.

---

### Post by oldfred on 2014-12-02
If UEFI, grub was not overwritten, just that Windows reset UEFI to make Windows first in boot order. And Windows 8.1 likes to do that a lot.
See if in UEFI you can set ubuntu entry as first or try one time boot key often f10 or f12 to see if you can still boot ubuntu entry.

---

