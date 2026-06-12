---
title: "Upgrade from 32 bit to 64 bit"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by tilixibr on 2010-04-29
Ok, so I recently saw that I'm getting a notification telling me about the new 10.04 release on my taskbar, **but**, I discovered that my processor is 64 bit, after installing the 32 bit Ubuntu 9.10 (that was a long time ago, but had no issues whatsoever). Is there a way that I can upgrade from 32 bit Ubuntu 9.10 to a 64 bit Ubuntu 10.04 without having to burn another live CD?

I'll post my laptop's conditions in case there might be some issues:

Model: Compaq CQ60
CPU: AMD Athlon X2 (64 bit) (dual-core)
GPU: NVidia GeForce 8200M G
RAM: 2.7 GB
HDD: 250 GB (currently using 20 GB for the linux partition, the rest is a partition that used to have windows, but still has all the files in it)

OS: 
Ubuntu and Kubuntu 9.10
A Windows Vista partition which will be deleted after all the files are backed up

---

### Post by bumanie on 2010-04-29
you have to reinstall with 64bit. It's going to take downloading a new .iso and then either using a cd or a usb or unetbootin to install it.

---

### Post by eyelessfade on 2010-04-29
Probably some small possibility, but I wouldn't try it if I where you. Your best bet is to install a clean 64 bit.

To remember what packages you had do a
```
dpkg --get-selections > mypackages.txt
```
on the old install, and after reinstall

and on the new shiny 64-bit
```
sudo dpkg --set-selections < mypackages.txt
sudo apt-get dselect-upgrade
```

should do the trick. Can't guarantee 100% though :)

---

### Post by tilixibr on 2010-04-29
Thanks, at least i got the download part done, which I had done when I was trying out lucid. I had thought: Lets see if I can run lucid  64 bit on Vbox. Since i was using a 32 bit OS, it didnt work, but now at least i already have the .iso file :)

---

### Post by tilixibr on 2010-04-29
I forgot to ask one more thing. Since I'm going to transfer the files from the "old" Ubuntu partition to the new partition, I'll install 10.04 on a new partition, copy the files and delete the old partition once I'm done. How will I take care of GRUB? When the installation process asks to install GRUB, what do I do? I already have GRUB installed. I know I should not install it again, so how will I configure it to add the new Ubuntu partition to the boot list? Will it do it automatically or will I have to do it manually?

---

### Post by tilixibr on 2010-04-30
Installing Ubuntu 10.04 right now, and I'm impressed that it's a lot faster than 9.10 when using the Live CD :D, and the graphics are fast even without my graphics driver installed!!!! Let's pray that I don't get any problems with it [-o<

---

### Post by -Zeus- on 2010-04-30
> **tilixibr said:**
> Thanks, at least i got the download part done, which I had done when I was trying out lucid. I had thought: Lets see if I can run lucid  64 bit on Vbox. Since i was using a 32 bit OS, it didnt work, but now at least i already have the .iso file :)

Wait, you couldn't run 10.04x64 on 9.10x86 with vbox?  ATM I'm running WinXPx64 on 10.04x86... I just don't have multi-processor core support.

---

### Post by tilixibr on 2010-04-30
> **-Zeus- said:**
> Wait, you couldn't run 10.04x64 on 9.10x86 with vbox?  ATM I'm running WinXPx64 on 10.04x86... I just don't have multi-processor core support.
  No, I tried it and it gave me an error saying that it doesnt support 64 bit OS's =\

 But now I don't have to worry about that because my installation is at 95% right now :biggrin:

---

### Post by tilixibr on 2010-04-30
Okay, so I tried installing the new distro without installing grub ( bad idea), when i restarted, i got the message:
```
Error: file not found
grub rescue>
```So I fired up the Live CD again and had to reinstall, this time including the boot loader.

Another issue, Grub 1.98 is extremely slooow, even slower than 1.97~, whats up with that? It takes a good 10 seconds to show the boot menu and the keyboard takes 2 seconds to take effect to change the highlighted OS:(

When I get home I'll downgrade to grub 1.97~

Other than that, everything is working perfectly :D

---

