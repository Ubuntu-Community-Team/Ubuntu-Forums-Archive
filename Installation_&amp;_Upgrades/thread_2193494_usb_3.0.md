---
title: "usb 3.0"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by farshad_poor on 2013-12-13
Hi . I have MyPassport Exteranal Hard Disk and I can't use this in Ubuntu13.04

---

### Post by nerdtron on 2013-12-13
How do you say you can't use it in Ubuntu?

Plug it in and run "sudo fdisk -l" from the terminal and let's see if it is detected.

Or open the GUI Disk utility and see it the drive is there.

---

### Post by sudodus on 2013-12-13
Welcome to the Ubuntu Forums :-)

How do you want to use it?

Please try some commands from a terminal window (use the hotkey combination ***ctrl + alt + t*** )

```
lsusb
sudo fdisk -lu
sudo parted -l
ls -l /media

```
Copy and paste each command line into the terminal window and press the Enter key to run it.

Copy and paste the output text from each command into a 'reply editing window', 'go advanced', mark the text and click on the # icon just above the window to put it within code tags.

---

