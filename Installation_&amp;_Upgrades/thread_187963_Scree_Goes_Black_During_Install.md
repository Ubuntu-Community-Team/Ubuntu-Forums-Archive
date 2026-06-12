---
title: "Scree Goes Black During Install"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by kingsidy on 2006-06-03
I tried to install Dapper on an Acer 4202 with the intel duo and the intel 950 express graphic card. The installation starts fine. After it copies the files, the screen suddenly goes black with a few artifacts. It then just stays like that. Nothing happens. I suspect that the Xserver has issues with the graphic card. The installation never finishes. I am thinking about installing it as a server and then adding gnome and kdm. and edit the xserver. If anybody has any more details about your experience with the acer with the intel duo please post.

I also get an error at the beginning when the install cd boots. It says 
PCI: cannot allocate ressource region 7. Does anybody else get that error if you were succesful at getting rid of it how??? It seems like it does not affect anything but it is annoying.

---

### Post by usernamed on 2006-06-03
[QUOTE=kingsidy]I tried to install Dapper on an Acer 4202 with the intel duo and the intel 950 express graphic card. The installation starts fine. After it copies the files, the screen suddenly goes black with a few artifacts. It then just stays like that. Nothing happens. I suspect that the Xserver has issues with the graphic card. The installation never finishes. I am thinking about installing it as a server and then adding gnome and kdm. and edit the xserver. If anybody has any more details about your experience with the acer with the intel duo please post.

I also get an error at the beginning when the install cd boots. It says 
PCI: cannot allocate ressource region 7. Does anybody else get that error if you were succesful at getting rid of it how??? It seems like it does not affect anything but it is annoying.[/QUOTE]

How early in the installation is this happening?  If it's happening within the first minute of boot I suspect that the laptop doesn't like the framebuffer.  If this is the case, begin the installer with 'linux debian-installer/framebuffer=false'

If it's happening at the end of the install, then definitely an xorg driver issue.

---

### Post by kingsidy on 2006-06-03
it happens towards the end of the install. I think that it might be and xorg issue. However the installation never completes. therefore i cannot edit the xorg file because the install never completes. i have tried a lot of the special instructions like noapic and such, still does not work.

---

### Post by kingsidy on 2006-06-07
It finally installed. However i still get the error: PCI: cannot allocate ressources region 7 and 8. does anybody know anything about that

---

