---
title: "Intrepid Ibex 8.10 Beta x64 Cd - kernel panic on boot"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tqft on 2008-10-18
Motherboard: P5Ld2-VM
Processor: Intel Pentium D 805
Memory: 3Gb
Only ide drives in machine - no sata drives

Downloaded Intrepid Ibex 8.10 Beta x64 Cd - burnt & booted

got the boot options screen (live vs install etc) screen
hit enter - "kernel live" message, then "kernel really live" message
then no further action

Tried again with boot option acpi=on as per current intrepid (upgrade from hardy) boot sequence - kernel panic message.


any ideas?

Am downloading alternate x64 cd to give that a go.

---

### Post by Yellow Pasque on 2008-10-18
IIRC, The Pentium D 805 doesn't support x86-64

**On second Google, it looks like I was wrong :P**

---

### Post by Dufangoer on 2008-10-19
bump!!hahacheap wow power leveling --------------------------------**buy [eq2 plat](http://www.epaxx.com),  [eq2 gold](http://www.epaxx.com), [everquest platinum](http://www.epaxx.com), [rs gold](http://www.favgames.com/rs-gold/), [silkroad gold](http://www.favgames.com/silkroad-gold/),**

---

### Post by felker2 on 2008-10-19
Your Intel Pentium D 805 is x86-64 compatible, so the AMD64-CD should work. And: the CD would give a *nice* explanation if your hardware was not 64bit-enabled.

About "kernel really alive" (with an a) in your 8.10 64-bit version: I think you should use trial-and-error to find out what's wrong. Suggestions:

- try the "Safe Graphics Mode"
- try the 8.04 64bit version
- try the 8.10 32bit version
- remove "quiet splash" from the boot options
- burn the 8.10 x86-64 image at low speed and try again
- try the same CD in another 64-bit system

HTH

---

### Post by tqft on 2008-10-20
rsynched latest 8.10 - same again
tried safe graphics mode - same again
lenny amd64 dvd - booted but crapped out trying to fix the partitions
remove "quiet splash" - no luck - drops its bundle at about 1.6 secs still

will keep rsynching and see if I have any luck

thanks for trying

---

### Post by tqft on 2008-10-22
Think I have found the problem.

I would like to thank asus for shipping the motherboard without the drivers for 64bit os'es.

Would explain the errors I saw when trying to boot Intrepid & the inability of Lenny to partition drives (ie hard disks not responding properly to commands).

I will update the bios and attempt to install the 64 bit drivers for the chipset(s) on board.

Unfortunately the motehrboard doesn't appear to be supported by coreboot directly.  More research required by me there.

I will reply when I find out if this was the case - as there may well be mroe people out there with similar problems (taking the opportunity to go x86_64 and getting boot errors).

---

### Post by Roasted on 2008-10-23
Imagine that. I'm having the exact same problem and I have an ASUS motherboard.

What's weird is, I have Hardy 64 bit installed with no problems. 

Is there a fix for this??

Is it to be fixed upon final release?

---

### Post by tqft on 2008-10-23
Roasted,

Check the manufacturer or asus (if you bought a bare motherboard) website for bios updates and check through the changelogs.  Check which version of BIOS you have - "sudo lshw"  I found to be very helpful in spitting out m/b data without killing everything.

Hoep it helps.

---

### Post by Roasted on 2008-10-24
It appears to be fixed. I found a bug report that announced on the 14th that it was fixed with 2.6.27-7.11

I went to daily build and downloaded the latest version. As we speak, I have Ubuntu Intrepid 64 bit 8.10 installed on my system which has the ASUS P5QL motherboard. I had no issues at all installing it.

I guess the ISO I downloaded was an older one, whereas daily build has frequent enough updates that allowed me to download the fully patched beta version this afternoon and install it.

All is well on my end, now. :) Good luck!

---

### Post by tqft on 2008-10-28
> **Roasted said:**
> It appears to be fixed. I found a bug report that announced on the 14th that it was fixed with 2.6.27-7.11

I went to daily build and downloaded the latest version. As we speak, I have Ubuntu Intrepid 64 bit 8.10 installed on my system which has the ASUS P5QL motherboard. I had no issues at all installing it.

I guess the ISO I downloaded was an older one, whereas daily build has frequent enough updates that allowed me to download the fully patched beta version this afternoon and install it.

All is well on my end, now. :) Good luck!

Did you use any boot parameters?  

Tried acpi=on OR irqpoll   with CD integrity check, live cd and install - all give the same basic result.

Still getting a crap out about after initramfs loads (1.7sec) with 8.10 amd64 rc.  Not sure if it is initramfs where it dies but I see it flash past and then stacktrace messages.

Will try 8.10 rc i386 tomorrow.

---

### Post by Roasted on 2008-10-28
I didn't use a darn thing. I simply downloaded the latest ISO from Daily Build (8.10 64 bit) and burned the image to a CD with k3b in Hardy.

Booted up, detected it, bam... just fine.

It may also be worth noting that my drives are running in AHCI mode. I think that was the one thing with this board, that IDE Legacy mode was a little finicky. Who wants IDE Legacy mode anyway when you got a couple SATA drives to play with? :)

---

