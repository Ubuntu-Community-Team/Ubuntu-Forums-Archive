---
title: "Installing Ubuntu 10.04 LTS on Pavilion dv1000"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by raphytaffy on 2010-06-29
Hi all, I'm trying to install Ubuntu on my dv1000 but I can't seem to get past the Ubuntu loading logo. I'm using the same CD that I used when I installed onto my Dell Inspiron 600m and that installation went flawlessly.

Right after the Ubuntu loading logo, my screen just goes black and sits there seemingly doing nothing. Does anyone know of compatibility issues with my laptop or is there a workaround to this black screen issue?

---

### Post by davidmohammed on 2010-06-29
probably a graphics issue.  The resolution depends upon the graphics card you've got.

suggest do an experiment

when booting (after your bios screen) press shift to display your grub.  Press e.  On the  line with quiet splash add one of the following BEFORE quiet splash

i915.modeset=1
i915.modeset=0
nomodeset

e.g.

... i915.modeset=1 quiet splash --

then press CTRL + X to boot.

---

### Post by raphytaffy on 2010-06-29
Tried pressing shift at every stage of the install. I'll take you through what I see when I boot up:

Screen with Ubuntu and options
Try without installing
Install Ubuntu
Check disc for defects
Test memory
Boot from first hard disk

F1 Help F2 Language F3 Keymap F4 Modes F5 Accessibility F6 Other Options

Pressing enter on Install Ubuntu gives me the Ubuntu logo with five dots underneath it (turns progessively red to indicate loading) and then black screen.

---

### Post by davidmohammed on 2010-06-29
ok - thought you managed to install.

Press F6 - at the bottom of the screen you will see a line of characters that at first looks like gibberish!  in there you'll see "quiet splash".

Add what I suggested immediately before quiet splash before continuing with "try without installing"

---

### Post by raphytaffy on 2010-06-29
That was such a simple fix.. +1000 internets to you, good sir!

Edit: Hmm, after the install I had to go into grub and edit the command line as instructed for it to display properly again. These settings are lost when I restart though, so how do I go about making it permanent?

---

### Post by davidmohammed on 2010-06-30
Edit the /etc/default/grub file (sudo nano /etc/default/grub) and add the kernel parameter you need to boot to the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line, then run:


sudo update-grub

---

### Post by raphytaffy on 2010-06-30
Done and done! Thanks again!

---

### Post by d.michalakos on 2010-08-03
I used the the i915.modeset=1 trick and managed to install Ubuntu 10.04.

Now that the OS is installed, I cannot log into it. I get the same black screen again and again.

If I can't log into the system how can I edit the grub?

Btw I tried pressing ESC on system startup but I do not see a GRUB dialog. Neither do I see a countdown message.

Plz help.

---

### Post by d.michalakos on 2010-08-03
Please ignore my previous message. It seems that I should press the shilf key repeatedly to see the grub menu.

---

