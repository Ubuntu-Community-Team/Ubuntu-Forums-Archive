---
title: "Image 5.19.0.38 issue"
date: 2023-10-11
forum: Installation &amp; Upgrades
---

### Post by 20hharry19 on 2023-10-11
Hello, when I want to upgrade Ubuntu 22.04 I get the next message (in Dutch):
  	 	 	 	  [LEFT] linux-image-5.19.0-38-generic (5.19.0-38.39~22.04.1) wordt verwijderd ...[/LEFT] [LEFT] /etc/kernel/postrm.d/initramfs-tools:[/LEFT] [LEFT] update-initramfs: Deleting /boot/initrd.img-5.19.0-38-generic[/LEFT] [LEFT] /etc/kernel/postrm.d/zz-update-grub:[/LEFT] [LEFT] Sourcing file `/etc/default/grub'[/LEFT] [LEFT] /usr/sbin/grub-mkconfig: 1: /etc/default/grub: 0#: not found[/LEFT] [LEFT] run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127[/LEFT] [LEFT] dpkg: fout bij verwerken van pakket linux-image-5.19.0-38-generic (--remove):[/LEFT] [LEFT]  subproces van pakket linux-image-5.19.0-38-generic werd script post-removal geïnstalleerd gaf de foutwaarde 1 terug[/LEFT] [LEFT] dpkg: te veel fouten; er wordt gestopt[/LEFT] [LEFT] Fouten gevonden tijdens verwerken van:[/LEFT] [LEFT]  linux-image-5.19.0-38-generic[/LEFT] [LEFT] Verwerking werd afgebroken omdat er te veel fouten waren.[/LEFT] [LEFT] E: Sub-process /usr/bin/dpkg returned an error code (1)

I do need 5.19.0-38-generic when i want to install Image Scan! for Linux. how can I 'repair' it?

Thanx for your help!
[/LEFT]

---

### Post by #&amp;thj^% on 2023-10-11
I post this link with a warning: [https://linux.how2shout.com/how-to-install-linux-kernal-5-19-on-ubuntu-22-04-or-20-04/](https://linux.how2shout.com/how-to-install-linux-kernal-5-19-on-ubuntu-22-04-or-20-04/)
It's best to stay within the provided kernels on installation, and may cause issues or breakage. (Your Mileage may vary)

---

### Post by 20hharry19 on 2023-10-12
Thanks, 1fallen!

---

