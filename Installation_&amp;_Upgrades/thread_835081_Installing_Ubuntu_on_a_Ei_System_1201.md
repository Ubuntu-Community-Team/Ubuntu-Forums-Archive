---
title: "Installing Ubuntu on a Ei System 1201"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by The Browncoat Cat on 2008-06-20
I am trying to install Ubuntu Linux on an Ei System 1201 laptop.  If I try to install straight from the Live CD he Installer freezes as soon it enters graphical mode.  If however, I hit F6 and append the commands ```
"acpi=off noapic nolapic edd=on"
```to the boot command line then the Installer runs, sets up Ubuntu on the laptop, but there is still a problem.  Any subsequent attempt to boot into Ubuntu freezes the machine as soon as it hits graphical mode, just like wen the Installer froze before I appended the above commands to the Boot Command Line. Booting in Recovery Mode also freezes.

---

### Post by ercork on 2008-07-01
If you managed to complete the installation then it should be possible to get it to load. Try booting up the computer without the cd in the drive. After the computer's bios screen is displayed the grub bootloader comes up and asks you to choose between ubuntu and any other OS that you might have installed (e.g. win XP). It usually defaults to ubuntu after 9 seconds (I think).

Before the 9 second countdown finishes type 'e' (edit). Then press 'o' (new line) and 'e' again (edit). I may have the exact sequence wrong here but it tells you the correct ones at the bottom of the screen. Then type in the same command you entered in while booting the live cd.

Hopefully ubuntu boots up now. If so you can edit grub so that the same command is passed every time you boot. In a terminal type

sudo gedit /boot/grub/menu.lst

Add the command to the file that opens up, save it and exit. Hopefully your next boot will be problem-free.

---

### Post by gallifreyangirl on 2008-07-05
Have managed to finally install this on my mums laptop with the help of the instrcutions above and using this website to edit grub and permentlety change the boot loader. [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html") Have not managed to get wifi working howver have got usb wifi dongle which works perfectly fine.

---

### Post by ercork on 2008-07-12
For your wireless have you tried ndisgtk? It's for using the windows wireless drivers in linux. Install it through Synaptic and then open it up through System/Administration/Windows Wireless Drivers

---

