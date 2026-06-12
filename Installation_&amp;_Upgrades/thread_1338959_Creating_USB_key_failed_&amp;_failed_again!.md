---
title: "Creating USB key failed &amp; failed again!"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Ragtop on 2009-11-27
I cannot begin to tell y'all (Yep, I'm a Texan) the level of my frustration after three days  of trying to create a Ubuntu thumb drive. 

I have downloaded and installed the program several times.  After installing, I could not FIND the program.  I read the  tutorial, went through the "how to" list, tried everything I could think of, but I was not able to find a way to start the program.  I finally found  it in the windows prefetch folder in my C:\ directory, but _still_ could not start it because it has a file  extension of ".pf"! These are the files: 
"LINUXLIVE USB CREATOR 2.1.EXE-354EC5E1.pf" & 
"LINUXLIVE USB CREATOR 2.1 - F-25D94E92.pf"

To say the least, my patience has been severely tested!   

I'm running Win2000Pro and using Mozilla Firefox as my browser.  My  desktop computer is a Dell XPS with three gigs of ram. 

Is there any help anyone can offer?  It would be greatly appreciated, to  say the least!!! 

Thank you 

BC

---

### Post by running_rabbit07 on 2009-11-27
I have never tried it, but I have heard you can use Unetbootin to make a bootable USB drive.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://lifehacker.com/5042630/unetbootin-creates-usb+bootable-linux-the-easy-way](http://lifehacker.com/5042630/unetbootin-creates-usb+bootable-linux-the-easy-way)
[http://en.wikipedia.org/wiki/UNetbootin#USB_Install_Mode](http://en.wikipedia.org/wiki/UNetbootin#USB_Install_Mode)
[http://www.linuxjournal.com/video/creating-bootable-usb-install-drives-unetbootin](http://www.linuxjournal.com/video/creating-bootable-usb-install-drives-unetbootin) this last link has a video clip on making the USB. 

I hope this helps/

---

### Post by PariahVayne on 2009-11-27
Unetbootin is pretty sucky. 

Try this in Terminal;

```
sudo bash
```

```
cd /home/yourusernamehere/folderwithisoin
```

```
dd if=nameofiso.iso of=/dev/sdb
```

---

### Post by PariahVayne on 2009-11-27
Ignore my last post >_<

---

### Post by Ragtop on 2009-11-27
Well, I guess I've made a little headway, but only got more frustration from it.  I found usb-creator "somewhere".  I guess I just couldn't see it 'til after my first post to the forum:mad:  Well, having found the little bugger, I put a shortcut on my desktop to eliminate the chance of losing it again.

NOW I'm building a collection of thumb drives that usb-creator doesn't recognise as suitable targets for the iso image file.  There's a brand-new, never formatted or used Sandisk 8GB "Cruzer, and a two and an eight GB Kingston Data Travelers.  I deleted the files and folders from the Kingstons and ran FORMAT F:\ from the Windows start menu.  So, FWIW, usb-creator sees them, identifies the drive and shows the capacity and free space, but the "Make startup disk" remains grayed out and non-functional.    That is after I clicked on the "Other" button below the top pane and entered the netbook remix iso.  

Oh well, as Handsome Ronnie Reagan might say, it's bedtime for Bonzo.  Too late and too tired to futz with it anymore tonight.

Thanks for the replies, and I deeply appreciate any further input.

BC

---

