---
title: "The right thumbdrive for Ubuntu on USB"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2009-12-05
Just wanted to share an experience I had yesterday buying a thumb drive intended for a portable "Ubuntu-on-USB" installation.

I made the mistake of picking up a Sandisk Cruzer.  It has an annoying application at the root of the drive called U3.  U3 is an unnecessary geegaw designed to impress Windows users.  In Linux it's a real annoyance.  I tried formatting the drive with a GPartedLiveCD.  GParted didn't see the U3 folder.  It just saw a big old fat32 partition.  I tried deleting the three files in the U3 folder but they wouldn't go away.

I was able to install Ubuntu on the Cruzer.  But at the BIOS "quick-boot" menu the Cruzer was seen as two USB devices, not one.  If I picked the wrong one, BIOS would look at U3, skip past it, and boot from the default device.

Took the Cruzer back to the store and exchanged it for a PNY Micro-Attache, which has no applications installed and is seen as one device.

So the lesson is: pick a basic no-frills thumb drive that doesn't have any cutesy applications pre-installed.

---

### Post by howefield on 2009-12-05
You can remove the U3 software from the thumb drive turning into a normal flash drive.

---

### Post by darkod on 2009-12-05
Yeah, U3 is real hassle. It can be removed under windows with an uninstall app but if you have no windows machine I guess it can be tough. Not sure if there is removal app for linux, never needed to look for it.
I guess you don't need the link for the windows uninstall app right? You exchanged the stick already.

---

### Post by Bartender on 2009-12-05
Yeah, I did replace it.  I haven't done anything with the PNY yet except to verify that it's just a generic storage device with nothing on it.

Makes sense that there's a way to strip U3 off the drive.  I guess I shoulda googled instead of taking it back but what's done is done...

I have a Windows machine but stuck with dial-up at home, which sort of skews the way I do things :(

---

### Post by cybrsaylr on 2009-12-05
FWIW, I just bought an 8GB Sandisk Cruzer and just ignored that U3 app and all seemed OK. U3 and the flash drive icon shows up on my Ubuntu desktop when it's plugged in and while annoying sitting there has caused no problems. I installed Ubuntu 9.10 on the Sandisk Cruzer with no problem, took about 6 minutes used up 1.2GB of space and when I tested it, Ubuntu seems to run off it with no problem.

Decided to keep U3 because I dual boot with Windows 7 and may use that app in the future with M$.

---

### Post by phillw on 2009-12-05
Then again, you always get a REAL COOL one from here --->  [http://shop.canonical.com/product_info.php?products_id=577](http://shop.canonical.com/product_info.php?products_id=577)

Has 9.10 already on it, cute :p

Phill.

---

### Post by darkod on 2009-12-05
> **Bartender said:**
> Yeah, I did replace it.  I haven't done anything with the PNY yet except to verify that it's just a generic storage device with nothing on it.

Makes sense that there's a way to strip U3 off the drive.  I guess I shoulda googled instead of taking it back but what's done is done...

I have a Windows machine but stuck with dial-up at home, which sort of skews the way I do things :(

You could have downloaded the uninstall app on a linux machine with faster internet, then use the stick itself to take it to the windows machine and kill U3. Did I say how easy it is removing U3? :P

---

