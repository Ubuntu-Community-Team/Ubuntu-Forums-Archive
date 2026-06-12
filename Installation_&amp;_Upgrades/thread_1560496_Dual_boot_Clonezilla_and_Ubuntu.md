---
title: "Dual boot Clonezilla and Ubuntu"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by GaretJax on 2010-08-24
I recently used Clonezilla for the first time and through my experience it would seem that one could not install Clonezilla in Ubuntu. I had to install it on a freshly formatted USB drive and boot my computer from it to use it.

I am fine with that, but I would like to know how I can put Ubuntu and Clonezilla on the same USB drive and so that when I boot from this USB drive, it would give me a menu option to run one or the other.

My idea here is to create a tool for use in my computer administrative duties and so when I need to troubleshoot a computer, I would like to be able to run Ubuntu or Clonezilla on a computer.  And if there are other applications that would assist me in these tasks, I would like to be able to add them to this same USB drive in the future.

Should I simply create seperate partitions for Ubuntu and Clonezilla, and use grub to give me the boot menu?  Or is there a way to combine both of these items into one partition?

---

### Post by quixote on 2010-08-25
I'm almost 100% sure you can't combine them.  Partitioning SD cards and the like (eg USB thumbdrives) is not like partitioning a hard drive.  The process is the same (eg use gparted or fdisk), but the result is much iffier.  I tried partitioning one a couple of years ago, and after a while all I accomplished was 3GB of corrupted memory.  Unless the robustness of the media when partitioned is much improved (which it may well be), I'd worry.  If you want to try it anyway, yes, you just partition, install them, and use grub to sort them out.

My suggestion would be to carry two different thumbdrives. :D

---

### Post by GaretJax on 2010-08-30
Hmm.  Carrying around multiple USB drives gives me the image of a janitor's keyring. LOL.  I think I will try the partition method and see how far I get.  Thanks for you help.

---

### Post by Mark Phelps on 2010-08-31
Don't know about a USB drive, but I do know you can do that with a hard drive because my system is configured that way.

Go to the Clonezilla website, look through the FAQs, and look for one describing how to install the ISO to a hard drive.  It involves saving the ISO file and adding an entry to the appropriate GRUB config file.  Steps should work much the same with your USB stick.

---

### Post by stlsaint on 2010-08-31
> My idea here is to create a tool for use in my computer administrative duties and so when I need to troubleshoot a computer, I would like to be able to run Ubuntu or Clonezilla on a computer. And if there are other applications that would assist me in these tasks, I would like to be able to add them to this same USB drive in the future.


This is the start of what you are looking for. [MultibootUSB]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/")

The multibootiso link uses a program to put the iso's to the hdd for you. But you can also create your own using your own menu.lst config from scratch using some iso's that the pendrive linux setup does not offer! (IE: Trinity Rescue Kit) Do a google search for Hak5 multipass usb to learn to do from scratch!

I did a mixture of using the program and merging my config that i made from scratch and im very happy with the results! I have knoppix, trinity rescue kit, DSL, puppy, ubuntu livecd, kubuntu livecd, Hirens boot disc and many more on a 8GB usb drive. :popcorn:

---

### Post by GaretJax on 2010-09-11
> **stlsaint said:**
> This is the start of what you are looking for. [MultibootUSB]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/") ...
Wow. That looks promising. I will look into this now and post my experience. Thank you.

---

