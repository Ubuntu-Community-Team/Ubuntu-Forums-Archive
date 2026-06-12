---
title: "what file to boot from"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by ninja85a2 on 2015-10-31
how do i install ubuntu gnome from just the GRUB interface? i used the [http://rufus.akeo.ie/](http://rufus.akeo.ie/) tool to write it to the usb stick and somehow that worked :D

---

### Post by oldfred on 2015-10-31
What brand/model laptop.
And what video.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by ninja85a2 on 2015-10-31
ive got a asus X555L [https://www.dropbox.com/s/jrk8x0hgeb5e3dv/2015-10-31%2015.03.18.jpg?dl=0](https://www.dropbox.com/s/jrk8x0hgeb5e3dv/2015-10-31%2015.03.18.jpg?dl=0) this is the bios boot order screen

---

### Post by oldfred on 2015-10-31
I would also turn the fast boot off, at least until you are fully configured. That can make it difficult to get back into UEFI.
Do you have secure boot on? If so you may need to specifically allow USB booting in another setting somewhere. Or turn off secure boot.
You should have two entries for USB flash drive if correctly configured as a bootable device. One is UEFI & name/label of flash drive and other is just name/label.

---

### Post by ninja85a2 on 2015-10-31
even if i choose the one with UEFI and boot to that it still goes to the GNU GRUB

---

### Post by oldfred on 2015-10-31
From installer or from an actual install.
With UEFI you should get the grub menu and you boot that. If you need special boot parameters as many laptops do, then you have to manually add them to the Linux line.

It looks like your model includes an nVidia chip. Do you know if booting it is using the Intel video mode or the nVidia video. If nVidia you need nomodeset boot parameter:
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

If Intel Video you may need one of these:
      
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by sudodus on 2015-10-31
> **ninja85a2 said:**
> how do i install ubuntu gnome from just the GRUB interface?

Is it important to install Ubuntu from the grub interface, or can you try 'any' method to install ubuntu gnome?

Do you mean the you want to boot the iso file via grub, what I call 'grub-n-iso'? Or do you mean that you want to boot an installed system (which is 'always' booted via grub)?

---

### Post by ninja85a2 on 2015-10-31
i want to boot the iso file via grub and my laptop doesnt have a nvidea gpu it has intel graphics

---

### Post by VMC on 2015-10-31
> **ninja85a2 said:**
> how do i install ubuntu gnome from just the GRUB interface?

This is kinda confusing. Do as sudodus suggested and boot from a live cd/usb. If you want grub to boot the iso, then were talking loopback. See [this thread.]("https://help.ubuntu.com/community/Grub2/ISOBoot/Examples")

---

### Post by ninja85a2 on 2015-10-31
> **VMC said:**
> This is kinda confusing. Do as sudodus suggested and boot from a live cd/usb. If you want grub to boot the iso, then were talking loopback. See [this thread.]("https://help.ubuntu.com/community/Grub2/ISOBoot/Examples")
no im saying that no matter what i do it always starts in the grub so i dont know what to do to make it not do that

---

### Post by sudodus on 2015-10-31
> **ninja85a2 said:**
> i want to boot the iso file via grub and my laptop doesnt have a nvidea gpu it has intel graphics

Intel graphics is often easy to manage with linux. Can you also tell us exactly the model/version of the graphics chip :-)

> **VMC said:**
> This is kinda confusing. Do as sudodus suggested and boot from a live cd/usb. If you want grub to boot the iso, then were talking loopback. See [this thread.]("https://help.ubuntu.com/community/Grub2/ISOBoot/Examples")

> **ninja85a2 said:**
> no im saying that no matter what i do it always starts in the grub so i dont know what to do to make it not do that

You can create a booting system according to *VMC's* link [Grub2/ISOBoot/Examples]("https://help.ubuntu.com/community/Grub2/ISOBoot/Examples"). ***Edit:*** and the wiki page above it, [Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot").


It is is probably easier to use a tool and create a DVD or USB drive from your Ubuntu Gnome ISO file, and boot from that drive. See the following link

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ninja85a2 on 2015-10-31
ive got it on a usb stick but for somereason the laptop ive got doesnt seem to like having linux booted onto it

---

### Post by sudodus on 2015-10-31
What iso file (with Ubuntu Gnome) file have you downloaded?

Have you checked the md5sum with the listed string in [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

How did you create the USB stick? [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Please ***describe in detail***, what happens when you try to boot from the pendrive :-)

---

### Post by ninja85a2 on 2015-10-31
[IMG]https://www.dropbox.com/s/i0lqnslzkauhzxc/2015-10-31%2016.04.04.jpg?dl=0[/IMG]
this is what comes up when i boot from the usb stick
[https://www.dropbox.com/s/i0lqnslzkauhzxc/2015-10-31%2016.04.04.jpg?dl=0](https://www.dropbox.com/s/i0lqnslzkauhzxc/2015-10-31%2016.04.04.jpg?dl=0)

---

### Post by sudodus on 2015-10-31
You arrive at the grub prompt.

Please reply also to the other questions in post #13. Knowing the answer makes it easier to suggest a solution. Otherwise we can only guess.

---

### Post by ninja85a2 on 2015-10-31
well ive managed to get it to work by using a different tool to write the image to the usb stick dont know why but it worked so im happy :D

---

### Post by sudodus on 2015-10-31
Congratulations :KS

Please share your solution (which tool) and click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

-o-

Edit: Thanks for sharing :-)

Other users: See the first post (edited to share the solution)

---

