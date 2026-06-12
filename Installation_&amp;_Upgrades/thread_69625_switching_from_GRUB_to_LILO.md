---
title: "switching from GRUB to LILO"
date: 2005-09-27
forum: Installation &amp; Upgrades
---

### Post by Brando569 on 2005-09-27
ive found various things on the internet but none of them seemed to really help. i managed to throw together a lilo.conf but wanted to run it through you guys before i rebooted.

# Start LILO global section
boot = /dev/hda   # The boot device.  In this case, the first harddrive
delay = 50        # Delay in tenths of seconds between LILO prompt
                  # and loading of default image.
vga = normal      # Force sane state of video. (80x25)
ramdisk = 0 
                  
read-only         # All Linux filesystems should be read-only for the fsck
                  # at boot time.
root = /dev/hda6  # Everytime I boot Linux it will be on the same root
                  # filesystem.
# End LILO global section

# Linux default bootable partition config begins
image = /vmlinuz
  label = Ubuntu-2.6.10-5-686
# Linux bootable partition config ends

# Linux old kernel partition config begins
image = /vmlinuz.old
  label = Ubuntu-2.6.10-5-386
# Linux old kernel bootable partition config ends

other = /dev/hda5
label = WinXP
table = /dev/hd5


how do i use initial ramdisks with the kernels? i tried removing the 0 from ramdisk (in the first section) and putting /initrd.img but that gave me this:

Warning: LBA32 addressing assumed
Fatal: Not a number: "/initrd.img"

can anyone give me a correct setup?

---

