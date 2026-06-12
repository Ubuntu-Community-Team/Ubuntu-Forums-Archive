---
title: "USB install makes HD install unusable, grub problem"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Captain Giraffe on 2008-04-02
I tried to install hardy on an USB drive, but now my hd installation is unusable. 
The USB installation was made to make the usb drive bootable by itself, ie grub was only installed on the usb disk.

The really odd thing is that its WindowsXP that boots the hd installation, and the windows installation works fine.
The ntldr boot menu displays WinXP and ubuntu options as usual but when I try to boot ubuntu a locked grub blinks (not the grub command line, it doesnt get that far).
The boot directory and the rest of the ubuntu installation seems to be intact.
Any suggestions for a fix or a troubleshooting approach?

---

### Post by Captain Giraffe on 2008-04-02
I note that if i boot with my USB and change the entry for the HD installation of ubuntu to grub> root (hd1,1)  it works fine. It was originally (hd0,1), but this shouldnt have changed for the HD boot.
(bump)
Any thoughts are welcome.

---

