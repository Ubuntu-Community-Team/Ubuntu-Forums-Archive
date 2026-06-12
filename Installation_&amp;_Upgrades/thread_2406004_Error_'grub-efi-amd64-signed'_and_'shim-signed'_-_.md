---
title: "Error 'grub-efi-amd64-signed' and 'shim-signed' - Dual boot Ubuntu 18.04.01/Windows10"
date: 2018-11-14
forum: Installation &amp; Upgrades
---

### Post by cmasso6 on 2018-11-14
Dear community,

I keep getting the same error message each time I run an "apt-get" command:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64-signed (1.93.8+2.02-2ubuntu8.7) ...
Installing for x86_64-efi platform.
Could not prepare Boot variable: No space left on device
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I installed Ubuntu 18.04 along side Windows 10 on a Surface Pro 4
I had some issues with the installation process with a "grub-efi-amd64-signed"
I resolved the issue following this workaround: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1771651](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1771651)
Now I can boot Ubuntu and it works fine apart from this error.

I run boot-repair which did not resolve the problem
Here is the boot-info report: [http://paste.ubuntu.com/p/yym3Xmrz2N/](http://paste.ubuntu.com/p/yym3Xmrz2N/)

The system:
```
Linux sp4 4.15.0-38-generic #41-Ubuntu SMP Wed Oct 10 10:59:38 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

Thank you in advance for your help,
Best

---

### Post by #&amp;thj^% on 2018-11-14
Can you please show us the output from:
```
dpkg -l grub\*
```
These type of problems can be a real pain.:(
While we are here could you also include this as well:
```
cat /etc/fstab
```

---

### Post by cmasso6 on 2018-11-14
Thank you for your answer
Here:

```

cmasso6@sp4:~$ dpkg -l grub\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  grub           <none>       <none>       (no description available)
ii  grub-common    2.02-2ubuntu amd64        GRand Unified Bootloader (common 
un  grub-coreboot  <none>       <none>       (no description available)
un  grub-doc       <none>       <none>       (no description available)
un  grub-efi       <none>       <none>       (no description available)
un  grub-efi-amd64 <none>       <none>       (no description available)
ii  grub-efi-amd64 2.02-2ubuntu amd64        GRand Unified Bootloader, version
iF  grub-efi-amd64 1.93.8+2.02- amd64        GRand Unified Bootloader, version
un  grub-efi-ia32  <none>       <none>       (no description available)
un  grub-efi-ia64  <none>       <none>       (no description available)
un  grub-emu       <none>       <none>       (no description available)
ii  grub-gfxpayloa 0.7          amd64        GRUB gfxpayload blacklist
un  grub-ieee1275  <none>       <none>       (no description available)
un  grub-legacy    <none>       <none>       (no description available)
un  grub-legacy-do <none>       <none>       (no description available)
un  grub-linuxbios <none>       <none>       (no description available)
ii  grub-pc        2.02-2ubuntu amd64        GRand Unified Bootloader, version
ii  grub-pc-bin    2.02-2ubuntu amd64        GRand Unified Bootloader, version
un  grub-xen       <none>       <none>       (no description available)
un  grub-yeeloong  <none>       <none>       (no description available)
un  grub2          <none>       <none>       (no description available)
ii  grub2-common   2.02-2ubuntu amd64        GRand Unified Bootloader (common 

```

```
cmasso6@sp4:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p4 during installation
UUID=6d873104-94ec-4d51-a0a8-dbf503bdaa77 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
#UUID=36A3-AA7B  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p5 during installation
UUID=abdaae2c-06a7-420f-8c1e-4e04833037b6 /home           ext4    defaults        0       2
# swap was on /dev/nvme0n1p6 during installation
UUID=072dccef-ffa8-4868-825d-7fb2bdb4ec90 none            swap    sw              0       0
UUID=36A3-AA7B    /boot/efi    vfat    defaults    0    1

```

---

### Post by #&amp;thj^% on 2018-11-14
yuck....This one is a mess, ;)
This is where i get thrown "# /boot/efi was on /dev/nvme0n1p1 during installation
#UUID=36A3-AA7B  /boot/efi       vfat    umask=0077 "
And due to the fact that I myself never dual boot with Windows. (I just don't use it). but this might  help hone in on it bit more:
```
sudo update-grub
```
post back the return please. :)

---

### Post by cmasso6 on 2018-11-14
Here it is

```
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-39-generic
Found initrd image: /boot/initrd.img-4.15.0-39-generic
Found linux image: /boot/vmlinuz-4.15.0-38-generic
Found initrd image: /boot/initrd.img-4.15.0-38-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

```

---

### Post by #&amp;thj^% on 2018-11-14
Well lets see if we can get lucky.
```
sudo apt update
sudo apt upgrade
```

---

### Post by cmasso6 on 2018-11-14
Nope, no luck :/
I get the exact same message

---

### Post by #&amp;thj^% on 2018-11-14
Please have a good back-up in place before proceeding.
Kind of a stab in the dark, but try
```

sudo apt remove --purge grub\*
sudo apt install grub-efi
sudo apt autoremove
sudo update-grub

```

---

### Post by 23dornot23d on 2018-11-14
> 
Could not prepare Boot variable: **No space left on device**
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.


Might be worth also looking at space on the boot drive ......... 
but if the last commands have been done - it may also give some room for it to now work .....

mmm ..... also ..... [https://bugs.launchpad.net/ubuntu/+source/shim-signed/+bugs?field.status:list=NEW](https://bugs.launchpad.net/ubuntu/+source/shim-signed/+bugs?field.status:list=NEW)

---

### Post by oldfred on 2018-11-14
I had that error on one of my systems, it took a while and/or UEFI replacement, grub update and various housecleaning.

[https://askubuntu.com/questions/1072618/could-not-prepare-boot-variable-no-space-left-on-device-grub-install-error-ef](https://askubuntu.com/questions/1072618/could-not-prepare-boot-variable-no-space-left-on-device-grub-install-error-ef)

In my case I found grub or UEFI finding all my entries in the ESP as I had backed up my /EFI/ubuntu folder several times. Still lots of room in my ESP.
But I could tell grub or  UEFI was adding UEFI boot entries as they had the name of my backup folders.
Post this:
sudo efibootmgr -v

I totally updated my UEFI, but newest version was version I had, so I just reinstalled it. It will reset many settings to defaults. So keep track of what you changed like UEFI Secure boot, allow USB boot, and any others. 
I housecleaned my ESP so it only had /EFI/ubuntu. If you have Windows or other systems you will want to keep those also.

If the efibootmgr -v shows lots of entries, we should houseclean out all duplicates or old entries. Do that before updating UEFI.
       Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

---

### Post by cmasso6 on 2018-11-15
It seems to have solved the problem :)
Thank you very much for your help !

However the grub menu now shows new entries:
```

EFI/BOOT/bkpbootx64.efi
EFI/BOOT/fbx64.efi
EFI/ubuntu/fwypx64.efi
EFI/ubuntu/mmx64.efi

```

I can boot properly, I was just wondering where they come from and if should/can remove them?

Thanks again !

---

### Post by oldfred on 2018-11-15
Boot-Repair probably created bkpbootx64.efi as a backup of your old bootx64.efi. That may have been a backup Windows boot loader.

Boot-Repair may also add any found .efi boot files in ESP into a new /etc/grub.d/25_custom file. If so you can edit or delete that file. 

The fwupx64.efi is a new file to directly update UEFI from within Ubuntu. Some brands now allow that. But if that is running never interrupt it.
        [https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist) 
    
The mmx64.efi is the key manager. May be required if you install proprietary drivers.

---

### Post by cmasso6 on 2018-11-15
Thanks !

---

### Post by jeff-artik on 2019-04-04
I fixed this message following this workaround [https://askubuntu.com/questions/1031066/errors-during-upgrade-from-17-10-to-18-04-shim-signed-and-grub-efi-amd64-signed](https://askubuntu.com/questions/1031066/errors-during-upgrade-from-17-10-to-18-04-shim-signed-and-grub-efi-amd64-signed)

> [COLOR=#333333][FONT=monospace]sudo su -[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]cd /boot/efi/EFI[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]mv ubuntu ubuntu-old[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]apt install -f[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]mv ubuntu-old ubuntu[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]update-grub2[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]exit[/FONT][/COLOR]

---

