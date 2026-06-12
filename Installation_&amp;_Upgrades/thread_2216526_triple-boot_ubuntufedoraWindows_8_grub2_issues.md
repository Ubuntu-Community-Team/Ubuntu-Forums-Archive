---
title: "triple-boot ubuntu/fedora/Windows 8 grub2 issues"
date: 2014-04-12
forum: Installation &amp; Upgrades
---

### Post by PatrickD-52761 on 2014-04-12
Hi everyone,

I'm running into some strange issues with a triple-boot (Windows 8.1, Ubuntu 14.04, and Fedora 19). I've got both Windows 8 and Ubuntu loading fine (using Ubuntu's GRUB bootloader). But Fedora only boots to an older kernel (I'm guessing it's the rescue kernel). If I try to use Fedora's GRUB to control things, the only thing that boots is Fedora, and I have to completely reinstall GRUB from Ubuntu to get things working again. In looking at some other thread, I found the suggestion that I should take the menu entries, and add them to the 40_custom file. When I copied the menu entries, I *think* I found the problem--but I don't know how to get Ubuntu to not do it.

Here are the menu entries for Fedora 19 in my Ubuntu grub.cfg file:
```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Fedora release 19 (Schrödinger’s Cat) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-e0a5e358-e8d7-4fb9-8abd-81334f0c1112' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt9'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  b238e718-da90-470e-b533-fab66caf2ef2
    else
      search --no-floppy --fs-uuid --set=root b238e718-da90-470e-b533-fab66caf2ef2
    fi
    linux /vmlinuz-0-rescue-78e4400d811c4c4ab2683d523615cd48 root=/dev/sda10
    initrd /initramfs-0-rescue-78e4400d811c4c4ab2683d523615cd48.img
}
submenu 'Advanced options for Fedora release 19 (Schrödinger’s Cat) (on /dev/sda10)' $menuentry_id_option 'osprober-gnulinux-advanced-e0a5e358-e8d7-4fb9-8abd-81334f0c1112' {
    menuentry 'Fedora release 19 (Schrödinger’s Cat) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-0-rescue-78e4400d811c4c4ab2683d523615cd48--e0a5e358-e8d7-4fb9-8abd-81334f0c1112' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  b238e718-da90-470e-b533-fab66caf2ef2
        else
          search --no-floppy --fs-uuid --set=root b238e718-da90-470e-b533-fab66caf2ef2
        fi
        linux /vmlinuz-0-rescue-78e4400d811c4c4ab2683d523615cd48 root=/dev/sda10
        initrd /initramfs-0-rescue-78e4400d811c4c4ab2683d523615cd48.img
    }
    menuentry 'Fedora release 19 (Schrödinger’s Cat) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.12.5-200.fc19.x86_64--e0a5e358-e8d7-4fb9-8abd-81334f0c1112' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  b238e718-da90-470e-b533-fab66caf2ef2
        else
          search --no-floppy --fs-uuid --set=root b238e718-da90-470e-b533-fab66caf2ef2
        fi
        linux /vmlinuz-3.12.5-200.fc19.x86_64 root=/dev/sda10
        initrd /initramfs-3.12.5-200.fc19.x86_64.img
    }
    menuentry 'Fedora release 19 (Schrödinger’s Cat) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.12.6-200.fc19.x86_64--e0a5e358-e8d7-4fb9-8abd-81334f0c1112' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  b238e718-da90-470e-b533-fab66caf2ef2
        else
          search --no-floppy --fs-uuid --set=root b238e718-da90-470e-b533-fab66caf2ef2
        fi
        linux /vmlinuz-3.12.6-200.fc19.x86_64 root=/dev/sda10
        initrd /initramfs-3.12.6-200.fc19.x86_64.img
    }
    menuentry 'Fedora release 19 (Schrödinger’s Cat) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.9.5-301.fc19.x86_64--e0a5e358-e8d7-4fb9-8abd-81334f0c1112' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  b238e718-da90-470e-b533-fab66caf2ef2
        else
          search --no-floppy --fs-uuid --set=root b238e718-da90-470e-b533-fab66caf2ef2
        fi
        linux /vmlinuz-3.9.5-301.fc19.x86_64 root=/dev/sda10
        initrd /initramfs-3.9.5-301.fc19.x86_64.img
    }
}

```

For reference I've attached my complete grub.cfg file (as grub-cfg.txt).
[ATTACH]251987[/ATTACH]

Youll notice that it boots vmlinuz-0-rescue by default, and it only mentions the actual numbered kernels in the Advanced Options.

So my questions are these:
1.  How do I get Ubuntu to list the numbered kernels first (specifically vmlinuz-3.12.6-200.fc19.x86_64, and the rescue kernels in the Advanced Options?
2.  Would I be better off just adding them to the 40_custom file, and manually updating that file with every kernel upgrade?
3.  (Probably something that can't be answered here) Can I uninstall GRUB completely from Fedora, since I don't use it, and it only causes issues when I try to? Or can I make it so the Fedora GRUB only adds Fedora entries to its loader? (this way I could chainload them, and let it handle any Fedora upgrades, while the Ubuntu GRUB that I use by default handles the rest)

I'm sure as this thread progresses, I'll have more questions.

Thanks, and have a great weekend.:)
Patrick.

---

### Post by carl4926 on 2014-04-12
Mount the Fedora root partition in Nautilus

Now with your terminal do

```
sudo update-grub
```
Does that help?

---

### Post by oldfred on 2014-04-12
You show Windows in UEFI boot mode. 
Are both Ubuntu & Fedora installed in UEFI boot mode?
If so you should be booting Fedora's efi file in the efi partition.
You cannot start booting in one mode and boot another system from grub menu that is in different boot mode.
UEFI & BIOS are not compatible. You can only boot systems in different modes from UEFI/BIOS menu.

It also looks like you ran Boot-Repairs rename. Does your system not boot an ubuntu entry in UEFI? If you can boot ubuntu entry you do not need the rename as that make the boot of the Windows UEFI entry actually boot into grub and then you an only boot Windows from grub menu.
Only some systems have modified UEFI to only boot Windows. What system, model is this?

May be best to see all details:
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

