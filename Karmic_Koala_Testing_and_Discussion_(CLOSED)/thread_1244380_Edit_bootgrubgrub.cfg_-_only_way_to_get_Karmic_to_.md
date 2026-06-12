---
title: "Edit /boot/grub/grub.cfg - only way to get Karmic to run GDM"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Lutin on 2009-08-19
So much for the warnings on NOT editing /boot/grub/grub.cfg. Adding "acpi=off" to the kernel line is the only way that I have found of getting Karmic to boot-up into GDM.

This is on an, admittedly oldish, Dell Dimension 2400 with integrated Intel graphics.

Well, at least I have it running now.

---

### Post by BwackNinja on 2009-08-19
instead of editing grub.cfg, edit /etc/default/grub and add acpi=off to GRUB_CMDLINE_LINUX_DEFAULT so you don't have to keep messing with grub.cfg every time there is a kernel update

---

### Post by kestal on 2009-08-19
If wonder if this is linked to the same problem I had. Did you just get stuck at tty1?

I had this with 9600m intel though..

---

### Post by Lutin on 2009-08-19
> **kestal said:**
> If wonder if this is linked to the same problem I had. Did you just get stuck at tty1?

I had this with 9600m intel though..

I just couldn't get GDM to start at all. Karmic would boot into command line mode okay, but no way was I getting GDM to come up.


> **BwackNinja said:**
> instead of editing grub.cfg, edit /etc/default/grub and add acpi=off to GRUB_CMDLINE_LINUX_DEFAULT so you don't have to keep messing with grub.cfg every time there is a kernel update

Thanks for that, I'll change it now.

---

### Post by ranch hand on 2009-08-20
You can also go to /etc/grub.d and create a document 06_new (any name will do) and put in the version that you get when you edit grub.cfg.

This will be at the top of your menu when it comes up.



The document should look like this;
```

#!/bin/sh
# This file is an example on how to add custom entries

echo "Adding Jaunty on sda8" >&2
cat << EOF
menuentry "Jaunty 9.04, kernel 2.6.28-14-generic (on /dev/sda8)" {
        set root=(hd0,8)
        search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
        linux /boot/vmlinuz-2.6.28-14-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
        initrd /boot/initrd.img-2.6.28-14-generic
}
EOF

EOF
echo "Adding Mandriva2009-1-Gnome on sda12" >&2
cat << EOF
menuentry "Mandriva" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
EOF

```
I just grabbed 2 entries for examples.  You can edit grub.cfg and cut copy to your custom file (mine is 06_custom)

I included the second entry because Mandriva would not boot with the info that os-prober got and thisis what was recommended to me on the forums here.  Works great and should actually work for ANY OS.  I have 2 Mandrivas on one drive and 2 on another and this works great.

The custom file is the way to go if you want to label your entries too.  The stuff that shows up on the menu is between the "" marks;
```

menuentry "Jaunty 9.04, kernel 2.6.28-14-generic (on /dev/sda8)" {

```

---

### Post by dino99 on 2009-08-20
hey guys,
i'm afraid that karmic can't find his kids with those multi config files: i would say the simplest the better.

We need only a clear logical config file.

---

