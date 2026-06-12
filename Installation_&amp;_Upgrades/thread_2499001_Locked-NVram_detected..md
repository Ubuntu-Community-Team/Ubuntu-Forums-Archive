---
title: "Locked-NVram detected."
date: 2024-07-07
forum: Installation &amp; Upgrades
---

### Post by noviceubunruuser14 on 2024-07-07
Hello

After I had installed on my PC Ubuntu 24.04 I have got an error - after I tried to launch only grub terminal appears.

I found that Boot repair can fix my problem. Message that it gives me "Boot successfully repaired."

Yet I have another massage below - "Locked-NVram detected."

So after I rebooting I still have an error - only grub black terminal 

[https://paste.ubuntu.com/p/w6sgkYJVMQ/](https://paste.ubuntu.com/p/w6sgkYJVMQ/)

---

### Post by oldfred on 2024-07-07
Can you directly boot ubuntu entry in UEFI one time boot menu?
Or can you press escape just after vendor logo, but before grub menu normally appears and boot recovery mode from grub menu?

Locked NVRam error is not an error, other than it is trying to mount efivars in wrong place.
Its looking in kernel folder & it really is here and your system shows it on line 196.
This is from my mount command.
[FONT=monospace][COLOR=#000000]efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)[/COLOR]

You already have a correct UEFI entry so this may work if reinstalling grub.
If you have UEFI boot entry, you can add this: You could add "--no-nvram" to the "grub-install" command and the "error" should not appear, as the boot entries in the NVRAM are not [/FONT]touched/updated.
[FONT=monospace]
[/FONT]

---

### Post by noviceubunruuser14 on 2024-07-08
Nothing is happening while I press 'esc' button right after vendor logo. I steel see a grub console after.

And I noticed that there are an error right after vendor logo

"error file '/boot/' not found" or something similar

---

### Post by oldfred on 2024-07-08
I do not know btrfs, but thought the grub entries used sub-volumes somehow.
There may be some advantages to the other Linux formats, but I think they are more for advanced users.
Ubuntu's standard is ext4.
Some I have seen with other formats use ext4 for / (root) and then other formats for data.

Are you getting grub>
can you press enter?

```
ls # Do you see (hd0), (hd0,2) ? If so, run the next command. Change if not hd0,2.
configfile (hd0,2)/boot/grub/grub.cfg
OR:
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/boot/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/boot/initrd.img
boot

```

---

