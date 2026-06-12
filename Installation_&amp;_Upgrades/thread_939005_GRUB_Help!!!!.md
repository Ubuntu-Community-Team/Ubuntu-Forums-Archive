---
title: "GRUB Help!!!!"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by TheRiddler12 on 2008-10-05
I formatted my C:\ drive but GRUB still tries to boot :O how can  stop this happening 

thanks in advance.

---

### Post by Elfy on 2008-10-05
You've uninstalled ubuntu and are left with grub failing or something else?

If that's the case use your win disc to restore the windows bootloader

---

### Post by TheRiddler12 on 2008-10-05
i dont have a windows disc to restore the MBR, is there another way i can fix it ?

---

### Post by GuDoN on 2008-10-05
What exactly do you mean? You want grub to boot your linux? Windows bootloader to take over, even though you formatted it's drive?? 

Grub is on your linux partition? More info, expecting help with two sentences isn't really helping anyone here, especially yourself.

Please explain your case to us. :)

---

### Post by GuDoN on 2008-10-05
> **TheRiddler12 said:**
> i dont have a windows disc to restore the MBR, is there another way i can fix it ?

Try [http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

---

### Post by TheRiddler12 on 2008-10-05
ok ill explain it all now, i had a dual boot system with ubuntu on my external hdd and xp on my internal one, i decided against linux now, and i wanted to uninstall it, i read that if i fix the MBR then jus format the external drive everything should be ok, but i formatted my drive but grub still boots up even though the external drive isnt plugged in and i want to stop this from happening so i can just go back to having xp as my only operating system

---

### Post by Elfy on 2008-10-05
then you need to fixmbr if you don't have the windisc then go with the supergrub option as gudon has given you can get the supergrub here

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It has to be burnt as an iso and then you boot with it.

---

### Post by TheRiddler12 on 2008-10-05
so when i boot up the supergrub disc what do i ?

---

### Post by Elfy on 2008-10-05
Once it has started follow the menus to the win options and use it - it should uninstall grub from the mbr for you - screenshots above show it

---

### Post by TheRiddler12 on 2008-10-05
ive burnt the iso u gave me directly and it wont boot :( ive run out of ideas now :(:( any help at all is greatly appriciated

---

### Post by Elfy on 2008-10-05
Did you burn it as an iso or data?

Is your pc/laptop setup to boot from cd first?

---

### Post by TheRiddler12 on 2008-10-05
i tried it as both incase one wasnt working and yeh it jus says, Operating system not found unless i plug my external hard drive in and grub loads

---

### Post by Elfy on 2008-10-05
Does the buntu livecd boot? If it does then there is something wrong with the discs you have burnt.

IF no discs boot then you need to check that you are booting with cdrom first.

---

