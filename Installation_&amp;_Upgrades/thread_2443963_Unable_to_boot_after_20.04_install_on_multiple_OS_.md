---
title: "Unable to boot after 20.04 install on multiple O/S setup"
date: 2020-05-22
forum: Installation &amp; Upgrades
---

### Post by losange13 on 2020-05-22
I had a working ubuntu 16.04 LTS and windows 10 dual boot setup with spare space, so after booting up with a usb 20.04 image to ensure it worked fine I decided to install it to a new empty partition.
I now find that I'm unable to boot any partition, even after following various boot-repair tutorials.

My current boot-repair diagnostic file is on [https://paste.ubuntu.com/p/9fc8q8hbpq/](https://paste.ubuntu.com/p/9fc8q8hbpq/)

My BIOS say's I have legacy mode enabled, but boot-repair claims it's set to UEFI. Don't understand why that is.
If I set UEFI (secure mode or insecure mode) I don't get any options other than booting the HD, which when selected just goes back to the error.

The message I get when the BIOS is set to legacy shows:

 'System BootOrder not nofound'
'Creating boot entry "Boot0000" with label "ubuntu" for file "\EFI\ubuntu\sGNU GRUB version 2.04"'

I have tried the following from grub:
grub> ls
(proc) (hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
grub> set root=(hd0,msdos1)
grub> linux /vmlinuz
grub> initrd /initrd.gz
grub> boot

this will take me to initramfs with the error "can't find /root in /etc/fstab"

I'm totally stumped, and would appreciate help on getting my O/S's booting agian.
Thanks.

---

### Post by oldfred on 2020-05-22
You cannot mix BIOS/MBR and UEFI/gpt.
And Ubuntu lets you install in UEFI Mode to MBR drive, and it really should not.

Windows only boots in BIOS mode from MBR partitioned drive. It has to have boot flag on the primary NTFS partition with its boot files. You have all the Windows boot files in sda3, so need to have boot flag on sda3.

UEFI requires boot flag (really esp flag) on ESP - efi system partition which is FAT32. But you can only have one boot flag per drive
So move boot flag back to sda3.

You may need to reinstall BIOS grub (grub-pc) in BIOS boot mode, to have correct grub in MBR.

New UEFI systems have 3 ways to boot, UEFI with Secure Boot, UEFI (without Secure Boot), and BIOS/CSM/Legacy (which also requires Secure Boot to be off).

Default boot settings in UEFI are for installed systems.

But you can boot external devices in either UEFI or BIOS mode, just by selecting correct entry in UEFI menu. 
Some installers seem to make USB flash drive in boot one mode or other, although ISO is configured to boot in either mode and most install tools create a bootable flash drive that will boot either way.

---

### Post by losange13 on 2020-05-23
Still no luck I'm afraid.

I moved the boot flag back to sda3 and eventually completely reinstalled grub via:

root@ubuntu:~# mount /dev/sda1 /mnt
root@ubuntu:~# mount -t proc proc /mnt/proc
root@ubuntu:~# mount -t sysfs sys /mnt/sys
root@ubuntu:~# mount -o bind /dev /mnt/dev
root@ubuntu:~# chroot /mnt

```
root@ubuntu:~/grub_restore# apt purge -y grub*-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'grub-common' for glob 'grub*-common'
Note, selecting 'grub2-common' for glob 'grub*-common'
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin* grub2-common* os-prober*
0 upgraded, 0 newly installed, 6 to remove and 19 not upgraded.
After this operation, 16.8 MB disk space will be freed.
E: Can not write log (Is /dev/pts mounted?) - posix_openpt (19: No such device)
(Reading database ... 290045 files and directories currently installed.)
Removing os-prober (1.70ubuntu3.3) ...
dpkg: warning: while removing os-prober, directory '/var/lib/os-prober' not empty so not removed
Removing grub-gfxpayload-lists (0.7) ...
Removing grub-pc (2.02~beta2-36ubuntu3.23) ...
Purging configuration files for grub-pc (2.02~beta2-36ubuntu3.23) ...
Removing grub2-common (2.02~beta2-36ubuntu3.23) ...
Removing grub-pc-bin (2.02~beta2-36ubuntu3.23) ...
Removing grub-common (2.02~beta2-36ubuntu3.23) ...
Purging configuration files for grub-common (2.02~beta2-36ubuntu3.23) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...

oot@ubuntu:~/grub_restore# apt install -y grub-pc
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc-bin grub2-common os-prober
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common os-prober
0 upgraded, 6 newly installed, 0 to remove and 19 not upgraded.
Need to get 2,238 kB/3,326 kB of archives.
After this operation, 16.8 MB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-common amd64 2.02~beta2-36ubuntu3.23 [1,704 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub2-common amd64 2.02~beta2-36ubuntu3.23 [511 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/main amd64 grub-gfxpayload-lists amd64 0.7 [3,658 B]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 os-prober amd64 1.70ubuntu3.3 [19.1 kB]
Fetched 2,238 kB in 0s (3,830 kB/s)
Preconfiguring packages ...
E: Can not write log (Is /dev/pts mounted?) - posix_openpt (19: No such device)
Selecting previously unselected package grub-common.
(Reading database ... 289597 files and directories currently installed.)
Preparing to unpack .../grub-common_2.02~beta2-36ubuntu3.23_amd64.deb ...
Unpacking grub-common (2.02~beta2-36ubuntu3.23) ...
Selecting previously unselected package grub2-common.
Preparing to unpack .../grub2-common_2.02~beta2-36ubuntu3.23_amd64.deb ...
Unpacking grub2-common (2.02~beta2-36ubuntu3.23) ...
Selecting previously unselected package grub-pc-bin.
Preparing to unpack .../grub-pc-bin_2.02~beta2-36ubuntu3.23_amd64.deb ...
Unpacking grub-pc-bin (2.02~beta2-36ubuntu3.23) ...
electing previously unselected package grub-gfxpayload-lists.
Preparing to unpack .../grub-gfxpayload-lists_0.7_amd64.deb ...
Unpacking grub-gfxpayload-lists (0.7) ...
Selecting previously unselected package grub-pc.
Preparing to unpack .../grub-pc_2.02~beta2-36ubuntu3.23_amd64.deb ...
Unpacking grub-pc (2.02~beta2-36ubuntu3.23) ...
Selecting previously unselected package os-prober.
Preparing to unpack .../os-prober_1.70ubuntu3.3_amd64.deb ...
Unpacking os-prober (1.70ubuntu3.3) ...
Processing triggers for systemd (229-4ubuntu21.28) ...
Processing triggers for ureadahead (0.100.0-19.1) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Setting up grub-common (2.02~beta2-36ubuntu3.23) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Running in chroot, ignoring request.
Setting up grub2-common (2.02~beta2-36ubuntu3.23) ...
Setting up grub-pc-bin (2.02~beta2-36ubuntu3.23) ...
Setting up os-prober (1.70ubuntu3.3) ...
Setting up grub-pc (2.02~beta2-36ubuntu3.23) ...

Creating config file /etc/default/grub with new version
Installing for i386-pc platform.
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-178-generic
Found initrd image: /boot/initrd.img-4.4.0-178-generic
Found linux image: /boot/vmlinuz-4.4.0-177-generic
Found initrd image: /boot/initrd.img-4.4.0-177-generic
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Found Ubuntu 20.04 LTS (20.04) on /dev/sda7
Adding boot menu entry for EFI firmware configuration
done
```


But I still get the BIOS error 'System BootOrder not nofound' on boot.
 
current boot-repair diagnostic is: [https://paste.ubuntu.com/p/Z5TJgq9BzF/](https://paste.ubuntu.com/p/Z5TJgq9BzF/)

---

### Post by oldfred on 2020-05-23
You booted live installer in UEFI mode.

> BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.

But it looks like it correctly installed grub-pc.
So is system trying to boot in UEFI mode. That is the BIOS/Legacy/CSM boot mode setting in UEFI.

To boot my system in UEFI mode, all the UEFI settings were under the CSM setting which seemed backwards to me?

---

### Post by losange13 on 2020-05-23
It definitely says 'Legacy' in the BIOS. This is just so confusing - I  now find that running boot-repair (after usb boot in 20.04) it seems to  suggest it will reinstall grub-efi-amd64-signed etc.
[https://pastebin.ubuntu.com/p/7QgnzNjnSW/](https://pastebin.ubuntu.com/p/7QgnzNjnSW/)

Not  sure if I should attempt that. I'd rather not loose the ability to boot  windows, but I just can't live without my Ubuntu being bootable!

---

### Post by oldfred on 2020-05-23
Pastebin link not working.

But you need to always boot in BIOS mode. 
Boot Ubuntu live in BIOS mode from UEFI boot menu & add Boot-Repair using ppa.

Make sure you get BIOS screen when booting live installer:
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by losange13 on 2020-05-23
Sorry - corrected the pastebin like above, but will try to boot live in BIOS mode...

---

### Post by oldfred on 2020-05-23
Because you booted live installer with Boot-Repair in UEFI mode and have an ESP, it wants to reinstall grub in UEFI boot mode.
You have to always be in BIOS mode.

You also need to use advanced mode and choose install & drive to place grub bootloader.
Otherwise it installs grub for first install found. I think you want grub from 20.04.

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Anyone with multiple drives or multiple installs, should use Boot-Repair's advanced mode with then give options to choose correct drive or correct install. Default with multiples often is not best alternative.

---

### Post by losange13 on 2020-05-23
getting further now, although not quite there - I'm able to boot in BIOS mode to my 18.04 on /dev/sda1 using a utility from Ultimate Boot CD iso.

UBCD iso boot -> Boot Management -> Smart Boot Manager -> 'selected boot from HD partition 0' to get to old 18.04 grub menu.

boot-repair still shows that it wants to reinstall grub-efi-amd64-signed of sda1, which is not actually installed on sda1.

[http://pastebin.ubuntu.com/p/Xw4xkGwxsp/](http://pastebin.ubuntu.com/p/Xw4xkGwxsp/)

Still not convinced those are the actions I want to carry out.

But with advanced mode, there's quite a lot of options that I'll need to review before I commit to any changes.
At least for now, I can use my system booting via Smart Boot Manager.

---

### Post by oldfred on 2020-05-23
Because you have the ESP and your fstab has the mount of your ESP, Boot-Repair is seeing your install as UEFI.
I thought the grub-pc install would remove the mount of the ESP. But you reinstalled grub for the install in sda1, not the newer 20.04 install.

> # /boot/efi was on /dev/sda6 during installation
UUID=22DB-370F  /boot/efi       vfat    umask=0077      0       1

---

### Post by losange13 on 2020-05-24
I have managed to get 20.04 booting natively.
Not too sure how though as I reinstalled grub*-common after booting non-UEFI to 16.04, which didn't allow booting directly, so I used another utililty to BOOTMGR (on UBCD) to write the MBR. Things got worse as I couldn't seem to boot anything even using the old method of Smart Boot Manager (on UBCD), so I changed the bios setting to UEFI which still failed to boot, then after changing back to Legacy mode I got the following message on booting:

'System BootOrder not found'
'Creating boot entry "Boot0000" with label "ubuntu" for file "\EFI\ubuntu\shimx64.efi"'

and 20.04 started booting.
Great!

efibootmanager shows:
Timeout: 0 seconds
BootOrder: 0000,0003,0002,0001
Boot0000* ubuntu
Boot0001* BRCM MBA Slot 0100 v15.4.2
Boot0002* WDC WD10JPVX-22JC3T0            
Boot0003* HL-DT-ST DVDRAM GU71N           
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network

I thought I might try to reinstall the mbr etc via 'grub-install /dev/sda', but I now find this fails!
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.

The exact reason for this is unknown, but at the moment I can boot my system again - so will leave it alone for a while until I feel brave enough to try again.

Thanks oldfred for your advice on this, just a shame my system didn't play nicely.

---

### Post by oldfred on 2020-05-24
Then you are using UEFI to boot.
You may be able to manually boot in BIOS mode thru MBR to old install. But will not be able to boot Windows, unless BIOS grub by passes boot flag & lets you boot it in BIOS mode.
And if reinstalling Windows in UEFI mode drive would have to be gpt partitioned.

If now deciding to use UEFI, better to use gpt partitioning. But that is a major change as reinstall and gpt will erase drive.
There are tools to convert to gpt, but then old Windows will never boot. Windows in BIOS mode has to be on MBR drive.
But long term, you want to use gpt. 
I planned ahead a bit and started converting new or reconfigured drives to gpt with my old BIOS only system 10 years ago. :)

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

