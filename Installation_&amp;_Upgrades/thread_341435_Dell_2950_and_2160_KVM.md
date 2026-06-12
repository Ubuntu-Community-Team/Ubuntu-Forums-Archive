---
title: "Dell 2950 and 2160 KVM"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by hogman23 on 2007-01-18
I recently installed 6.10 (Edgy) on a Dell Poweredge 2950 hooked up through a Dell 2160as usb KVM.  As soon as the installer started, the screen would go blank.  In desperation, I finally plugged the monitor and usb KVM cables in the front of the machine and everything worked perfectly.  I finished the install, moved the cables back to the back of the server and rebooted, and everything works perfectly.  I'm not sure if this is a resolution issue or what, but here is the solution if you are having the same problem.

Also,
if you want your resolution better than 800x600, you can edit the /boot/grub/menu.1st file:

add vga=791 to the end of these lines just like this: (note: do not remove the # sign in front of the defoptions line)

# defoptions=quiet splash vga=791
**then to your kernel line:**
kernel          /boot/vmlinuz-2.6.17-10-server root=/dev/sda2 ro quiet splash vga=791

---

