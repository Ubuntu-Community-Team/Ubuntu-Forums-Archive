---
title: "live cd wont boot"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by matthewric on 2007-12-06
hello i have a problem where the live cd wont boot i know the cd is find because i installed if on my laptop off the same cd a while ago i thought it was because i was using svideo out but it wont even boot with a monitor the ubuntu bar goes up for a while then it stops and the screen kinda distorts oh it does exactly the same thing in safe graphics mode

---

### Post by jasmuz on 2007-12-06
Did you check the live cd is burned properly?

---

### Post by Pumalite on 2007-12-06
> **matthewric said:**
> hello i have a problem where the live cd wont boot i know the cd is find because i installed if on my laptop off the same cd a while ago i thought it was because i was using svideo out but it wont even boot with a monitor the ubuntu bar goes up for a while then it stops and the screen kinda distorts oh it does exactly the same thing in safe graphics mode

Try the Alternate CD.

---

### Post by matthewric on 2007-12-06
i know the live cd is burned properly because it installed fine on my laptop i also tryed the alternate cd which did the blue screen text based install it installed ok but does exactly the same thing when booting it just stops and hangs with a distorted ubuntu loading bar screen

---

### Post by JangMunho on 2007-12-06
> **matthewric said:**
> i know the live cd is burned properly because it installed fine on my laptop i also tryed the alternate cd which did the blue screen text based install it installed ok but does exactly the same thing when booting it just stops and hangs with a distorted ubuntu loading bar screen

Try Ctrl+Alt+F2 to login through tty2, if you can do so, you should try to install ubuntu with a display with DVI or VGA, and then install the official video card driver...

---

### Post by matthewric on 2007-12-06
when do i press the keys

---

### Post by Pumalite on 2007-12-06
If you finished your Alternate CD installation; you can do this:
Ctrl+Alt+F1 to get command line
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
At the end: startx

---

### Post by matthewric on 2007-12-11
i tryed thant and it  did the same thing

---

### Post by pizzipie on 2007-12-11
I may have a related problem??

Latitude D800 with Nvidea 5000? 

I am trying to do a "clean" install with Gutsy 7.10. I now have  7.04. I'm trying to go in little steps so I don't screw up everything. I have done the following so far. 1. Downloaded the 7.10 iso file. Checked it with md5sum - OK.
2. Burned  the iso file to CD. Verified writing  is OK. 3. Booted with the Live CD 
Now is the problem! I don't know whether it booted or not. The screen is black with rows of white dashes over the complete screen. Nothing else happens. I can't even "ctrl-alt-delete" out of it. 4. Removed battery and rebooted Feisty OK. 
Is this a video driver problem? If so what can I do to make this work???

Thanks in advance.

RP

---

### Post by Pumalite on 2007-12-11
> **Pumalite said:**
> If you finished your Alternate CD installation; you can do this:
Ctrl+Alt+F1 to get command line
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
At the end: startx
Start checking your hardware, cables, connections, settings in BIOS, etc.

---

### Post by Pumalite on 2007-12-11
You might also want to try some boot parameters. Her is a guide and a collection of them:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

