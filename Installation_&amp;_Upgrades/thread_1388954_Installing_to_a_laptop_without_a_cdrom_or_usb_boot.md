---
title: "Installing to a laptop without a cdrom or usb boot options."
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by netddd on 2010-01-23
So, I have an old laptop that used to have windows/ubuntu until the drive got fubarred (no physical damage).  I shoved the laptop as side as I didn't use it much anymore (it's an old, loud 2.4GHz desktop p4 in a dell--mostly toshiba--laptop.  pcmcia atheros based wifi card and an ATI m6 graphics card.  Laptop was new back in 2002-03 maybe).  

The Cdrom drive had died a while back, and it's not worth buying a replacement.  The bios doesn't support boot to USB.  What are my options for getting Ubuntu on there (9.10 preferably)?  The drive has been formatted already, so there is nothing to boot into right now.  

I can pull the drive and hook it up to my desktop (windows 7 machine only right now) via USB, and partition it from there, but I'm not sure how to get the installer on there.  The MBR of the laptop drive will also have to be rewritten.  Is there a way I can create a dos partition, load it with files, and start a linux install that way (maybe with grub4dos or something)? 

Or can I somehow boot into an ISO image on a partition?   

The only other thought I have is creating a floppy disk that will allow a network boot, but I haven't looked into that.  

Any suggestions would be wonderful.

I basically just want something to bring with on vacation that I can get online with.  Browsing from the phone leaves a little bit to be desired.

Thanks for your help!


~Dominique

---

### Post by tachuela on 2010-01-23
If you can see your Notebook's HH when you boot a Live CD on your Desktop; then, you can install to it.

---

### Post by netddd on 2010-01-24
Yeah, I did try putting the laptop drive into the desktop, but it didn't display any drives on the partition screen, so that was out.  Would have been nice had it worked...

---

### Post by C.S.Cameron on 2010-01-24
Could you just swap hard drives with your desktop then install from the Live CD.
Or disable your desktop HDD and then install using the USB setup.
Or clone ubuntu to from a flash drive or HDD install using dd.

---

### Post by netddd on 2010-01-28
Thanks for the idea.  I tried installing to the laptop hard drive by booting to a cd in my desktop.  For whatever reason it wouldn't recognize the drive (I could have been using a bad adapter.  I didn't try it with my USB adapter, but instead a 44pin pata to 40pin pata + 4pin molex power).

So I took a leap of faith and installed in a VM, then pulled an image from the VM.  I then transfered the image to he laptop drive and viola, it worked.  Certainly not the best way, but it did work.  It wasn't stable if gnome (kept freezing up), but I dropped to a console via the ctrl-alt-F1 and ran aptitude update and added my wireless modules and old ATI drivers, and all the existing updates.  It is running just fine now.

Thanks for your help.

---

