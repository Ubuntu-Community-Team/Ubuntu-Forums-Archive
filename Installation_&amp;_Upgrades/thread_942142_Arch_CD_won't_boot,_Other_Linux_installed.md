---
title: "Arch CD won't boot, Other Linux installed"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by Mr.Macdonald on 2008-10-08
I currently have Ubuntu installed and after reading I feel that I could use some fast Linux. So I downloaded an ISO and checked its md5sum. I wrote it to disk using Ubuntu's "right click on ISO and click write to disk" utility to write the ISO to the disk. Now I tried to boot it and it failed.

My system is the Via Artigo with an external (usb) LaCie CD/DVD drive. I pressed ESC and F12 upon boot to select the bootable media. On  the list there was CD-ROM and USB-CD-ROM. each time I choose either one the system starts booting the hard drive without and recognition of the CD.

Do i need to make the CD bootable "chmod +boot /dev/cdrom"

Now I won't do anything drastic but what if I deleted my /boot directory, would that force the system to boot the CD

---

### Post by Partyboi2 on 2008-10-08
> Now I won't do anything drastic but what if I deleted my /boot directory, would that force the system to boot the CDI would say no, because the cd should have booted before ubuntu kicks in. Make sure that you burnt the iso as a iso not as a data file.

---

### Post by Mr.Macdonald on 2008-10-08
My Ubuntu Live Disk will boot, and the Arch disk boots on another computer.

The disconcerting thing is that the system doesn't seem to even try the disk

---

### Post by Partyboi2 on 2008-10-08
Maybe another option you can try is [[COLOR=Blue]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/") to install arch. Unetbootin does not require the use of a cdrom

---

