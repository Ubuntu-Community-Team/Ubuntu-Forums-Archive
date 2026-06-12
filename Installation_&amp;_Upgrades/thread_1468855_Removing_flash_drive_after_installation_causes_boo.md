---
title: "Removing flash drive after installation causes booting fail"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by ageless on 2010-05-01
Hi all. I'm installing the netbook remix 10.04 on HP Mini 5102. Installation goes fine and system is successfully started after the reboot. One problem - If I remove the flash drive used during the installation my new system fails to boot. I've played around by changing hd1 to hd0 in grub.cfg but this didn't helped.

Please, any suggestions?

---

### Post by Herman on 2010-05-01
By the sounds of things you have GRUB installed to MBR in the USB drive.
Leave your flash drive in and boot Ubuntu, then install GRUB to MBR in your internal disk.

EDIT: Link - [How  To Re-install GRUB2 from within Ubuntu]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-install")

---

### Post by ageless on 2010-05-01
> **Herman said:**
> By the sounds of things you have GRUB installed to MBR in the USB drive.
Leave your flash drive in and boot Ubuntu, then install GRUB to MBR in your internal disk.

EDIT: Link - [How  To Re-install GRUB2 from within Ubuntu]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-install")

OK (I've already tried this but maybe I was missing something).

One update: on the final screen (before the installation process starts) there is a button called "Advanced" and installing grub to the flash drive seems to be selected by default. Isn't this a kind of bug? I've selected the correct hard drive and trying to reinstall...

---

### Post by ageless on 2010-05-01
Yes, it helped.

---

### Post by Herman on 2010-05-01
> Yes, it helped. 	
You have fixed it? :)
> Isn't this a kind of bug?It's a bug in a way, but it's not a bug in Ubuntu or in GRUB really. I think it's a problem caused by the lack of clearly defined conventions  being drawn for computer BIOS designers back in earlier times, but I'm  only guessing.
 It seems that the are no hard and fast rules about how computers should number their drives, IDE, then SATA then USB, or some other sequence. Apparently it's not possible to design an operating system installer that can correctly understand the information in the BIOS regarding this matter.

This kind of problem has been happening since before I joined this forum, and I've been hanging around here almost since the beginning, since the first Ubuntu release anyway. I think it predates Ubuntu by a long way.
Since UUID booting and file system mounting has come in, problems simialr to this  have been reduced a lot. :)

---

### Post by ageless on 2010-05-01
> **Herman said:**
> You have fixed it? :)

Just selected the correct drive for the bootloader during the installation. Thanks anyway.

---

