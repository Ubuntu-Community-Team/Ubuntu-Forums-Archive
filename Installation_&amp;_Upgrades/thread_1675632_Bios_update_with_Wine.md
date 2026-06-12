---
title: "Bios update with Wine??"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by Dsky on 2011-01-25
I would update the bios of my asus with his utility

[http://support.asus.com/technicaldocuments/technicaldocuments_content.aspx?no=714](http://support.asus.com/technicaldocuments/technicaldocuments_content.aspx?no=714)

do you think i can use that under wine?

---

### Post by khamil8686 on 2011-01-25
you might be able to but id be very wary of doing it, wine isnt perfect and wont run all windows software, and if there was a problem halfway through flashing your bios then you could ruin your motherboard, id try to see if they have an option to download your bios to usb or floppy and then manually do it

heres where you can search for bios updates for download
[http://support.asus.com/download/download.aspx?SLanguage=en-us]("http://support.asus.com/download/download.aspx?SLanguage=en-us")

---

### Post by tommcd on 2011-01-25
I would most definitely *not!!!* trust a BIOS update to run through wine.
I would not even trust a BIOS update to run through Windows!!
 What Asus motherboard do you have?

I have used Asus motherboards for some time now. One of the nice things about Asus motherboards is the fact that they have several methods of updating the BIOS that are independent of the operating system you are using. My Asus M2N-SLI-Deluxe motherboard has an EZ-Flash utility that can easily update the BIOS from a floppy (which I used), a flash drive (formatted in FAT16 or 32), or a CDR disc. This all works from the BIOS without ever booting to an operating system.
Gigabyte motherboards (by the way as a comparison) only seem to have BIOS updates available as Windows .exe files that would be problematic to use in linux.

---

### Post by cascade9 on 2011-01-25
> **tommcd said:**
> I would most definitely *not!!!* trust a BIOS update to run through wine. What Asus motherboard do you have?

I wouldnt trust WINE for doing a BIOS update either. 

@ Dsky- if you know what motherboard you have, check the BIOS version then just check theasus  site to see if there is a newer version. 

> **tommcd said:**
> Gigabyte motherboards (by the way as a comparison) only seem to have BIOS updates available as Windows .exe files that would be problematic to use in linux.

They are all .exe files now, which is annoying. Its not really an .exe file, its actually zipped. One of these days I'll try unzipping with WINE. 

Unzip the BIOS, then you can update the BIOS from USB stick, and I think you can still use a floppy as well (I havent had a floppy drive in any of my 'good' systems for years, and even the junkers I just disconnect the floppy). 

Asus is slightly easier in some ways but I prefer the gigabyte dual BIOS voer ease of use myself. I've seen dual BIOS save a lot of trouble over the years (even when gigabyte motherboards werent anywhwere near as good as they are now I said the same thing).

---

### Post by tommcd on 2011-01-26
> **cascade9 said:**
> I
They are all .exe files now, which is annoying. Its not really an .exe file, its actually zipped. One of these days I'll try unzipping with WINE. 

The BIOS updates from the Asus website are provided as .zip files that can easily be unzipped in linux simply by running **unzip** from the terminal.

---

### Post by 1clue on 2011-01-26
My Asus P6T has that ez-update feature.  I think I used a USB stick.

It was funny, I searched the net for several bios update CD images, burned them all -- just in case one failed! -- and then didn't use any of them.  Gotta be the most stupid-simple BIOS update I've ever attempted.  If I had read the directions it could all have happened in 20 minutes, including the download.

---

### Post by Mark Phelps on 2011-01-27
First of all, you shouldn't be updating your BIOS unless there is a compelling reason to do so -- as you know for a FACT, that the BIOS update fixes some problem you're having.

Second, Wine is most definitely NOT the way to do it.

Third, as other folks have pointed out, and my experience bears this out, ASUS motherboards nearly always provide the EZ-flash utility, in which you stick in a diskette or USB stick with the new BIOS .bin file on it and update using that.

Be sure to save your existing BIOS to the USB stick as the first thing you do.  That will allow you to get the old BIOS back if the update goes bad.

---

