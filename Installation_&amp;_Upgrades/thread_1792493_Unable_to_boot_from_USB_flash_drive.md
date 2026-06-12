---
title: "Unable to boot from USB flash drive"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by ktp.kti on 2011-06-28
I am trying to install ubuntu 11.04 from a bootable USB flash drive. As i couldnt create the USB using the inbuilt usb creator which came with the .iso file i had downloaded, i had used universal USB installer to create it. It took a lot of time to created the bootable pendrive. 

I had copied the contents of the pendrive thus created to a folder on my hard disk and named it 'PENDRIVE'. Later i had formatted the pendrive and used it for other purposes.

Today, i wanted to install ubuntu on another computer, so i copied the contents of this folder to my pendrive (instead of creating a bootable usb drive using universal USB installer again) and renamed my pendrive as 'PENDRIVE'. But when i tried to boot from it (i had changed the boot order of my computer accordingly) i got this message, 'remove any removable cd or media and press any button to restart'. Until i removed the pendrive my system refused to start and i was unable to install ubuntu. Why did this happen?

---

### Post by lightstream on 2011-06-28
because the USB drive needs to be made bootable. You can do this using cfdisk with the -b option on the command line.

An easier way would be to download [unetbootin]("http://unetbootin.sourceforge.net/") though.

---

### Post by ktp.kti on 2011-06-28
I used unetbootin and it worked! Thank you lightstream!

---

