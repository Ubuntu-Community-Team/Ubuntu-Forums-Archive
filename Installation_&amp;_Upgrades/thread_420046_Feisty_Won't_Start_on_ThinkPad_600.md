---
title: "Feisty Won't Start on ThinkPad 600"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by w3jf on 2007-04-23
I installed 7.04 in a multiboot configuration with Xandros on a desktop and was so pleased with it, I decided to use it to replace Xandros on my old IBM ThinkPad 600.  I attempted to boot from the CD (same CD I'd used successfully on the desktop) and it froze immediately after the initial splash screen.

After the line telling me the BIOS was pre-2000 and I'd have to use ACPI=Force, it generated two and a fraction more lines:

[41.947588] Invalid compressed format (err=1)
[41.954997] Kernel Panic - not sync-ing - VFS: Unable to mount root fs on unknown block (104,1)
[41.955708] _

   --- at which point it froze.  

I tried it with a second CD and it repeated.  

Any clues?

John

---

### Post by dannyboy79 on 2007-04-23
you need to try to use the following boot options. also, what kind of graphics adapter is in this laptop? how powerful is this laptop? you might want to try out xubuntu instead.

noapic nolapic

I would also recommend removing the "splash quite" from the end of the boot line as well. this way you can see what it get's stuck on. normally quite boot option will not display any of the boot process and normally splash will show you an image while it's booting. often times ati adapters will choke on the splash screen so it's good to try it without the splash until you can get in and change the xorg driver. the live cd atempts to figure out your graphics adapter and sometimes choses the wrong driver and then freezes. so sometimes you need to follow this guide to even get past that: [http://ubuntuforums.org/showthread.php?t=386688](http://ubuntuforums.org/showthread.php?t=386688)

and read post #5 within that link.

---

### Post by w3jf on 2007-04-24
Thanks for the reply.  The answer was to go to Xubuntu.  
 
The ThinkPad 600 is a 9-year-old laptop with a 300 MHz CPU  and only 192 Mb RAM -- just not enough to handle full blown Ubuntu.  

John

---

