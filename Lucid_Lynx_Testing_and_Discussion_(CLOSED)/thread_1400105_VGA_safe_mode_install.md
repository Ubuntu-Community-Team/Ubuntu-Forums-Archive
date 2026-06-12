---
title: "VGA safe mode install"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by juanJosepablos on 2010-02-06
Hi,
I Have got a  [Shuttle SK43G ]("http://www.shuttle.eu/_archive/older/en/sk43g.htm") that I want to install lucid. I am using todays version, and I am not able to see the screen to install.

it is using a S3/VIA KM400/KN400/P4M800 graphic card. [http://pci-ids.ucw.cz/read/PC/1106/7205](http://pci-ids.ucw.cz/read/PC/1106/7205)


 On this system I had installed 8.04 and 6.04 with not issues at all. It used to be a vga safe mode but I am not able to find it right now. I putt a vga=771 with not luck. can anyone en-light me?
Cheers

---

### Post by Ibidem on 2010-02-06
VIA  UniChrome graphics (per the specs you linked to)?
Sounds like you're asking for trouble.  I saw reports of some VIA board dieing with Lucid.  
If you can't see the screen, the graphics driver you're loading isn't working; vga=xxx probably wouldn't help, and it's deprecated in the new kernel.  
Is there an option to use a VESA or "safe mode" driver available when booting from CD?

If you could blacklist the VIA driver, that might help.
You might have to use the alternate (text mode) installer; one sure way to force it into safe (VGA) mode is to use an expert install, and at the end run a shell, chroot into /tgt (the "target" partition for installation), and use Aptitude to remove all drivers other than the VESA & fbdev drivers.
Any way to get into a text-mode root shell should work. 

Ibidem

---

### Post by juanJosepablos on 2010-02-06
ok,
I am not asking for the 3D support. So it would be a shame that this system is not working out of the box when It has been working fine on previous LTS  release
it is not exactly same bug (my system does not crash,is does not display propertly), this is similar:
 [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/311051](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/311051)

---

### Post by juanJosepablos on 2010-02-06
Weird.
Ctrl+F1 gives me the console.
Ctrl+F7 bring the desktop ok.
Sometimes I get the gdm login page. Not sure where to go from here.

---

