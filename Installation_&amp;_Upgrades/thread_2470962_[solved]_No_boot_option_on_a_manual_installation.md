---
title: "[solved] No boot option on a manual installation"
date: 2022-01-18
forum: Installation &amp; Upgrades
---

### Post by iutech on 2022-01-18
[FONT=arial]I'm trying to follow this tutorial for a LVM on LUKS installation, as the installer craps on me when I try to do it directly from the installer : [URL="https://gist.github.com/labbots/0d66f0eea653624329f7e1fabef3e25c"]https://gist.github.com/labbots/0d66f0eea653624329f7e1fabef3e25c
[/URL]
But when I get to the "installation from the live OS" part, I don't see a way to "set /dev/nvme0n1p2 as /boot" ?
I only have  "zone réservée pour le chargeur d'amorçage BIOS" which later appears as "biosgrub".

From what I checked on the net biosgrub is only needed for booting GPT partitions in legacy, but the computer I'm installing unto can't boot on legacy, only on UEFI.
So I guess biosgrub is the wrong choice ?
But why don't I have any option to set the partition as /boot ?

I tried to continue the tutorial anyway while having set  /dev/nvme0n1p2 as biosgrub, but then when I reach the post-installation part there is no /efi on the /boot I mounted on /mnt/boot.
I have a vague idea of what the post-installation part is doing, but not enough to understand whether the "rebuild boot files" part will work if there is no /efi on /mnt/boot (nor if I create it myself with a mkdir).

And if the boot is not correctly set, I have no idea how to correct that myself...
[/FONT]

---

### Post by iutech on 2022-01-18
Follow-up : I tried to pursue the tutorial anyway, but then the update-grub final part answers ```
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
/usr/sbin/grub-mkconfig: 269: cannot create /boot/grub/grub.cfg.new: Directory nonexistent
``` and quite logically when rebooting the computer doesn't know where to find the encrypted disk and just shows a grub command prompt.

Also, reading [this]("https://help.ubuntu.com/community/ManualFullSystemEncryption") I did turn secure boot off (after the installation though, but from what I understand it shouldn't prevent the boot once deactivate - and anyway the inability to update the grub is a much more likely explanation for inability to boot on restart).

---

### Post by oldfred on 2022-01-18
I have not installed LVM.
But are you booting live installer in UEFI mode.
The mode you boot live installer UEFI or BIOS is then how it installs.
UEFI setting for UEFI or old BIOS/CSM/Legacy is then only for the installed system.

And if installing in UEFI mode it will want an ESP - efi system partition, FAT32
Of if installing in BIOS/CSM mode, it will want a bios_grub partition if drive is gpt (which it should be no matter how you install).

Since only wanting bios_grub it sounds like you are booting installer in BIOS mode?

---

### Post by MAFoElffen on 2022-01-19
If the installer mentions biosgrub, then it thinks it booted the USB with the install media as Legacy... What Veriosn, Edition and flavor of Ubuntu are you trying to install? (I need to know the full name of the ISO file)

Because at the point, if I got that message, I would pop out to a shell and do this:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```
That would confirm if there is problem with the installer just being confused, or the installer noting which boot mode there was. The installer is rarely confused about something like that.

---

### Post by iutech on 2022-01-21
No, it was UEFI (the computer BIOS doesn't offer legacy boot).

The problem was that the tutorial didn't explain that one has to first select the format of the second partition before setting boot as the mounting point (yes, it's quite obvious in retrospect, but I was following the tutorial closely as to not make mistakes, so I didn't notice the problem, especially as I already had set the partition to be formatted in ext4 with gparted, per the first step of the tutorial).

---

