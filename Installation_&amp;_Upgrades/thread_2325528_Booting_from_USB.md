---
title: "Booting from USB"
date: 2016-05-23
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2016-05-23
I have a Dell XPS 11 whose BIOS booting sequence option can be change from using the OS already installed or booting from the GRUB2 menu but not directly to a USB. I have the grml2USB installed to enable the USB to be used as a boot loader but how do I do that. The only advice on the GRML site is to prevent the BIOS from booting and then insert the USB. Thanks Mike

---

### Post by angel mike on 2016-05-23
I have just seen oldfred's post on this topic - 8 Aug 2010 'How do I stop a computer from Booting' - will try that. Can I use the nano commands from the Terminal  to do this?  Have no toolbars on the desktop so using the terminal appears the only option apart from the web and downloads.

---

### Post by oldfred on 2016-05-23
I am not sure a post by oldfred back in 2010 would be very good. He was (is?) not too knowledgeable especially back then.

And most things that old do not apply now. That was back when grub legacy was still being used a lot.

Many new systems have separate UEFI/BIOS settings to allow USB boot. And some need UEFI secure boot off as USB boot is not secure or may need UEFI password to allow more settings. UEFI password common on Acer.

Do not know if 11 is common with 13 & 15 or not. Often models are similar across brand. With biggest differences between Intel versions and AMD versions.
 Dell support - Update on XPS 13/15 2016 Developer Edition availability
[URL="http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9"]http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9
      [/URL]
 Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960) 
     Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot
[http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)
[https://bugs.launchpad.net/dell-sputnik/+bug/1499323](https://bugs.launchpad.net/dell-sputnik/+bug/1499323) 

[URL="http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9"]
[/URL]

---

### Post by angel mike on 2016-05-23
Your probably right oldfred but I just before your post here I saw a web page about booting to a USB on a Dell XPS12. Your right the magic key for me is F12 with the USB plugged in ! I get a page with an option to boot to the USB. Dell operate a secure boot system but this does not affect it on this machine. it's taken me several weeks of trying different methods but I now know a bit more about partitions etc.
 1 will mark this tread as solved. 
Thanks again oldfred.

---

