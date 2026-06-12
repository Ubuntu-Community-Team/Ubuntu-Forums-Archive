---
title: "Installation fails when detecting mouse"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by hfoucher on 2005-04-09
I burnt the ISO image of the installer downloaded this morning and booted.

20 seconds after boot, the following message appears and the install stalls:

*[... tons of text based messages with no apparent errors ...]*
input: USB HID v1..10 Mouse [Logitech Optical USB Mouse]
on usb-000:00:1d.3-2
usbcore: registered new driver usbhid
drivers/usb/hid-core.c : v2.0 : USB HID core driver
mice: PS/2 mouse device common for all mice

I waited 10 minutes but nothing happened. The CD ROM is not turning at all and I can even eject it.

Help!

PS: I have a Dell Dimension 8400

---

### Post by heimo on 2005-04-09
What I'd try.... remove mouse (you really don't need it when installing) and try again. Also the media may be defected, you could try checking the MD5 of the iso file and if that's ok, try burning the CD again. Also check your BIOS settings, try setting hard disk "access mode" to LBA - if you have any overclocking, go back to stock clock speed. You can also try playing with ACPI settings (disable / enable).

In Linux you can check MD5 of a file by running 'md5sum filename'. The correct "checksums" md5-values can be found in the same directory you downloaded the iso file from. For example: ([http://se.releases.ubuntu.com/5.04/MD5SUMS](http://se.releases.ubuntu.com/5.04/MD5SUMS)) 

[INDENT]
46135038af6dd2ef36fd8d521afe7de4  ubuntu-5.04-install-amd64.iso
**f6b3f164c99761234858a4d2c12d0840  ubuntu-5.04-install-i386.iso**
bf3fe18eb2fbc450769237dec189405b  ubuntu-5.04-install-powerpc.iso
[/INDENT]

Hopefully you can get it running. Stay tuned to this thread for more advice and better troubleshooting hints.

PS. Oh, you're using PC, so the i386-version of iso file is probably the one you're using (in bold).

---

### Post by hfoucher on 2005-04-09
Thanks for your advices. I checked the MD5. It is correct.
I will check the BIOS and try unplugging the mouse and let you know.

---

### Post by heimo on 2005-04-09
I went searching in Google and seems like the key could be to change SATA settings to COMBINED (if you can find this setting) rather than RAID or what ever it's by default. Is your hard disk serial ATA (SATA)? 

[http://www.fedoraforum.org/forum/archive/index.php/t-21328.html](http://www.fedoraforum.org/forum/archive/index.php/t-21328.html)
[http://www.linuxquestions.org/questions/archive/47/2004/12/1/232710](http://www.linuxquestions.org/questions/archive/47/2004/12/1/232710)

I also had problems installing to SATA disks, but only after the base install was done and I was rebooting. Grub (default bootloader) didn't work with my Epox / VIA motherboards VT8237 SATA controller (or at least I couldn't get it to cooperate) and I had to use LILO.

Cheers!

EDIT: Oh, I know the links are to different distributions, but both were on similar Dell. This is just a hunch - there has obviously been trouble installing any Linux on your computer model. The same problem could cause different kind of symptoms on different install programs. You can also try PATA/SATA -setting.

---

### Post by hfoucher on 2005-04-16
Ok, I changed the BIOS parameter for SATA to COMBINED and I could launch the installation with no problem.

However, now, I need to change back the parameter if I want to use Windows. :-? 

As I don't want to reinstall Windows and want to keep a proper support of SATA drives, is there any way to get SATA to work once Ubuntu is installed, for example by getting a new kernel ? Otherwise, would a recomplilation of the kernel solve my problem?

Thanks in advance.

---

### Post by heimo on 2005-04-16
This may be related:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1440](https://bugzilla.ubuntu.com/show_bug.cgi?id=1440)

See also this:
[http://lists.ubuntu.com/archives/kernel-bugs/2005-March/000322.html](http://lists.ubuntu.com/archives/kernel-bugs/2005-March/000322.html)

I'm not sure what you should do. :-/ Does the loading of Ubuntu hang (now as it's installed) if you have the BIOS setting 'SATA' enabled? 

Maybe someone with better understanding of this problem and / or some first hand experience can give more information?

---

