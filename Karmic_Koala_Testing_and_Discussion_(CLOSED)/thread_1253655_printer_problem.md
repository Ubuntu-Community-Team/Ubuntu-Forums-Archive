---
title: "printer problem"
date: 2009-08-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-08-30
okay ya'll having prioblem with getting my hp printer to work. any advise. need to get working by 9/1/09 when my daughter goes back to school

---

### Post by psyke83 on 2009-08-30
Searching the forum before posting is always a good idea.

[http://ubuntuforums.org/showthread.php?t=1252452](http://ubuntuforums.org/showthread.php?t=1252452)

---

### Post by garvinrick4 on 2009-08-30
I have fix for USB printer not being recognized. Post more info please.

---

### Post by lswb on 2009-08-30
Most HP printers work very will with ubuntu or any modern linux distribution. Please describe the problem in more detail.

---

### Post by maestrobwh1 on 2009-08-30
No and my printer has worked since Ubuntu 6.10!

Cups via browser does not even find the printer. Again, it was ALWAYS listed.

If I use package "printconf" (python) then it finds it in the terminal and then it shows up as

pagepro_1350w KONICA MINOLTA PP1350W USB Printer #1 Minolta PagePro 1350W Foomatic/min12xxw (recommended)

Description: KONICA MINOLTA PP1350W
Location: USB Printer #1
Driver: Minolta PagePro 1350W Foomatic/min12xxw (recommended) (grayscale)
Connection: usb:/dev/usb/lp0
Defaults: job-sheets=none, none media=na_letter_8.5x11in

However, it does not print. It works in jaunty, knoppix 6.01, arch linux with the same driver min12xxw

---

### Post by garvinrick4 on 2009-08-30
terminal Type: lsusb   (will see dev #'s and bus #'s for computer)

sudo rmmod usblp    
sudo aa-complain cupsd
sudo chgrp lp /dev/bus/usb/3 digit bus #/3 digit device #
sudo chmod 664 /dev/bus/usb/3digit bus#/3 digit device #

Go to graphic interface to add printer manually   System>Administration>Printing> Click New
                                                                                                                or CTRL +N
System will then find USB device and driver if necassary.


Linux instructions  Ubuntu 9.10 Karmic Koala Alpha 4

---

### Post by rburkartjo on 2009-08-30
after last update printer is now working tks

---

### Post by VMC on 2009-08-30
I have a Hewlett-Packard DeskJet 895c on a USB port. Works fine.
I had problems in previous Ubuntu releases, but so far not karmic. CUPS is being updated often. I use to have to alter the DEVICE URI. Right now I'm using "hp:/usb/DeskJet_895C?serial=CN99F1N0J3GG"

Edit: I just noticed that the posters printer now works.

---

