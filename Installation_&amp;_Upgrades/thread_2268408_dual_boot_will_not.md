---
title: "dual boot will not"
date: 2015-03-08
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2015-03-08
Hi, I have a new Samsung ATIV Book 2. I tweaked the bios to get it to boot from a usb stick, and Ubu 14.04 installed no probs. However, the dual boot will not work. Below is the grub generated Windows entry, and a custom one I tried myself. Neither can boot Win 8. To boot Win I need to enter the bios, set 1st boot Windows boot manager. Any tips?


This is what I have then in grub.config

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-34F6-50C3' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  34F6-50C3
    else
      search --no-floppy --fs-uuid --set=root 34F6-50C3
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}

I also tried this, which someone told me, but it does but it does not work!

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'windoze 8' {
set root='hd0,gpt2'
chainloader /EFI/microsoft/BOOT/bootmgfw.efi
}
### END /etc/grub.d/40_custom ###

I wanted to have a look on /dev/sda2 Ubu cannot mount /dev/sda2 It says I  should shut Windows down fully, then try to mount it. All I can do is  shut Win down as normal!

Any tips out there? This is not too big a problem, as I only need win for my online bank really. I can go there via the bios.

---

### Post by grahammechanical on 2015-03-08
Did you install Ubuntu in EFI mode? Or legacy mode? If Windows 8 is installed in EFI then Ubuntu must be installed in EFI mode as well.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Windows 8 does not shutdown. It hibernates to give it a quick re-start and that is why Ubuntu cannot mount the Windows 8 partition. You need to find a way through the maze of Windows settings to switch off that feature.

Regards.

---

### Post by Pedroski55 on 2015-03-08
I just made a usb stick, changed the bios to boot from the stick and Ubu installed nicely. I do not know if it was legacy or EFI. In my bios, I can choose UEFI, UEFI and csm or csm. I chose UEFI and csm. However, I made the stick on this laptop, which runs 32 bit Ubu 14.04. I am downloading the 64 iso torrent now. 

I will try and make a usb stick from that somehow, then reinstall on the new laptop. Thanks for the links!

---

### Post by Pedroski55 on 2015-03-08
Ok now, I installed again. The 64 bit system installed in Uefi mode, no probs!

I set the bios to boot PO Toshiba SOMENUMBER as first boot device. It did not, went to Win. I restarted, pressed f2 and then the bios showed my usbstick as Innostar 1 or something Uefi. I set that as 1st boot device. Ubu installed rapidly.

Just all the stuff I copied yesterday from my old hd is gone. Have to do that again.

Thanks for the tips!!

Quick tip for anyone: in Win 8 go to Control Panel>Power settings, you can tell it to shut down, not hibernate. Or search 'How to shut down Win 8'

---

### Post by Mark Phelps on 2015-03-09
Pedroski55: Just so you know ... if you select Restart, then hibernation will STILL be enforced -- that is the new Win8 policy default.  You have to do Shut Down to avoid the hibernation.

---

