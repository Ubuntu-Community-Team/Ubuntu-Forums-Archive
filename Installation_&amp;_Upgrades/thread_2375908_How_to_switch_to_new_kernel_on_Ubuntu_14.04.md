---
title: "How to switch to new kernel on Ubuntu 14.04"
date: 2017-10-28
forum: Installation &amp; Upgrades
---

### Post by mossley74 on 2017-10-28
[SIZE=2][FONT=arial]Hi, 

I'm running 14.04, the current kernel returned by uname -r  --> [/FONT][/SIZE][SIZE=2][FONT=arial][/FONT][/SIZE][SIZE=2][FONT=arial]2.6.32-48-pve

I have installed the following kernel 

Output of --> dpkg -l | grep linux-image

[/FONT][/SIZE][SIZE=2][FONT=arial][/FONT][/SIZE]
[SIZE=2][FONT=arial]i  **linux-image**-3.13.0-133-generic       3.13.0-133.182                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP[/FONT][/SIZE]
[SIZE=2][FONT=arial]ii  **linux-image**-extra-3.13.0-133-generic 3.13.0-133.182                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP[/FONT][/SIZE]
[SIZE=2][FONT=arial][/FONT][/SIZE]
[SIZE=2][FONT=arial]ii  **linux-image**[/FONT][/SIZE][SIZE=2][FONT=arial]-generic                  3.13.0.133.142                       amd64        Generic Linux kernel image

How do I switch to the new kernel? There is no /boot/grub/grub.cfg file
There is however /etc/default/grub file

Thanks


[/FONT][/SIZE]

---

