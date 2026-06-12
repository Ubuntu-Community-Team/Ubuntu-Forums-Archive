---
title: "Dual-Boot Issues after Windows Upgrade"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by Kchymet on 2011-02-06
So I decided to switch from Vista to Windows 7. Before, with Vista, I would boot then select either my Ubuntu 10.10 installation or Vista (loader) from the grub menu, but now that I've upgraded to 7, the grub menu no longer appears and I'm just led into Windows. This i obviously a problem. I've read some other posts, but they all want me to boot from an Ubuntu install disk then use the "sudo grub" command, for which I receive a "command not found" error. When I was attempting this I ran "sudo fdisk -l" and found that Ubuntu 10.10 was on /dev/sda5, Win7 was on /dev/sda1, and my swap partition was on /dev/sda3. I just don't know what to do at this point lol.

---

### Post by wilee-nilee on 2011-02-06
> **Kchymet said:**
> So I decided to switch from Vista to Windows 7. Before, with Vista, I would boot then select either my Ubuntu 10.10 installation or Vista (loader) from the grub menu, but now that I've upgraded to 7, the grub menu no longer appears and I'm just led into Windows. This i obviously a problem. I've read some other posts, but they all want me to boot from an Ubuntu install disk then use the "sudo grub" command, for which I receive a "command not found" error. When I was attempting this I ran "sudo fdisk -l" and found that Ubuntu 10.10 was on /dev/sda5, Win7 was on /dev/sda1, and my swap partition was on /dev/sda3. I just don't know what to do at this point lol.

So since you have run the sudo fdisk command here is the link you need. You will run the fdisk again to confirm the information then run the next two commands and reboot to the grub menu.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you want the actual commands posted just ask, after providing the actual readout of the fdisk command.:)

---

### Post by Kchymet on 2011-02-06
Thanks, I figured it out.

---

