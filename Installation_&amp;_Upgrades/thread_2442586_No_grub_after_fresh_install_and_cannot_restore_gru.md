---
title: "No grub after fresh install and cannot restore grub"
date: 2020-05-05
forum: Installation &amp; Upgrades
---

### Post by rdh61 on 2020-05-05
Hi,

After installing Lubuntu 20.04 over 18.04 there is no grub menu, and attempts to restore grub fail, both via the Boot Repair tool and reinstalling grub via the command line. I am copying my output from the latter here. My disk partition is odd: 2 Windows recovery environments and 2 swap partitions.

How can I sort this out?

Many thanks.


```
lubuntu@lubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.53 GiB, 1631215616 bytes, 3185968 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 298.9 GiB, 320072933376 bytes, 625142448 sectors
Disk model: ST320LT012-9WS14
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 0C7D6C59-A456-4E93-A15E-497C9491116B

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   2050047   2048000  1000M Windows recovery environment
/dev/sda2    2050048   2582527    532480   260M EFI System
/dev/sda3    2582528   2844671    262144   128M Microsoft reserved
/dev/sda4    2844672 305745919 302901248 144.4G Microsoft basic data
/dev/sda5  305745920 306671615    925696   452M Windows recovery environment
/dev/sda6  306671616 578392063 271720448 129.6G Linux filesystem
/dev/sda7  586483712 598204415  11720704   5.6G Linux swap
/dev/sda8  598204416 625141759  26937344  12.9G Windows recovery environment
/dev/sda9  578392064 586483711   8091648   3.9G Linux swap

Partition table entries are not in disk order.


Disk /dev/zram0: 947.26 MiB, 993267712 bytes, 242497 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 947.26 MiB, 993267712 bytes, 242497 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
lubuntu@lubuntu:~$ sudo mount /dev/sda6 /mnt
lubuntu@lubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
lubuntu@lubuntu:~$ 
```

---

### Post by oldfred on 2020-05-05
You show UEFI system.
Grub re-install only asks for bios_grub partition, if trying to re-install in BIOS boot mode, which you do not want.
You may need to re-install grub in UEFI boot mode.

Be sure to boot Ubuntu live installer in UEFI mode and add latest Boot-Repair via ppa to it. I just got new update today for Boot-Repair. CD/DVD with Boot-Repair is older.
Post link to summary report.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rdh61 on 2020-05-05
> **oldfred said:**
> Be sure to boot Ubuntu live installer in UEFI mode

My BIOS is already set to boot in UEFI mode. I brought up the boot menu with F12 and selected the CD/DVD drive to boot into the Live CD. Is that not correct?

---

### Post by rdh61 on 2020-05-05
I have made sure the Ubuntu live installer boots in UEFI mode, run the latest boot-repair, and the result is the same, no boot loader, it just boots straight into Lubuntu. The boot-repair report is located at: [URL="http://paste.ubuntu.com/p/BjzCrqszgH/"]https://paste.ubuntu.com/p/BjzCrqszgH/
[/URL]
I was told:
"Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file!"

I do not know how to do this. There are not such detailed options in my BIOS settings screen.

---

### Post by oldfred on 2020-05-05
If you look at the output of efibootmgr after reinstall of grub, it shows the ubuntu entry using shimx64.efi:
sudo efibootmgr -v

> Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
And you need to turn off Windows fast start up.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

The setting in UEFI for default boot is for installed systems.
If UEFI Secure boot is off, you normally have two boot entries in UEFI to boot USB flash drive installer. Some tools that create installer may make the installer UEFI only or BIOS only, but ISO is configured to be either.
So in UEFI one time boot menu you should always boot an entry like UEFI:flash where flash is name or label of flash drive. You may have BIOS entry with just the "flash" entry for BIOS boot, but do not want to ever use that.

---

### Post by rdh61 on 2020-05-06
@oldfred Thank you. I have turned off Windows fast start up. UEFI secure boot is off. There is still no boot loader screen. I am not sure what to do with the rest of the information you have provided.

---

### Post by oldfred on 2020-05-06
What brand/model system?
What video card/chip?
Can you press Escape just after UEFI screen & before grub should appear to get grub menu?

If you press keys for UEFI one time boot, same as you do for live installer, does it not show an Ubuntu entry?

---

### Post by rdh61 on 2020-05-08
> **oldfred said:**
> What brand/model system?
What video card/chip?
Can you press Escape just after UEFI screen & before grub should appear to get grub menu?

If you press keys for UEFI one time boot, same as you do for live installer, does it not show an Ubuntu entry?

1. Lenovo B590 laptop / Lubuntu 20.04 LTS + Windows 10.
2. robert@roberts-work-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
3. No, grub does not appear.
4. Yes, there are ubuntu and windows boot manager entries.

---

### Post by oldfred on 2020-05-08
Normally Intel graphics just work.
I expect because fast start up in Windows was on, grub could not add it to grub menu. Then with only one system, grub does not show menu, but just starts system boot. And usually issue then is graphics related, most often nVidia.

Can you press escape right after lenovo screen and before grub menu should appear. May have to try a few times to get it just at right time.
Then you should get grub menu. See if recovery mode boots, it should be second menu item.

Not sure if this applies, but UEFI updates required for most systems anyway.
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

Issues often common across many models of same brand, but not sure if any of these are close to yours.
Lenovo Yoga S740     [SOLVED] Installation problem
[https://ubuntuforums.org/showthread.php?t=2433373](https://ubuntuforums.org/showthread.php?t=2433373)
Lenovo Yoga 730-15IWL i5-8265U
[https://askubuntu.com/questions/1182889/install-ubuntu-on-lenovo-yoga-730-15iwl-with-a-i5-8265u-cpu-alongside-windows](https://askubuntu.com/questions/1182889/install-ubuntu-on-lenovo-yoga-730-15iwl-with-a-i5-8265u-cpu-alongside-windows)
Lenovo laptops containing Optimus graphics W520/T520/T530 nox2apic boot parameter
[https://gist.github.com/wbond/3800562](https://gist.github.com/wbond/3800562)
[https://askubuntu.com/questions/1178883/ubuntu-18-04-requires-multiple-attempts-to-boot](https://askubuntu.com/questions/1178883/ubuntu-18-04-requires-multiple-attempts-to-boot)
Lenovo Legion Y530-15ICH
[https://ubuntuforums.org/showthread.php?t=2425907](https://ubuntuforums.org/showthread.php?t=2425907)
Lenovo Gamer Legion Y530
[https://askubuntu.com/questions/1161675/ubuntu-18-04-does-not-load-sdd-nvme-xpg-gammix-lenovo-gamer-legion-y530?noredirect=1#comment1935970_1161675](https://askubuntu.com/questions/1161675/ubuntu-18-04-does-not-load-sdd-nvme-xpg-gammix-lenovo-gamer-legion-y530?noredirect=1#comment1935970_1161675)

---

### Post by rdh61 on 2020-05-08
This seems to be a bug:
[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1863434?comments=all"]
https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1863434[/URL]

---

