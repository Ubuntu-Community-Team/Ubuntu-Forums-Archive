---
title: "URGENT! Error Trying To Install To External USB Device"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by Mr|C on 2007-05-14
I'm trying to install 6.10 to my external hard drive.

Here's the link - [http://www.amazon.co.uk/Western-Digital-Elements-250GB-External/dp/B000MES2UE/ref=pd_bbs_sr_3/026-7995223-8539653?ie=UTF8&s=electronics&qid=1179159397&sr=8-3](http://www.amazon.co.uk/Western-Digital-Elements-250GB-External/dp/B000MES2UE/ref=pd_bbs_sr_3/026-7995223-8539653?ie=UTF8&s=electronics&qid=1179159397&sr=8-3)

The error I get while trying to install is:
The ext3 file system creation in partition #1 of SCS15 (0,0,0) (Sdb) failed.

I'm installing Ubuntu on the whole of the HD and I'm installing grub to (hd1)
**_I just tried installing via my laptop, and it works. Is it possible to install via my laptop, and just use on my desktop?_**

Then, when I press ok, it closes down the whole install.

Help

---

### Post by Mr|C on 2007-05-14
Please?

---

### Post by Mr|C on 2007-05-14
Sorry to bump..again. Really do need help though <3

---

### Post by bulldog on 2007-05-14
Try the gparted live cd to format the external disk.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If formatting in ext3 won't succeed,try another file system just to see if you get errors too.

Installing on the laptop and using it with the desktop should be possible
You'll have to reconfigure your xorg.conf.

---

### Post by Mr|C on 2007-05-14
bulldog, I <3 you. You've helped me a lot recently. Anyway, I had dinner, and tried again. Seems to be installing properly right now. I've just got to hope that I installed GRUB to the correct HD xD

---

### Post by eentonig on 2007-05-14
Also, it's quite possible you'll have to reconfigure grub. 
1. Make sure GRUB is installed on the USB disk, and not on the Laptop HD.


And then, I installed Ubuntu on an external USB disk just fine. The only thing I had to keep in mind was to install grub to (if memory serves me well) hd1,0 (the USB disk as seen during install, being the second HD) and then after/during the reboot change grub to point to the first HD (as you are now booting from USB, this becomes your first HD).

Make sure your BIOS supports booting from USB Harddisks (it's not because your BIOS has an option USB, that it means USB HD)

---

### Post by Mr|C on 2007-05-14
Thanks. Everything seemed to install properly but now I cannot seem to get on to Ubuntu when booting from the USB drive. This is an example of what I get:
[http://img16.imagevenue.com/img.php?image=64507_IDIOT_122_634lo.JPG](http://img16.imagevenue.com/img.php?image=64507_IDIOT_122_634lo.JPG)

This stays like that and doesn't go away. Any ideas?

---

### Post by bulldog on 2007-05-14
Try the recovery mode option to see if that one will boot

---

### Post by Mr|C on 2007-05-14
First, I'm reinstalling. This time, instead of (hd1) for GRUB, I'm doing (hd1,0). Not sure if it will make a difference, but no harm in trying. 

If that doesn't work, can you tell me how to get in to the recovery mode option <3

---

### Post by eentonig on 2007-05-14
I think you're better off searching the forum for a how to I used when installing to an external USB HD.

This was a very easy to follow howto. And it will save you a lot off unneeded headaches. Unfortunatly, I don't have the link at hand. But I found it by searching for "install usb HD"

---

### Post by bulldog on 2007-05-14
Grub should be installed in MBR of the hdd,not in the root section!!
So use (hd1) in your choice.

To get in recovery consolo,just choose this option in your GRUB menu.
It's possible you have a not properly working kernel.
If you have the generic installed,try to install the i386 [single processor]

---

### Post by Mr|C on 2007-05-14
I don't get the GRUB menu :( 

I'll go for one last clean install. I'll catch you up in a bit.

---

### Post by Mr|C on 2007-05-14
Ok, now I'm almost certain GRUB is installed in the right place. Still, on boot from my external USB hard drive, I'm left with a blank screen with a flash white line at the top, which doesn't go. 

Please..please help :)

---

### Post by Mr|C on 2007-05-14
Bumpage

---

### Post by Mr|C on 2007-05-14
Another update.

By getting to that blank screen, I press Cntrl+ALT+Delete. It then boots again and gets me to the GRUB menu. However, the Ubuntu loading bar doesn't move what-so-ever. Nothing loads up. Any ideas?

---

