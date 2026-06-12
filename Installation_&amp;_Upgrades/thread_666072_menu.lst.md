---
title: "menu.lst"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by money2themax on 2008-01-13
i was editing menu.lst with the help of rocket

[quote="rocket"]
gksudo gedit filename

sudo nano filename
[/quote]
whats nano do?
```

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=70ff6c9b-2314-4b9c-a109-11e0f3d9b618ro quiet splash **noapic**
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=70ff6c9b-2314-4b9c-a109-11e0f3d9b618 ro single
initrd        /boot/initrd.img-2.6.22-14-generic
title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

```^is there anything i need to mess with here other that the one in bold?

---

### Post by PmDematagoda on 2008-01-13
Nano is a CLI file editor.

And do you have any problem?

---

### Post by money2themax on 2008-01-13
yes the apic thing i have to put it in every time i boot up and i can't figure out how to fix it

---

### Post by zvacet on 2008-01-13
Save the file with **ctrl+o** and exit with** ctrl+x**.

---

### Post by money2themax on 2008-01-13
i got it saved but i want to not have to do that

---

### Post by Partyboi2 on 2008-01-13
I would add it to this part of grub menu.lst
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d roso it after you option added to it, it would look something like this
>  ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro **[COLOR=SeaGreen]noapic[/COLOR]**
Nothing wrong on what rocket has shown you, just means that when ever you have a kernel update you will need to re apply it. where as adding it to the #kopt=root line you will not need to update it when you kernel gets updated.
After you have added noapic remember to update grub
```
sudo update grub
```

---

### Post by money2themax on 2008-01-13
huh? kernel update whats that gonna do for me?

---

