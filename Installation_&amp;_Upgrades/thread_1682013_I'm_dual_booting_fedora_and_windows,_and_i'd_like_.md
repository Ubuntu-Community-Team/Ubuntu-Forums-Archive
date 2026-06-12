---
title: "I'm dual booting fedora and windows, and i'd like to replace fedora with ubuntu..."
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Dixi1801 on 2011-02-05
but the DVD with the ISO wont boot up, nor will the USB drive, which i formatted and set to a bootable ubuntu state(or so i thought)

i've gone into bios and changed boot order and still nothing, just the grub installed by fedora appears.

any help welcome 

thanks in advanced!

---

### Post by mikewhatever on 2011-02-05
The obvious questions to ask are:
Did you burn the iso as image?
What program did you use to make a bootable usb?

With Fedora, you can just dd the iso, but it doesn't work with Ubuntu. You need to use Unetbootin or another program in Windows.
Kmandla has Ubuntu images you can dd.
[http://kmandla.wordpress.com/2010/10/11/ubuntu-10-10-desktop-i386-usb-image//](http://kmandla.wordpress.com/2010/10/11/ubuntu-10-10-desktop-i386-usb-image//)

---

### Post by Dixi1801 on 2011-02-05
> **mikewhatever said:**
> The obvious questions to ask are:
Did you burn the iso as image?
What program did you use to make a bootable usb?

With Fedora, you can just dd the iso, but it doesn't work with Ubuntu. You need to use Unetbootin or another program in Windows.
Kmandla has Ubuntu images you can dd.
[http://kmandla.wordpress.com/2010/10/11/ubuntu-10-10-desktop-i386-usb-image//](http://kmandla.wordpress.com/2010/10/11/ubuntu-10-10-desktop-i386-usb-image//)

I used pendrivelinux USB bootable something or other, and I don't know what dd means :(

I'll check the link and try unetbootin when I get in and report back!

Thanks again!

---

### Post by mikewhatever on 2011-02-05
The Universal usb installer from pendrivelinux.com should work with the regular Ubuntu iso, same as Unetbootin. DD is a command to write the iso to usb which works with the likes of Fedora, Mandriva and Suse, but for some reason, not with Ubuntu isos. I tought you may have used it with Fedora.

---

### Post by Dixi1801 on 2011-02-05
> **mikewhatever said:**
> The Universal usb installer from pendrivelinux.com should work with the regular Ubuntu iso, same as Unetbootin. DD is a command to write the iso to usb which works with the likes of Fedora, Mandriva and Suse, but for some reason, not with Ubuntu isos. I tought you may have used it with Fedora.

my fedora install was from a dvd, really easy too :)

putting ubuntu on USB stick with Unetbootin as i write this, will let you know how it goes :)

---

### Post by Dixi1801 on 2011-02-05
Still no luck, my computer says there isn't a bootable drive or something when i select removable :(

---

### Post by scarey9 on 2011-02-05
Did you run the MD5 after you downloaded the ISO to make sure it was not corrupted.  Are you having UNetbootin download the ISO and put it on the USB (distribution opton) or are you using the disk image option? I have not had much luck with the disk image option. You might also consider formating the USB drive completely b4 running it thru UNetbootin.

---

### Post by Dixi1801 on 2011-02-05
> **scarey9 said:**
> Did you run the MD5 after you downloaded the ISO to make sure it was not corrupted.  Are you having UNetbootin download the ISO and put it on the USB (distribution opton) or are you using the disk image option? I have not had much luck with the disk image option. You might also consider formating the USB drive completely b4 running it thru UNetbootin.

I'm unsure what MD5 is, but i downloaded the ISO from the ubuntu website, and i've tried the diskimage option, im not sure about the other one, there's a fair few options, like 10.10 live(i know it isnt this option) and a few others.

would using gparted to format the current fedora partition help at all?

---

### Post by scarey9 on 2011-02-05
i dont think partitioning your Fedora Partition would help at all. MD5 just a way of checking the integrity of your downloaded file against the original file. If even one bit is changed from the original the Hash(checksum) will be different. The last install that i did on my Panasonic Tougbook was with a live CD. I liked that option. I have also done it with a Live USB.

---

### Post by mikewhatever on 2011-02-05
Odd indeed. Double check the bios is set to boot from usb.

---

### Post by Dixi1801 on 2011-02-05
I've fixed my problem, i just reburned ubuntu to a fresh dvd(the old one was a little scratched) and installed from there!

glad to be back on ubuntu :D

thanks for all your help guys!

-Dixi

---

