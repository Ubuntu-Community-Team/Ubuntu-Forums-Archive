---
title: "Cannot make SSD boot on new MSI laptop (dual boot Ubuntu - Windows)"
date: 2024-10-06
forum: Installation &amp; Upgrades
---

### Post by vinnyzetrue on 2024-10-06
I'm currently trying to change my laptop computer. I'm switching from one MSI laptop to another :

the old laptop is a MSI GF63 8RC-290FR (around 5 years old), in which I have a 2TB Samsung SSD drive. Windows 11 (upgraded from a Win10 initially provided with the computer) and Ubuntu 22.04 in a dual boot with Grub2.

the new laptop is a MSI Thin 15 B13VE-226, initially provided with only a NVMe drive containing a Win11 install.

My hope was simply to insert my SSD in the new laptop and hoping it would simply "work"... So the "Bios" on the new computer (which is a modern thing with mouse support and no longer the blue/grey thing we're all used to. I think there is not option for any legacy thing.

But this bios is actually detecting my SSD quite well, I can even choose between the ubuntu or the Windows boot.

If I select Ubuntu, I get my usual grub menu, containing the same entries as I get on the old laptop. But if I choose Ubuntu, I am getting a "UUID not found" error, and the initramfs console opens. From there I cannot see any /dev/sd*, /dev/hd*. blkid shows nothing, no output, error code 2 (nothing identified according to the man page).

If I select Windows, I get a BSOD "NO_BOOT_MEDIA" at some point. But for now I don't really care about Windows.

I tried to boot from a Lubuntu live USB key on the new laptop. The SSD and its content can be easily mounted and accessed.

My guess is that maybe some module is missing from the initramfs image, but I cannot find out how to add just one module. It is currently configured with 'most' modules, which apparently should contain all hard disk drivers. But maybe it is created from the old laptop therefore not containing what is actually needed on the new one ?

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add most filesystem and all harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=most

[...]
"/etc/initramfs-tools/initramfs.conf" 69L, 1284B                                                                                                                           1,1          Haut

When mounting the SSD on the new laptop with the live usb key, I can see the UUID from the grub configuration is correct. So it reaffirms the idea that it's 'only' a "driver(ish)" issue.

If entering the command line from grub by typing 'c', I can see the SSD files under (hd0) and all the partitions from (hd0,gpt1) to (hd0,gpt7). More specifically the boot files under (hd0,gpt6), which should be the one used by grub.

menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-9d5e61ed-15ce-4ef4-ba72-78d99a800737' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  9d5e61ed-15ce-4ef4-ba72-78d99a800737
        else
          search --no-floppy --fs-uuid --set=root 9d5e61ed-15ce-4ef4-ba72-78d99a800737
        fi
        linux   /boot/vmlinuz-5.15.0-122-generic root=UUID=9d5e61ed-15ce-4ef4-ba72-78d99a800737 ro  quiet splash pcie_aspm=off pcie=noaer acpi_osi= $vt_handoff
        initrd  /boot/initrd.img-5.15.0-122-generic

I wanted to try to add ahci module in initramfs. I'm not even sure if that's a thing... Anyway, I can't figure out how, because I couldn't find how to list the actual modules contained in the existing initramfs, as lsinitramfs lists a lot of things presented as files with paths, not something I could consider as a "module name list" which is what is expected when configuring modules=list in the modules files of initramfs configuration.

I'm also wondering if this could be because the modern bios installed on the new laptop isn't referencing my ssd under SATA drives. SATA drives appears explicitly empty, and the ssd appears as a PCIe SSD.

I also tried to disable secure boot and trusted computing in the bios. No changes.

On the old laptop, the bios (blue/grey one), I can select some legacy/ahci parameter, but it is not on legacy.

What can I try from there ?

---

