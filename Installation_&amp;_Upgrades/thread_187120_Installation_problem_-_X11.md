---
title: "Installation problem - X11"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by NinjaZombie on 2006-06-02
Hello all!

I downloaded the desktop-i386 ISO9660 image of the brand new Diaper Dake release. It boots fine until it tries to start X. Then vertical stripes in gay purle colour appear on my screen and I can't do nothing, everything freezes. I tried every possible video resolution (by pressing F4 on the boot prompt). I have some NVidia video card in my computer, don't really know which model.
Is it possible to start the install in the good ole text mode, or at least change the X11 video driver to VESA or VGA for the installation?

Thanks a bunch.

---

### Post by mscman on 2006-06-02
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by NinjaZombie on 2006-06-02
[QUOTE=mscman]```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

Thanks for your quick reply. I'd like to do what you suggested, but I can't switcth  to another tty. CTRL+ALT+F1, F2... etc does nothing. The stupid computer is completely frozen, it doesn't respond to anything. I even tried kicking it hard, but it wouldn't budge. I also messed with BIOS setting, disabled ACPI, tried booting with ACPI=OFF to no avail. Obviously, I will have to spend another boring weekend with my old Breezy :-? . I'll try the alternative CD next week. Ugh.:( Or maybe I'l shoot myself.

---

### Post by tseliot on 2006-06-02
[QUOTE=NinjaZombie]Thanks for your quick reply. I'd like to do what you suggested, but I can't switcth  to another tty. CTRL+ALT+F1, F2... etc does nothing. The stupid computer is completely frozen, it doesn't respond to anything. I even tried kicking it hard, but it wouldn't budge. I also messed with BIOS setting, disabled ACPI, tried booting with ACPI=OFF to no avail. Obviously, I will have to spend another boring weekend with my old Breezy :-? . I'll try the alternative CD next week. Ugh.:( Or maybe I'l shoot myself.[/QUOTE]
Ok, there's no need to commit a crime against yourself or your computer :p 

Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

Then type:
```
nano -w /etc/X11/xorg.conf
```

Scroll down the file with your keyboard until you find the Section Device

Set the driver to "vesa"

Then type CTRL+X to exit (save the file)

Restart your computer:
```
reboot
```

Boot as usual and you should be able to see the graphical interface (the desktop enviroment).

If that doesn't work, repeat the process I described above but this time set the driver to "vga".

---

### Post by NinjaZombie on 2006-06-02
[QUOTE=tseliot]
Then type:
```
nano -w /etc/X11/xorg.conf
```
```
reboot
```
[/QUOTE]

/etc/X11/xorg.conf is read-only, I can't save it. OMG, I will have to spend the entire weekend with my fiancee instead of apt-getting packages. Oh, the cruel world. ](*,)

---

### Post by Carrots171 on 2006-06-02
I believe that you need to do: 

**sudo** nano -w /etc/X11/xorg.conf 

so you have the permissions to save it.

---

### Post by josir on 2006-11-03
Just to add more tips on this topic (it happens to me):

if you type

sudo dpkg-reconfigure xserver-xorg

and if you get an error message

or if you can't access /etc/X11 directory, probably your X11 server packages was not installed for some reason.

To install it, you should do:

apt-get install xserver-org

Good Luck,
Josir

---

