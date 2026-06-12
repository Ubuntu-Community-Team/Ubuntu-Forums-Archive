---
title: "Huge problem with grub/Ubuntu 10.04"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by bareil76 on 2010-06-13
Ok.. I wasted 6 hours on getting ubuntu to work and I have done lots of thing.. but now I need HELP!!!!

Here is what I have done!
0) I have a dual core intel processor with IDE hard drive and IDE cdrom
The motherboard only has a single slot for ide drive. Hard drive is master (set with jumpers) and the other is slave.

1) XP 64 installed in C: partition (it is named differently in linux but I will come back to that)
2) ubuntu installed in D: partition with 58Gb and 2.3 Gb for memory
I wasn't able to boot from CDrom, I would get to an (initramfs) console. It would say :'' unable to find a medium containing a live system file
3) I then made a usb key and installed ubuntu 10.04lts easily.
4) BANG cannot boot into ubuntu... only windows with no grub loading!
5) Made a Gparted live cd but the cdrom would not boot... this cd works on another computer though
6) Then I want to use the usb key to use the "try ubuntu"  option BUT.... I then get to grub  whereI have the same choice to boot XP or ubuntu.. ubuntu gives me the same error.
7) I rebuild the usb key and can now boot into ubuntu live
8) I reinstall grub. I found out that my hard drive was called:  sdb and NOT sda
9) I update the initrd.img file and it didn't work either.
10) Then I re-reinstall the grub loader from a more direct way and it didn't work, so I tried to boot into the usb key again but got to a (initramfs) error again... I type EXIT and TADA!!!!

THe grub loader booted fine and I was able to get to ubuntu!  but I need to do that every time!!!

11) I tried to read the cdrom but it wasnt mounted. In fact, ubuntu didn't even detect the cd-rom... so I thoug the the error came from there.
12) I remove the cd-rom connection from the pc and booted right into ubuntu the first try... no "exit", no USB key. AND... the hard drive is named sda NOT sdb anymore!!!!!!

The question is... what the heck is happening???????????

PS. I have no problem booting in windows.

---

### Post by garvinrick4 on 2010-06-13
You need a hardware guy. Ubuntu is on sda because that is all you have is one drive.
What your Optical drive is doing seems to be the case. I do believe there is a hardware section in these Forums where those guys like to hang out. Good luck and stick with it.

---

### Post by bareil76 on 2010-06-14
Ok.. thank you, i will copy my post there!

---

