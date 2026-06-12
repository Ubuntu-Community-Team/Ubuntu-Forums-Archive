---
title: "Error installing on server without graphics card - no suitable video mode found"
date: 2018-09-20
forum: Installation &amp; Upgrades
---

### Post by rwfbc on 2018-09-20
Hello,

I am trying to install Ubuntu Server 16.04 on a single-board computer with no graphics card / chipset. After selecting "Install Ubuntu" from the menu, I get the following error:

[B]error: no suitable video mode found.
Booting in blind mode
[/B]
After this the install process just hangs.

I tried to edit the boot command, but I am not sure what to specify. I saw the "text" option, but it did not help. I also tried vga=ask, which did _not_ prompt for the mode.

I am installing from a bootable USB stick. I have used it before to install successfully (on a server with a graphics card).

I am connected using a USB Serial link, using [FONT=courier new]screen[/FONT] on a Mac.

Any suggestions?

Thanks...

Roger

---

### Post by TheFu on 2018-09-21
Use the alternate release ISO and a serial connector.
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto) (old)

[https://askubuntu.com/questions/769756/ubuntu-server-usb-installation-with-installers-output-on-ttys0-serial-port](https://askubuntu.com/questions/769756/ubuntu-server-usb-installation-with-installers-output-on-ttys0-serial-port) is probably more helpful.

---

### Post by rwfbc on 2018-10-03
The solution was to add "[COLOR=#091E42][FONT=monospace]console=ttyS0,115200n8[/FONT][/COLOR]" to the boot command.

When the boot menu comes up, select "[COLOR=#091E42][FONT=-apple-system]Install Ubuntu Server[/FONT][/COLOR]" and type "e" to enter the editor. Add the above to the boot command, so that it looks something like this:

[COLOR=#091E42][FONT=monospace]    linux  /install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet [/FONT][/COLOR]**console=ttyS0,115200n8**[COLOR=#091E42][FONT=monospace] ---[/FONT][/COLOR]

Then type ctrl-x to exit the editor and boot.

Roger

---

### Post by TheFu on 2018-10-03
Please mark the thread "SOLVED" using the thread tools button near the top of the pg.
And thanks for posting the solution. Both of these things help the community.

---

