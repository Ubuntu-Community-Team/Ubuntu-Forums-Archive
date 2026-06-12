---
title: "X server on liveCD versus installed"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by openhacker on 2008-02-10
I have a VIA video controller (the bios says:
[   59.252518] agpgart: Detected VIA VT3314 chipset

lspci says:
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA])

X.log says:
(II) VESA(0): VESA VBE OEM: VIA P4N800 PRO

Turns out I can't run graphics when I install 7.10 gutsy gibbon.
I'm playing around with persistent usb boot images and I installed 
the diskful /usr/bin/Xorg instead of the cdrom version of Xorg
(which works)

For reference:
   text    data     bss     dec     hex filename
1696171   57040   62012 1815223  1bb2b7 Xorg
1695995   57040   62012 1815047  1bb207 Xorg.iso.ubuntu
-rwxr-xr-x 1 root root 1755000 2008-02-09 15:11 Xorg
-rwxr-xr-x 1 root root 1754808 2008-02-09 15:10 Xorg.iso.ubuntu
where xorg is the one from the disk, and Xorg.iso.ubuntu is the distributed version on the 7.10 cdrom...

marty

---

