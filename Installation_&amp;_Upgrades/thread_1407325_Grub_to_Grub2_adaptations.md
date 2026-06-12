---
title: "Grub to Grub2 adaptations"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by zeltus on 2010-02-15
Hi

I'm trying to breathe new life into a Dell Inspiron 5000 laptop. The fact it has no network connectivity is not helping!

Anyways, I have found the following instruction in Linux for Laptops

1. ACPI is not supported, you need to use APM. In order to do so, Edit "/etc/modules/" and add the following line: 'apm'.
 
2. Also, edit "/boot/grub/menu.list" and add the following to your "kernel" option: 'acpi=off apm=on' 

4. Edit "/boot/grub/menu.list" and add the following to your "kernel" option: 'vga=791' 

Can someone kindly tell me how these translate into modern Grub2 usage? This for a 9.10 release.

Cheers

Bill

---

### Post by darkod on 2010-02-15
I think the kernel options are added in /etc/default/grub now. Look here for Grub2 basics, especially in section 5. The line in /etc/default/grub is:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

You just continue writing the kernel options after splash, inside the quotes and of course with space between each. Save and close the file.

You need to run:
sudo update-grub

after you're done with the changes.

PS. Sorry, the link for grub2 basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

