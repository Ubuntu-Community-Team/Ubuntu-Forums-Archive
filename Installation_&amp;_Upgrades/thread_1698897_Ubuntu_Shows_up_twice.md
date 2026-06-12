---
title: "Ubuntu Shows up twice??"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by akTHEbak on 2011-03-02
i recently installed ubuntu 10.04 LTS on a partition i made with windows. I then used the updater which comes with ubuntu the update manger. I upgraded to 10.10. Now when i turn on my computer ubuntu shows up twice. like 2 options. i want to know how i can get rid of the other one

---

### Post by redcodefinal on 2011-03-02
I would first try
```
sudo update-grub
```
That should update the grub entries and get rid of it

---

### Post by redcodefinal on 2011-03-02
[LEFT]Also the other one might be the recovery mode so it won't go away.
[/LEFT]

---

### Post by akTHEbak on 2011-03-03
> **redcodefinal said:**
> I would first try
```
sudo update-grub
```That should update the grub entries and get rid of it


root@akthebak-desktop:~# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-27-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-27-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda4
done

that wat it says...

---

### Post by akTHEbak on 2011-03-03
> **redcodefinal said:**
> [LEFT]Also the other one might be the recovery mode so it won't go away.
[/LEFT]


i tried the sudo update-grub.....it still comes up to the same thing..but when i go to the second option it boots 10.10 as well

like it comes up as Ubuntu with linux 2.6.xx
Ubuntu with linux 2.6.xx(recovery mode)
Ubuntu with linux 2.6.xx
Ubuntu with linux 2.6.xx(recovery mode) 
Windows 7
Windows Vista(Loader)this comes up because of the factory image with my pc

thats how my boot menu looks..anyways to keep it to 1?

---

