---
title: "Ubuntu 11.04 on UEFI success, mincor issues, solution wanted."
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by laichiwai on 2011-05-19
Hi all,

I have successfully installed Ubuntu 11.04 x64 booting from DVD through UEFI and manually configured Grub2 to boot into the new install. Though, I have a few minor issues seeking for answers.

Here is my installation method:
1. Boot Ubuntu 11.04 Live DVD in UEFI mode.
2. Install with GPT partitions.
3. Boot Ubuntu 11.04 Live DVD in UEFI mode.
4. Mount the installed /boot/grub and the /EFI partition.
5. Copy everything from /boot/grub to /EFI and those /usr/share/grub/*.pf2
6. Use efibootmgr to install the EFI boot image into EFI firmware.
7. Boot through EFI firmware.
8. Login.

Here is my hardware:
Asus P8P67 Delux (latest firmware 1503)
GeForce GTX 580 SLI (1920x1080 LCD)
3 HDD
Root / on sdb3
Boot /boot on sdb3
Home /home on sdc3
EFI on sda1
cat /proc/fb -> 0 EFI VGA

Here is what I experienced and would like to solve:
When booting with Live DVD through EFI.
1. Grub2 shows successfully but with prefix not defined error message.
1. The console resolution is the native resolution.
2. The splash screen is the native resolution.
3. nVidia proprietary can be installed and activated.
4. Display in System Settings can find out the LCD brand and resolutions.

When booting with EFI partition through EFI.
1. Grub2 beets (with the option enabled).
2. Grub2 does not display, even with shift key pressed.
3. Grub2 boots directly into my installation without delay after beet (with purple screen displayed in 80x25 text mode).
4. Console seems not in graphic (framebuffer mode), but in text mode.
5. Ubuntu splash displayed in low resolution mode.
6. nVidia splash displayed after driver install.
7. Display in System Settings cannot find out the LCD brand and resolution.
8. nVidia driver works flawlessly but cannot give graphic (framebuffer mode) console.
9. Console tty1 - tty6 in text mode.
10. Can shutdown properly but cannot reboot. Reboot result in different kinds of errors.
11. Splash screen not present when shutting down but the dots in there still works. Strange.

What I have tried:
1. Nearly all possible solutions on the web.
2. Different grub2 configurations
2.1 Force text mode.
2.2 Force framebuffer mode.
2.3 Force resolution.
2.4 Force VGA.
2.5 Force UVGA.
2.6 Force VBE.
2.7 Chainload from EFI to /boot/grub.
2.8 Disable any time out combinations.
2.9 Writing different kinds of grub2 commands in different steps.
3. Different kernel boot options.
4. Getting latest grub2 source and build.

Thanks for the long read and I am really waiting for a solution on this.

---

### Post by umaxtu on 2011-05-25
How do you load the firmware with efibootmgr?

---

### Post by srs5694 on 2011-05-25
On my Intel board with UEFI boot support, I've had *much* better success with [ELILO](http://sourceforge.net/projects/elilo/files/elilo/) than with GRUB 2. I'm using version 3.14 from the Sourceforge page, but there's a Debian package of 3.12 in the Ubuntu repositories. The version in the repositories includes a script called elilo that can be used to install the boot loader (it even calls efibootmgr). ELILO can not, AFAIK, chainload to another EFI boot loader, which means it can't select between Linux and Windows. Thus, if you dual boot and use ELILO, you'll neet to either use your firmware to select which OS to boot or install another boot selector, such as [rEFIt,](http://refit.sourceforge.net/) to do that job. FWIW, here's my elilo.conf file:

```
prompt
timeout=50
default=2639
#chooser=textmenu

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/seeker/u1104
        append="reboot=a,w"

image=bzImage-2.6.39
        label=2639
        initrd=initrd.img-2.6.39
        read-only
        root=/dev/seeker/u1104
        append="reboot=a,w"

```

You'd need to modify this for your own system, of course. Note that ELILO requires that your kernel and initial RAM disk files be copied to the EFI System Partition (or to some other partition that EFI can read -- it might be able to load from a /boot partition if you used FAT for /boot, but I've not tested that).

On a VirtualBox installation, ELILO doesn't work for me, and I had to tweak my GRUB configuration file (grub.cfg). Here's my grub.cfg file:

```
#
# DO NOT LET AUTOMATED TOOLS EDIT THIS FILE!
#
# It was created by Rod Smith as a custom GRUB configuration
# file for my VirtualBox installations.
#

if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
}

set timeout=5

menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 755a0038-2bb8-4a38-8075-669e34985201
    echo    'Loading Ubuntu 11.04 with 2.6.38-8-generic kernel...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=755a0038-2bb8-4a38-8075-669e34985201 ro
#    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=755a0038-2bb8-4a38-8075-669e34985201 ro   quiet splash vt.handoff=7
    echo    'Loading initial RAM disk....'
    initrd    /boot/initrd.img-2.6.38-8-generic
    echo    'Initial RAM disk loaded; booting....'
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 755a0038-2bb8-4a38-8075-669e34985201
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=755a0038-2bb8-4a38-8075-669e34985201 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}

menuentry 'Chainload to rEFIt' {
    insmod fat
    set root='(hd0,1)'
    chainloader /EFI/rEFIt/refit.efi
}

menuentry 'Chainload to ELILO' {
    insmod fat
    set root='(hd0,1)'
    chainloader /EFI/ubuntu/elilo.efi
}

```

If you use this, you'll need to modify the UUIDs and "set root" options to suit your system. You'll also have to back it up and/or use it from a location where Ubuntu won't try to modify it, then manually update it after any kernel changes.

Note that Ubuntu's default grub-efi package is designed to boot the grub.efi file (or whatever they call it) from the EFI System Partition but to look for grub.cfg and the kernel in the Linux /boot partition. Thus, copying everything from /boot to the EFI System Partition was unnecessary and potentially confusing.

The kernel panic on shutdown is a known issue; see [here,](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/721576) for instance. The "reboot=a,w" kernel option described in post #7 there fixes the issue for me. One other poster to this forum found that "noefi" did the trick, although I think that would disable EFI services, which would probably be undesirable (unless maybe they were causing other problems).

[quote=umaxtu]How do you load the firmware with efibootmgr?[/quote]

The efibootmgr utility doesn't "load the firmware," in the sense of updating or replacing it; efibootmgr just sets certain firmware-based EFI boot options. It's typically used to manage the boot loader options -- to add GRUB, LILO, or whatever; to delete an old option; to change the order of options; and so on. Install the package and read its man page for details.

---

### Post by JaccoH on 2011-06-07
Did you ever find an answer for the 'Error: Prefix not set' message?

My grub2 efi boots fine. I have a file called bootx64.efi in a directory /efi/boot on a fat32 partition. This way I dont have to bless the efi file (yes mac mini).

I made a script in upstart which is launched on reboot/shutdown. This script converts the /boot/grub/grub.cfg file to the proper settings for EFI boot. I even replaced the prefix variable but I still get the prefix not set error. I did try different prefixes with grub-mkimage.

---

