---
title: "Install grub2 from livecd on gpt efi"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by awers2 on 2013-08-23
Hi

 I would like to install clear grub2 on efi partition.

I mounted the partitions of efi on /mnt

```
 ls /mnt/EFI/
Boot/      Microsoft/ redhat/ 

```

I began installations grub

```
grub-install --target=x86_64-efi --efi-directory=/mnt/EFI/ --bootloader-id=grub2 --recheck --debug
source_dir doesn't exist. Please specify --target or --directory
```

Can someone help me with the manual installation of grub2 on the board efi and gpt?

---

### Post by oldfred on 2013-08-23
Not sure what you are trying to do?

Manually create efi on flash drive which is similar to any efi partition. You would have to edit your grub.cfg yourself.
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)

---

### Post by awers2 on 2013-08-28
Maybe not the best place for publications

The operating system on the disk: RedHat, Windows 7

How to install grub on a purely

In my case, it came to damage EFI bootloader. I run Ubuntu live from the cd-rom. Please remember to boot ubuntu with UEFI mode. I succeeded only after the live usb pendrive.

Once booted, I logged onto the console in root mode.

```
sudo su -
```

Then I mounted the partitions of / RH and mounted the proc, sys, dev,efi into RH
```
mount /dev/sda5 /mnt 
mount -o bind /proc /mnt/proc
mount -o bind /sys /mnt/sys
mount -o bind /dev /mnt/dev
mount /dev/sda1 /mnt/boot/efi
chroot /mnt
```

I downloaded the new version of grub2 and installed it

```
wget [ftp://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz](ftp://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz)
tar  -xvf ./grub-2.00.tar.gz
yum install bison flex
  
   
 ./configure --with-platform=efi --enable-grub-fstest=no   --enable-grub-mkfont=no --disable-nls --enable-efiemu=no
make -j 8
make  install


```

I proceeded to restore the bootloader
```
grub-mkstandalone --directory="/usr/local/lib/grub/x86_64-efi/"  --format="x86_64-efi" --output="/boot/efi/EFI/ubuntu/grubx64.efi" 
  
 "boot/grub/grub.cfg"
grub-install --bootloader-id ubuntu /dev/sda  --target /boot/efi/EFI/ubuntu --directory=/usr/local/lib/grub/x86_64-efi/


```

Then you need to check the UEFI settings
```
efibootmgr -v
```

If you get an error message about the absence of the module check whether the system is surely UEFI boot mode


To delete the INVALID entries do
```
efibootmgr -b 000x -B 000x
```

To add a again bootloader from Windows
```
efibootmgr -c -L "Windows 7" -l \\EFI\\Microsoft\\Boot\\bootmgfw.efi
```

To add Grub
```
efibootmgr -c -L "Grub2" -l \\EFI\\ubuntu\\grubx64.efi


```

 Sorry for my English :)

---

