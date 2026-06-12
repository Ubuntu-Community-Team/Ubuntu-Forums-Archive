---
title: "Re: Manual Upgrade to 16.04b2 from 14.04"
date: 2016-04-12
forum: Installation &amp; Upgrades
---

### Post by jwadamson on 2016-04-12
I am trying to do an upgrade in place using the live cd of the 16.04 beta2. I use LUKS, but otherwise nothing special.
The live boot disk still can mount my encrypted /, so I know I haven't lost everything yet.

During installation I map partitions as:

/dev/mapper/ubuntu-vg-root EXT4 / 491220MB
/dev/mapper/ubuntu-vg-swap_1 swap 8577MB
/dev/sda1 ext2 /boot 254MB
/dev/sda5 crypto 499849MB (physical volume for encryption)
boot loader destination as /dev/sda

I pick to continue without any reformatting and enter my prior username + password and computer name.
I have it pull updates and 3rd party options during install.

It seems to install fine, but complains that some packages could not be reinstalled afterwards. Seems like a reasonable outcome.

When I reboot, it drops me to busybox shell and the luks partitions are not visible. It never prompts for luks password.

I guess my question could be sumarized as how do I get the installer to pick up an existing Luks volume for /?

So I think the issue is that I may have damaged by grub /boot partition (sda1). I am still getting stuck on how to fix this to get it to boot from /boot and presumably unlock the sda5 volumes.

---

### Post by Bucky Ball on 2016-04-13
And I suspect the issue may be that you are downloading and installing third-party drivers and updates during install. Do no tick those boxes and try again. 

Before doing any OS upgrade you should get your install as 'vanilla' as possible: switch off any added PPAs, go back to the open-source video drivers.

Be aware that 16.04 LTS is not released yet and there are no guarantees every aspect of it is working. This may be a known install/upgrade bug for the moment. Have you checked?

---

### Post by jwadamson on 2016-04-13
Please if anyone can tell me how to configure grub to prompt to mount my luks partition on boot, I would really appreciate it.
Or if there are any alternatives for re-installing grub and adopting the existing luks partition.

Thanks, will try again. Sorry my comment #4 was a bit delayed. I may also just sit tight until I can burn a final disk. Getting booting of partitions that are recognized in the live cd wasn't expected to be such a chore.

---

### Post by Bucky Ball on 2016-04-13
> **jwadamson said:**
> Getting booting of partitions that are recognized in the live cd wasn't expected to be such a chore.

You are using an unreleased version. Expect nothing except perhaps the unexpected! After release all should be (close to) fine.

---

### Post by jwadamson on 2016-04-27
So update with the FINAL LTS CD:
1) ran live 16.04 FINAL CD, manually mount the encrypted volume
2) install select custom partition
3) sda1 -> ext4 /boot + format
    sda5 -> physical encryption volume
    .../luks-vg-root -> ext4 / (no format)
    .../luks-vg-swap -> swap

Result is a system that drops to emergency shell and does NOT prompt to unlock the luks items at boot.
I can not visibly see any "important" difference between the /boot area and grub.cfg of this and a luks system that does mount properly. One of my next steps may be to use the live cd to extract them directly and diff.

How do I repair the /boot and grub files to prompt to unlock my encrypted / at boot time? I know the blkid and volume names and desired mount points of desired result if they are needed during edits. 

p.s. I believe I tried chroot + update grub with the new /boot and / volumes mounted without any change to behavior

---

### Post by jwadamson on 2016-04-28
Next steps will probably be to verify the /etc/crypttab (but since that is on my intact volume that isn't being mounted, not sure how that could help)
Or do the chroot thing again and run something like `[COLOR=#111111][FONT=Consolas]update-initramfs -u -k all[/FONT][/COLOR]`. Anyone know if that would get it to prompt and mount a luks volume for / on sda5 at boot?

---

### Post by oldfred on 2016-04-28
Do not know encryption.
But it does seem like the install was just a LVM install as you opened the encryption before the install, so it does not know it is encrypted.

This mentions a couple of settings even though old version.
[http://askubuntu.com/questions/663332/what-is-the-proper-way-to-install-ubuntu-15-04-with-lvm-luks-and-manual-partit](http://askubuntu.com/questions/663332/what-is-the-proper-way-to-install-ubuntu-15-04-with-lvm-luks-and-manual-partit)

---

### Post by jwadamson on 2016-04-28
the [https://askubuntu.com/questions/663332/what-is-the-proper-way-to-install-ubuntu-15-04-with-lvm-luks-and-manual-partit](https://askubuntu.com/questions/663332/what-is-the-proper-way-to-install-ubuntu-15-04-with-lvm-luks-and-manual-partit) sounds like same thing as my effective setup. Shame that despite Koss645 seeming to know the answer he left it as an exercise for the reader. 

Sounds like I am slowly getting on the right path towards whatever it is I need to tweak for a boot decrypt prompt.

---

### Post by jwadamson on 2016-05-04
Based on comments, I extracted a initrd.img-3.13.0-85-generic from a working Ubuntu 14.04 system to try to compare with the upgraded machine.

which /scripts/local-top/ORDER then references /scripts/local-top/cryptroot which seems to have that machine's lvm partitions referenced and calls `/sbin/cryptsetup luksOpen ...` commands.
    $ fgrep -r sda5 .
    ./conf/conf.d/cryptroot:target=sda5_crypt,source=UUID=3c27b899-22f0-42b4-a446-55acfc6c4e62,key=none,rootdev,lvm=ubuntu--vg-root
    ./conf/conf.d/cryptroot:target=sda5_crypt,source=UUID=3c27b899-22f0-42b4-a446-55acfc6c4e62,key=none,lvm=ubuntu--vg-swap_1


I was surprised when I looked to do the same with the upgraded machine for comparison and found that the reformatted /boot is almost empty and is missing the /boot/grub/i386-pc/*.mod, /boot/initrd.img-*-generic, /boot/vmlinuz-*-generic, and /boot/System.map-*-generic files I see in the working 14.04 system.


    $ find boot/
    boot
    boot/abi-4.4.0-21-generic
    boot/memtest86+_multiboot.bin
    boot/memtest86+.elf
    boot/grub
    boot/grub/unicode.pf2
    boot/grub/grubenv
    boot/grub/gfxblacklist.txt
    boot/config-4.4.0-21-generic
    boot/memtest86+.bin

I am assuming this is at least part of the problem.
I think next will be to use a VM to generate new boot contents and copy that over. I probably will have to edit the cryptroot section of the resulting initrd img.
Hopefully that gets me an inital boot at least, may need to do other edits so that `[COLOR=#111111][FONT=Consolas]update-initramfs -u -k all[/FONT][/COLOR]` and next kernel update don't regenerate bogus ones.
Should update this later today.

---

