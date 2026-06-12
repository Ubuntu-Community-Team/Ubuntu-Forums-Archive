---
title: "Tryingto install 11.04. Failed to boot from USB."
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by Brian121 on 2011-08-06
I downloaded the 32-bit iso from the Ubuntu website. I followed all of the instruction given on [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download). I went into my BIOS settings and set it to boot from the USB. A black screen came up and first showed me a line of copyright information. On the next line it said "Boot failed: please change disks and press a key to continue". Then on the third line it repeated the same thing "Boot failed: please change disks and press a key to continue".

I don't know if any information about my computer is needed or not, but I'm using a Dell Latitude D610 laptop with Windows XP Media Center Edition Version 2002 Service Pack 2. The USB I'm using is eight gigabytes, was manufactured by Toshiba, and has absolutely nothing on it except for the stuff that needs to be on there to install Ubuntu.

Thanks in advance!
-Brian

---

### Post by jerrrys on 2011-08-06
boot with your laptop set to boot from usb, but without the usb inserted.  do you get the same error message?

---

### Post by Brian121 on 2011-08-06
> **jerrrys said:**
> boot with your laptop set to boot from usb, but without the usb inserted.  do you get the same error message?
No. It just boots Windows XP.

By the way, I just had a thought. When I used the Universal USB Installer there was an option to set something called "persistence". The instructions on ubuntu.com didn't say anything about persistence so I just left it set at "No persistence". What is persistence and would it have anything to do with why I can't boot Ubuntu from my USB?

---

### Post by jerrrys on 2011-08-06
no, the persistence option allows you to save settings.  without it, you start fresh (default) every time you restart.

---

### Post by jerrrys on 2011-08-06
how much ram do you have?

---

### Post by Brian121 on 2011-08-06
> **jerrrys said:**
> how much ram do you have?
I have one gigabyte of RAM on this laptop.

---

### Post by maxar6 on 2011-08-06
Try using a CD since USB boot is kind of new and still beta on most laptops.

---

### Post by jerrrys on 2011-08-06
EDIT:  didn't see your last post.  yes cd is best way to go

---

### Post by Brian121 on 2011-08-06
I guess I'll have to go out and buy a black CD then lol. I was hoping to be able to try this out tonight. Is there any way it can be done with a blank DVD instead of a CD? I have a bunch of blank DVDs but no CDs.

---

### Post by Hakunka-Matata on 2011-08-06
You might want to try reloading your USB using unetbootin.  It has worked better than other USB creator tools for me and many others.
see link in my signature

---

