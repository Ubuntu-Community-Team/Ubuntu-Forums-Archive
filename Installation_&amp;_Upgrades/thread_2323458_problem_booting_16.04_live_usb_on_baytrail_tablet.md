---
title: "problem booting 16.04 live usb on baytrail tablet"
date: 2016-05-05
forum: Installation &amp; Upgrades
---

### Post by miatawnt2b on 2016-05-05
I can't seem to get my live usb to boot on my Acer Switch10. It's a baytrail tablet that needs a 32bit EFI bootloader. I made a usb from the 16.04 64bit iso, and installed the bootia32.efi file in the EFI directory.
The machine boots the bootloader but drops me directly into a grub prompt. so I type the following.

linuxefi (hd0,gpt1)/casper/vmlinuz root=/dev/sda1
initrdefi /casper/initrd.img
boot

as soon as I hit enter after the boot command, I get a solid cursor and the machine hangs. It will not do anything. Any ideas?

---

### Post by fanum2 on 2016-05-08
I am also having this issue. I think we may need to generate a new bootia32 file using 16.04.

---

### Post by Bucky Ball on 2016-05-08
It is generally discouraged to post just a link here, but as this has been covered numerous times here and elsewhere (please search before posting :)), in this case I will:

[http://ubuntuforums.org/showthread.php?t=2314964&p=13445765&viewfull=1#post13445765](http://ubuntuforums.org/showthread.php?t=2314964&p=13445765&viewfull=1#post13445765)

Start there and keep reading til the end. Search these forums and do a general search of the internet for '16.04 baytrail' or 'Ubuntu baytrail' and see what you find ...

---

### Post by fanum2 on 2016-05-08
That doesn't answer anything. I'm aware of that thread, but the work around to boot stopped working with 16.04. it worked with 14.04, 14,10, 15.04 and 15.10. So, the original posters question is a legitimate one, not covered by any existing threads (that I could see with a quick search).

---

### Post by bmw-man on 2016-05-23
Try booting with **intel_idel.max_cstate=0** . That seems to be a known issue with bay trail hardware. 16.04 works fine for me with running 64bit installer on 32bit UEFI without any modifications.

---

