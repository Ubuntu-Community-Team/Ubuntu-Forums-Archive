---
title: "Install Issue, No Bootloader in MBR"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by preben7 on 2014-10-18
So this problem has been bothering me for a couple days now. I have an original Surface Pro on which I was trying to reinstall windows and it was refusing to boot to my recovery USB. I'd been having a lot of issues with it anyway, so I thought it would be a good idea. When that did not work, I tried to install Ubuntu which I've been running without trouble on two old computers. Long story short, the process did not work. After the first attempt, it would continue to boot straight into Windows 8.1 without an option to go to Grub. Next attempt, it boots straight to the UEFI settings menu.

I've deleted all partitions and tried to install Ubuntu using a live USB which has not worked, although Ubuntu is clearly installed in /dev/sda2. It is a 64-bit version of Ubuntu 14.04 LTS (uname -a returns x86_64). Running gdisk -l /dev/sda returns

```

GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B06273A3-A1B3-4917-A030-E7D400E062EE
Partition table holds up to 128 enties
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  
   2         1050624       241917951   114.9 GiB   8300  
   3       241917952       250068991   3.9 GiB     8200  

```

I have tried to follow the instructions in the last post of [http://ubuntuforums.org/showthread.php?t=2223856&page=3](http://ubuntuforums.org/showthread.php?t=2223856&page=3), however I am a little concered about this output:
```

ubuntu@ubuntu:~$ sudo efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu

BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0000,0001,0000
Boot0000* ubuntu

```
I am not entirely sure how the bootorder is supposed to look, but shouldn't ubuntu be first? Regardless, I end up with
```

ubuntu@ubuntu:~$ sudo grub-mkconfig -o /mnt/system/boot/efi/EFI/GRUB/grub.cfg

/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.

```
Tryng a recommended repair with bootrepair does not work either, but the pastebin is [http://paste.ubuntu.com/8585716/](http://paste.ubuntu.com/8585716/)

Anybody have any ideas? Usually I find something in the forums that fixes my problem but I am completely stumped. Any and all suggestions are very appreciated.

---

### Post by oldfred on 2014-10-18
Surface Pro Ubuntu install:
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
[http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946)
[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247)

I would not expect Microsoft hardware to work at all, so am surpised that users have been able to install Ubuntu and get it to at least partially work.

 [http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge](http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge)

You may need to have a UEFI entry that says Windows. We have for a few other systems with only Ubuntu recreated the Windows efi file structure and renamed grub to be bootmfgw.efi so it thinks it is booting Windows but really boots grub.

      
 Ubuntu only on HP, recreate Windows folder and grub as Windows boot file
[http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714)
    From live installer mount the efi partition on hard drive:
    mount /dev/sda1 /mnt
    cd /mnt/EFI

       use ls to see if created correctly
    ls -l
    mkdir Microsoft
    mkdir Microsoft/Boot
    cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi

---

