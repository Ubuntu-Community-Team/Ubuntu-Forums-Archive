---
title: "Ubuntu 14.04 entries in GRUB 2 disappeared; dual boot Windows broken"
date: 2016-04-12
forum: Installation &amp; Upgrades
---

### Post by pdkok on 2016-04-12
Hi there!

My system is setup as a dual boot of Windows 8 (laptop came with this) and Ubuntu 14.04 64 bit (installed with a LiveUSB, with different partitions for /boot, /home, / and swap). I received a warning that the /boot partition was getting filled near its limits, and I decided that it needed cleaning. Right now, I cannot access Ubuntu or Windows through GRUB anymore. 

**What did I do?**
I tried to clean up my /boot partition by uninstalling unused Linux kernel packages from my Ubuntu 14.04 install:
```
sudo apt-get remove linux-image-3.19.0-37-generic linux-image-3.19.0-39-generic linux-image-3.19.0-4* linux-image-3.19.0-51-generic linux-image-extra-3.19.0-3* linux-image-extra-3.19.0-4* linux-image-extra-3.19.0-51-generic 
sudo update-grub
```

After a reboot, the Ubuntu entries in GRUB vanished. Under Windows 8 I tried to use EasyBCD to fix this problem, but now I also cannot get into Windows anymore. 

I tried using Boot Repair's recommended repair on a LiveUSB of Ubuntu 14.04, but that kept running for over 8 hours and got stuck in the same phase. I quit Boot Repair and let it make a Boot Info summary. This is available at [http://paste.ubuntu.com/15783962/](http://paste.ubuntu.com/15783962/)

Can anyone help me get my system to work again?

Thanks in advance!

---

### Post by grahammechanical on 2016-04-12
I get the feeling that you removed all Linux kernels.

The boot info summary prints the contents of grub.cfg. That is used by Grub to draw the boot menu. grub.cfg does not show any entries for any Linux kernels. Under this section

> ### BEGIN /etc/grub.d/10_linux ###

It should show at least one entry like this
> 
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-6c98e446-6cb2-420f-9fde-4326bee63e01' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos7 --hint-efi=hd1,msdos7 --hint-baremetal=ahci1,msdos7  6c98e446-6cb2-420f-9fde-4326bee63e01
    else
      search --no-floppy --fs-uuid --set=root 6c98e446-6cb2-420f-9fde-4326bee63e01
    fi
    linux    /boot/vmlinuz-4.4.0-18-generic root=UUID=6c98e446-6cb2-420f-9fde-4326bee63e01 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-18-generic
}

I cannot see anything like that in your grub.cfg file

Further down the summary says this

> =================== No kernel in /mnt/boot-sav/sda2/boot:
bootx64.efi
bootx64.efi.grb

And later it says this

> =================== No kernel in /mnt/boot-sav/sda7/boot:
efi

And then there is the contents of sda7/etc/default/grub

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

The Grub menu will remain on the screen for 1 second before boot the default OS. GRUB_TIMEOUT=1. From the Grub manual

> Boot the default entry this many seconds after the menu is displayed, unless a key is pressed.

That is very little time to make a selection.

---

### Post by pdkok on 2016-04-12
So that means that I should only use chroot to load my whole system, sudo apt-get the most recent kernel and run update-grub again?

**Update - partial fix**

I installed a new kernel  and now I can enter my Ubuntu install again. The Windows entry is not  there yet, but it's something to start with. Here follows the  instructions I followed:

I booted from the LiveUSB, and opened a  terminal. I created a new folder /chroot and in this folder, I mounted  my Ubuntu partitions. You might need to use different drive letters:
```
mkdir /chroot
mount /dev/sda7 /chroot
mount /dev/sda5 /chroot/boot
mount /dev/sdb3 /chroot/home
```

Then, I also mounted the system folders.
```
mount -o bind /dev /chroot/dev
mount -o bind /sys /chroot/sys
mount -o bind /dev/shm /chroot/dev/shm
mount -o bind /dev/mqueue /chroot/dev/mqueue
mount -o bind /dev/pts /chroot/dev/pts
mount -o bind /proc /chroot/proc
```

Finally, I logged in as my regular user, with its regular password:
```
chroot /chroot login MYUSERNAME
```

And then I installed the most recent kernel:
```
sudo apt-get install linux-image-4.4.0-18-generic linux-image-extra-4.4.0-18-generic
sudo update-grub
```

After rebooting, I could select this Ubuntu installation and Windows again from the list in GRUB. The only remaining problem is that the Windows boot loader doesn't load. I will continue giving updates for people with similar problems, but any help is still appreciated.

The Windows boot loader tells me the following:

```
Windows failed to start. A recent hardware or software change might be the
cause. To fix the problem:

  1. Insert your Windows installation disc and restart your computer.
  2. Choose your language settings, and then click "Next."
  3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer
manufacturer for assistance.

    File: \BCD

    Status: 0xc0000098

    Info: The Boot Configuration Data file doesn't contain valid information
          for an operating system.
```

---

