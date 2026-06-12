---
title: "Ubuntu 15.04 freezes on shutdown / restart"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by nikhilbhalwankar on 2015-05-09
Hi,

I am facing issues related to shutdown / restart on Ubuntu 15.04 32 Bit edition. The laptop freezses on shutdown / restart. The installation process went smooth, without any issues. Even updates got installed successfully after the installation but issue with shutdown / restart. Below alternatives too does not work..

[B]sudo poweroff
sudo shutdown -h now
[/B]

Ultimately, I went back to 14.04 Trusty Tahr. Its running damn smooth on my 8 years old laptop. Laptop is Lenovo 3000G Series. Please let me know how can I resolve this issue. I want to use 15.04.


[B]--
Many Thanks,
Nikhil Bhalwankar[/B]

---

### Post by dino99 on 2015-05-10
logs might help to identify that issue; but the easier way might be to remove 'quiet splash' from the /etc/default/grub file, then running > sudo update-grub
that way you can see where the freeze is happening (be sure that /etc/fstab is not trying to read a cdrom for example)

---

### Post by nikhilbhalwankar on 2015-05-11
Thanks. I will try this out.

---

### Post by Mike_Roncone on 2015-07-27
Just to tack on here, I recently fixed a similar problem myself. I am using an MSI GS60 Ghost 2PC and whenever I tried to reboot/shutdown the computer would either freeze entirely, or all of the windows/apps would shut down and I would be staring at just the background image into perpetuity. 

From another user on another forum, I got the idea that it may be my graphics driver messing up the process. Sure enough, after going into "Software & Updates" -> "Additional Drivers" and choosing one for my graphics card from NVIDIA itself with the (proprietary, tested) tag next to it, the issue is gone. give that a look.

---

### Post by Bert_Stanton on 2015-10-07
> **Mike_Roncone said:**
> Just to tack on here, I recently fixed a similar problem myself. I am using an MSI GS60 Ghost 2PC and whenever I tried to reboot/shutdown the computer would either freeze entirely, or all of the windows/apps would shut down and I would be staring at just the background image into perpetuity. 

From another user on another forum, I got the idea that it may be my graphics driver messing up the process. Sure enough, after going into "Software & Updates" -> "Additional Drivers" and choosing one for my graphics card from NVIDIA itself with the (proprietary, tested) tag next to it, the issue is gone. give that a look.

Just wanted to say this worked for me. I'm using a Gigabyte P35, and had to set the driver to "version 340.93 from nvida-340 (proprietary)". That did the trick. 

Thank you!

---

