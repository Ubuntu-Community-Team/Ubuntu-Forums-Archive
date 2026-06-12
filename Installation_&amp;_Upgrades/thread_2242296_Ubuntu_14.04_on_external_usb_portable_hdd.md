---
title: "Ubuntu 14.04 on external usb portable hdd"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by bugga on 2014-08-31
G'day Folks,
             I have Ubuntu 14.04 loaded on my internal 1 TB HDD on a Dell Inspiron One 2310 and triple booting with Windows 7 and Hackintosh Mavericks 10.9.4. I have now installed Ubuntu 14.04 to an external portable USB HDD with a / (root) partition, swap partition and Home partition with Grub installed to dev/sdb on the USB drive. I can boot to Grub via F12 key selecting my USB external HDD and it brings up the Grub menu for OS selection but it will not boot to anything including Ubuntu from there and just goes to a blank pink/mauve screen with no text.
Is there some simple way (for this Linux newbie) to edit files in Boot/Grub to complete booting to the OS?
I'll also mention that if I have the external portable USB HDD plugged in when attempting to boot to Ubuntu on my internal drive it fails to boot.
Any help with this would be greatly appreciated as I would like to have the Ubuntu installation on the external portable USB drive to be bootable on any PC for various reasons.

---

### Post by TheFu on 2014-09-01
USB is a poor substitute for using SATA-connected disks. When you get this working, you'll see how slow it is. Even USB3 doesn't perform well as an OS drive due to queuing issues.

From your description, I can't tell what the issue is, sorry.  I suspect the BIOS is changing the names of the devices when a USB disk is attached, so device-based booting doesn't work.  If UUIDs are used for the boot, it should work.

Is there a simple way? Sure - don't attempt to triple-boot and it becomes simple.
As you can understand, dual and triple booting add complexity - that's the price to be paid for flexibility.

If the system has a C2D or better CPU, why not use virtualization?

---

### Post by ubfan1 on 2014-09-01
The initial install creates a grub.cfg file with mostly UUIDs, but still some devices hardwired which can cause problems.  These are usually fixed by running sudo update-grub after a successful boot.  For the first boot, when you get to a grub screen, type "e" to edit the grub commands (instruction at the bottom of the screen), and look at the hd? devices (and maybe any /dev/sd? devices if they are present).  The usual problem is that the first set of devices was created with the USB installer present, which changes the hard disk numbering, causing the target USB to be a device which is not present when the install USB has been removed (devices become one number/letter less). Take a look at the hd devices, you can use tab completion to actually look at the device and tell from the partitions and files which disk you are looking at, or maybe it's obvious, like hd2 is used when there is no hd2 even present.  edit the hd? entries, try the boot with ctrl X or F10, and if successful, run the update-grub.  Portable usage should work with UUIDs in use, but you might need to explicitly edit more hd? s still left around -- Used to be (for me), hd0 was 99.9% the hard disk, but others have claimed that for them hd0 was the boot USB device, ymmv.  Portability issues also include video problems (and wireless problems).  Good Luck

---

### Post by C.S.Cameron on 2014-09-01
I would think that if you boot the internal Ubuntu and then plug in the external drive and then run update-grub, it will add the external drive to your internal's grub.

---

### Post by grahammechanical on 2014-09-01
For my own peace of mind I would disconnect the external hard disk and load into 14.04 on the internal drive and run

```
sudo update-grub
sudo grub-install /dev/sda
```

And see if that gets you loading into Ubuntu on the internal drive when the external drive is connected. I would also use File Manager and Disks utility in Ubuntu on the internal drive to see what is on the external drive. You will find the main grub configuration file at /boot/grub/grub/cfg. We are not supposed to edit this file. But we can examine it. Look for the section that begins

> ### BEGIN /etc/grub.d/10_linux ###

You will see menu entries for the Ubuntu that is the OS on that external drive similar to this

> menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5decfcfc-cb12-4294-bebd-4f70c129258c' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos8 --hint-efi=hd1,msdos8 --hint-baremetal=ahci1,msdos8  5decfcfc-cb12-4294-bebd-4f70c129258c
    else
      search --no-floppy --fs-uuid --set=root 5decfcfc-cb12-4294-bebd-4f70c129258c
    fi
    linux    /boot/vmlinuz-3.16.0-6-generic root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-6-generic
}


That is from my machine. Note     > set root='hd1,msdos8'

sda = hd0 and sdb = hd1 and msdos1 = first partition. In my case Grub is looking for Linux on partition 8 on the second hard disk. See, if the grub of the external drive is looking in the right place. Then look for this section

> ### BEGIN /etc/grub.d/30_os-prober ###

That section will have menu entries for all the other OS found on that machine. Do the locations seem correct?

Regards.

---

