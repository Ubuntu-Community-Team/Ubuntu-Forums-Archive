---
title: "Problems running live CD"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by licksick on 2007-01-08
I am a linux and ubuntu newbie, but I hope to change all that.  I am trying to get an old box I got for free to run ubuntu, but no luck.  The live CD works fine on my newer box, but not the old freebie box.  I have checked the CD for errors using the new box, and checked the md5 hash, and all is fine in that realm.  I am using the i386 live CD.  The old box runs win98 fine, so I doubt it's a hardware malfunction.

     Old Box (desktop):
         256 MB RAM
         AMD k6 300Mhz
         NEC Multisync C400 Monitor
         Not sure what motherboard
         3 gig HD with Win98 installed (2GB free)
         9 gig HD completely empty

    Initially I got an error "ACPI: Unable to load RSDP", but searching the forums I was able to fix that by changing the boot prompt to say "boot: live noacpi acpi=off apm=on", but the results I get are the same - **everytime I try to boot from the live CD I get a redish brown screen with verticle lines on it (no cursor, text, nothing). ** If I leave the computer for a LONG time I eventually get a black screen (no cursor, text ,etc), but the monitor still has the green light indicating it is recieving a signal.
    Not sure what to do, any help would be appreciated.  Thanks.

---

### Post by licksick on 2007-01-08
I forgot to mention I am trying to install 6.10 Edgy

---

### Post by taurus on 2007-01-08
Do you plan to run the LiveCD on your old machine or do you plan to install Edgy on it?  If you plan to install Edgy on it, I recommand you use the alternate CD.  Even though it's a text installer, it's real easy to follow and works great too.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by hal10000 on 2007-01-08
A normal ubuntu live cd (with gnome or kde window managers) may be to big for you 300 MHz cpu. You may try xubuntu cd instead, it needs less hardware performance.

---

### Post by oscrmyer on 2007-01-08
Sounds like you see to turn  apci off. You should be able to use that option from the menu that pops up from the live CD before the system boots. The second part sounds like some video card funki-ness (yes that is a technical term) it might be solved by turning apci off but I am not too sure.  
"acpi=off"

---

### Post by licksick on 2007-01-08
First of all:  THANK YOU for your reply.  I know time is precious and helping newbies tie their shoes can be a pain.
   
   Yes, I plan on installing.  I am planning on doing a dual boot win98 and ubuntu on separate hard drives.  I plan on using ubuntu, but being a newbie it would be nice to boot windows if I felt I needed it for something.  But I figured if the live CD didn't work then installing it also might not work.

     I will give the alternate CD a try.  I was nervous to try that approach because I am new to linux.  But I'll try it and see.  Hope it works.

---

### Post by licksick on 2007-01-12
Ok, here's the update.  I tried using Xubuntu live CD, same problem.  I tried using the i386 Ubuntu alternate CD in order to use the text based installer, and it gave me the following error:

[B]BASE SYSTEM INSTALLATION ERROR

The debootstrap program exited with an error (return value 1)

Check /var/log/syslog or see virtual console 4 for the details.
[/B]
The problem is I have no idea how to even access /var/log/syslog or virtual console 4 in order to see what the error is.  **Any help would be appreciated. ** I should probably note that when I run any of the Ubuntu cds on this older box I don't get the usual menu I would on a newer system (with the option to check CD integrity and all that), instead I get a "boot:" prompt with the option to press F1 to enter a help menu.  I have checked the MD5 hashes and cd integrity on my newer system, so I know thats not the problem.

---

### Post by hal10000 on 2007-01-12
You can get access to th virtual console 4 by simultaneously pressing the <ALT>+<F4> keys.

THere you may see where it hangs. Post what you find.
I suppose it is an ACPI problem, so might use the noacpi option on the boot prompt

---

### Post by licksick on 2007-01-12
I get the error even when typing "install noacpi acpi=off apm=on" or in the case of a live CD "live noacpi acpi=off apm=on".  I read to do this in another forum thread because I kept getting an error stating "ACPI: unable to locate RSDP".  So I turn acpi off and I no longer get the RSDP error, I get the errors described in this thread instead.  (A garbled red screen and no installation).

  Also, please understand that I am a complete newbie, so I'll experiment and probably find out, but please be as specific as possible.  I have no idea when to press <alt><f4>.  Before installation at the boot prompt?  When I get an error message?  After a failed install attempt?

Don't get me wrong, I appreciate your help, I just really am completely inexperienced in linux, and this is all new to me.

---

### Post by hal10000 on 2007-01-12
Press the keys after the erroe message appers

---

### Post by kghosh22 on 2007-02-12
> **licksick said:**
> I am a linux and ubuntu newbie, but I hope to change all that. ............

     Old Box (desktop):
         256 MB RAM
         AMD k6 300Mhz
         NEC Multisync C400 Monitor
         Not sure what motherboard
         3 gig HD with Win98 installed (2GB free)
         9 gig HD completely empty

....... Thanks.

Not sure if had success. I had a similar h/w and tried all the stuff w/o success. Then tried older distros. Knoppix 3.1 worked the best for me. Maybe if you can get hold of a copy, try it.

Hope that helps.
- K.Ghosh

---

