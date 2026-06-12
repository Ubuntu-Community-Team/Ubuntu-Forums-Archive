---
title: "&quot;Cannot open root device&quot; while booting install iso on flash drive"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by danielconvissor on 2010-09-26
Hello:

I am Ubuntu 10.04.1 to prepare a USB flash drive for use as installation media for a new computer that's on the way.  When the Linux kernel tries booting up on the flash drive, I get an error saying *VFS: Cannot open root device "<NULL>" or unknown-block(8,1)*.

Here's how I got to this point...
[list]
[*]Created bootable partition on the thumb drive.
[*]Put the following files onto the flash drive: *initrd.gz*, *vmlinuz*, and *ubuntu-10.04.1-server-amd64.iso* from [http://archive.ubuntu.com/ubuntu/dists/10.04.1/main/installer-amd64/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/10.04.1/main/installer-amd64/current/images/hd-media/)
[*]Install Grub2 to the drive via *grub-install*.
[*]Put the following into *boot/grub/grub.cfg*:
```

set timeout=120
set default=0

menuentry "Ubuntu Server amd64 Live ISO" {
    loopback loop /ubuntu-10.04.1-server-amd64.iso
    linux (loop)/install/vmlinuz boot=install iso-scan/filename=/ubuntu-10.04.1-server-amd64.iso splash --
    initrd (loop)/install/initrd.lz
}

```
[*]Restart the computer to test if the this setup works.
[*]Pick USB from BIOS boot menu.
[*]Pick my menu entry from the Grub menu.
[/list]

Then Linux starts booting from the thumb drive and the following message comes up:
```

VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
Please append a correct "root=" boot option

```

I then tried adding several variations of *root=* and *rootwait* to the *linux* line of the *menuentry*, above.  None worked.
[list]
[*]root=/dev/sda1
[*]root=/dev/hda1
[*]root=/dev/ram0
[*]root=/dev/ram
[*]root=(loop)
[*]root=(hd0,1)
[/list]

Any ideas, please?

---

### Post by tom4everitt on 2010-09-26
Are you aware that there is a tool "Startup Disk Creator" in System->Administration. 

It will do all the complicated settings for you :) (boring, I know)

---

### Post by sikander3786 on 2010-09-26
Why did you go the adventurous way? As tom4everitt mentioned, there is "Startup Disk Creator". Also there is unetbootin which can also run on Windows in addition to Ubuntu and Linux to create a live Linux USB.

[http://unetbooting.sourceforge.net](http://unetbooting.sourceforge.net)

---

### Post by danielconvissor on 2010-09-26
> **tom4everitt said:**
> Are you aware that there is a tool "Startup Disk Creator" in System->Administration. 

It will do all the complicated settings for you :) (boring, I know)

:)  Yeah, I know of that utility.  There also are the *boot.img.gz* images provided by Ubuntu.

There are several reasons I went the hard core route.  It provides more flexibility and a better understanding of how things work.  And I'm a masochist.

Hopefully someone will be able to help out with a way

---

### Post by tom4everitt on 2010-09-26
I like the spirit :) 

The root option provided to the kernel should be the root ('/') of your system, right? And probably your USB will not be hda1 or sda1, but sdb1. Did you try that as a root option? Perhaps it's even better to do

root=UUID=xxx (substitue xxx obviously. look in /dev/disk)

---

### Post by danielconvissor on 2010-09-26
> **tom4everitt said:**
> ...probably your USB will not be hda1 or sda1, but sdb1.

Perhaps it's even better to do
root=UUID=xxx (substitue xxx obviously. look in /dev/disk)

I tried your suggestions.  Alas, no love.

As far as it being sdb vs sda, in the grub interactive mode, doing an *ls* shows the USB as sda, since it's the unit that's being booted from.  I figured the kernel would feel similarly.

Is there a way for me to get into the kernel loader mode (or whatever it is) so I can do an *ls* there?  Or is there a way for me to log the dmesg?

What are we really looking to be the root, anyway?  Don't I want the mounted ISO image to be the root?

---

### Post by tom4everitt on 2010-09-27
Yeah, that would make a lot of sense actually. I'm not quite certain of how to pick an iso as root. I didn't even know that it was possible to have grub boot an iso :redface:

Putting the contents of the iso on the usb would not be an option?

---

### Post by ballle_98 on 2010-12-16
this line "initrd (loop)/install/initrd.lz" is wrong if you loop mount the iso you will see that it needs to be     "initrd (loop)/install/initrd.gz"

---

### Post by K.J. on 2010-12-16
I often have trouble with those automated utilities. A simple dd of the image to the flash drive usually works for me.

e.g. (where sdb is your flash drive)
dd if=/path/to/myimage.iso of=/dev/sdb

---

### Post by dabl on 2010-12-16
This is how I do it:  [http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

I'd love to hear feedback.

---

### Post by oldfred on 2010-12-16
I use the grub2 method, since I find it easy to just copy ISO to flash and edit grub.cfg. With larger 4GB flash I can have multiple ISOs and boot any of them and easily update to newest version. It has become my install and repair tool.

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

Some have automated the process.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
multicd.sh - combine Linux ISOS into one
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

