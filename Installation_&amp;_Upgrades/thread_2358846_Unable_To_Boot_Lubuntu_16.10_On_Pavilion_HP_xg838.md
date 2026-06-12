---
title: "Unable To Boot Lubuntu 16.10 On Pavilion HP xg838"
date: 2017-04-18
forum: Installation &amp; Upgrades
---

### Post by quaesitor2 on 2017-04-18
I first tried with an iso burned disk that I think was made too fast. Then I tried using a dvd-r at the slow setting. I made adjustments in the phoenix bios setting the computer to prioritize cd ROMs. I loaded the CD writer; it still doesn't boot. 

After messing around with the cd writer I decided it was time to give something else a try; I attached my Samsung portable dvd writer via a usb wire to the xg838 and I adjusted the bios settings to prioritize usb connections. All it did was load windows ME edition like normal.

I'm hoping to rehabilitate this antiquated computer to do interim research on what my next computer should be. I'd appreciate some guidance on booting and then maybe installing Lubuntu-16.10-alternative-iso386, thank you.

PS: could I hypothetically be able to reuse the case to make a new 1,200 value computer build like the one shown [here?]([http://lifehacker.com/5840963/the-best-pcs-you-can-build-for-600-and-1200](http://lifehacker.com/5840963/the-best-pcs-you-can-build-for-600-and-1200))

---

### Post by mörgæs on 2017-04-18
> **quaesitor2 said:**
> 
I'd appreciate some guidance on booting and then maybe installing Lubuntu-16.10-alternative-iso386, thank you.


Yes, the [alternate ISO]("http://cdimage.ubuntu.com/lubuntu/releases/17.04/release/") is worth trying but I suggest 17.04 and not 16.10.

---

### Post by quaesitor2 on 2017-04-18
> **mörgæs said:**
> Yes, the [alternate ISO]("http://cdimage.ubuntu.com/lubuntu/releases/17.04/release/") is worth trying but I suggest 17.04 and not 16.10.

17.04 got released about 1 day after I burned 16.10 onto the DVD-Rs. #-o

---

### Post by mörgæs on 2017-04-19
16.10 is still useful for a test if you burned the alternate ISO. I doubt that the full ISO will run.

In the [development forum]("https://ubuntuforums.org/forumdisplay.php?f=427") there is always a sticky note showing the release schedule for next release.

---

### Post by quaesitor2 on 2017-04-19
I was thinking it was the pae flag issue that wasn't allowing the computer to boot from the dvd-r  so I tried Lubuntu 12.04 for 32-bit computers. Windows ME loaded like normal no matter whether I used the usb connection or the internal cd-rw. I tried the mini.iso which didn't work either.

---

### Post by mörgæs on 2017-04-20
You need to provide much more information.

Why do you think it's a PAE problem?
Which processor do you have, a Pentium 3? 
Which error do you get when trying to install using the mini.iso?

---

### Post by quaesitor2 on 2017-04-20
> **mörgæs said:**
> You need to provide much more information.

Why do you think it's a PAE problem?
Which processor do you have, a Pentium 3? 
Which error do you get when trying to install using the mini.iso?
 
The reason I  think it's a pae problem is because my processor is a Celeron M 800 mhz and I read that Celeron M's are non-pae.
I get no errors at all; it just boots into Windows ME like the disk doesn't exist.

---

### Post by quaesitor2 on 2017-04-20
Yesterday when I went to attempt a netboot of Lubuntu on my HP Pavilion I realized that my ethernet cable plug was slightly too large for the ethernet port. It is actually a dsl port. Does anyone here know of a way to connect a computer by its dsl port to a router by its ethernet port? Would a splitter be the right solution?

---

### Post by mörgæs on 2017-04-21
> **quaesitor2 said:**
> The reason I  think it's a pae problem is because my processor is a Celeron M 800 mhz

No, Celeron M were only used in portables. Since you have a stationary and it's 800 MHz I guess it's a Celeron 3, probably a Coppermine. 

> **quaesitor2 said:**
> 
I get no errors at all; it just boots into Windows ME like the disk doesn't exist.

Does the computer (try to) boot from CD/DVD using any of the ISO's you have tried?

---

### Post by mörgæs on 2017-04-21
> **quaesitor2 said:**
> Yesterday when I went to attempt a netboot of Lubuntu on my HP Pavilion I realized that my ethernet cable plug was slightly too large for the ethernet port. It is actually a dsl port. Does anyone here know of a way to connect a computer by its dsl port to a router by its ethernet port? Would a splitter be the right solution?

If you decide to go on with the computer then the best solution is to find a used netcard. Should cost next to nothing.

---

### Post by quaesitor2 on 2017-04-21
> **mörgæs said:**
> No, Celeron M were only used in portables. Since you have a stationary and it's 800 MHz I guess it's a Celeron 3, probably a Coppermine.

You're right, I checked it again and I see no "M". I'm not sure how I thought that in the first place. It says Intel Celeron Processor, above the name is 800 Mhz.  Here's an img link containing a photo of my desktop, focusing on the specs: [www.ultraimg.com/image/0xPx](www.ultraimg.com/image/0xPx)



> **mörgæs said:**
> Does the computer (try to) boot from CD/DVD using any of the ISO's you have tried?

It doesn't try at all. If it is it isn't obvious cause it looks just like a routine booting of Windows ME.

---

### Post by mörgæs on 2017-04-21
Does the CD/DVD boot in another computer? 

You should be warned that the performance (if you get some kind of GNU/Linux installed) will be too slow to serve any sensible purpose. 128 MB may not even be enough to display a GUI. I consider 1 GB the minimum, and often I find much stronger hardware discarded.

---

