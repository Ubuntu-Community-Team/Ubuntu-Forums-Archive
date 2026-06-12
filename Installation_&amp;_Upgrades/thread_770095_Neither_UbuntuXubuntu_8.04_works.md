---
title: "Neither Ubuntu/Xubuntu 8.04 works"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by mypetduck on 2008-04-27
I tried the alternate install of Ubuntu 8.04 and Xubuntu 8.04 on an older laptop; in both cases after the boot page (with the colored bar) a blinking cursor would appear in the upper left center of the screen. Then nothing. [Toshiba Portege 7200CT, 320MB RAM, 6GB HD, Pentium III 500Mhz]

I'll have to go back to Xubuntu 7.10, unless Ubuntu 7.10 is an option. I'm eager to try it, but with my specs...

---

### Post by mypetduck on 2008-04-27
Does it matter how I partition the HD? Any suggestions how to partition the 6GB HD I have?

---

### Post by ugm6hr on 2008-04-27
6GB will be a squeeze for Ubuntu (7.10 or 8.04).

In fact, since 7.10 Xubuntu has been a bit beefy for that too.

Don't think that has anything to do with why the Alternate CDs for 8.04 won't work.

Are you sure the CD burn is OK?

---

### Post by mypetduck on 2008-04-27
How can I verify the integrity of the CD burn?

---

### Post by Patsoe on 2008-04-27
There's an entry in the boot menu that let's you do that. See this image, second entry:

[http://learninginlinux.files.wordpress.com/2008/04/dscf0001mod.jpg](http://learninginlinux.files.wordpress.com/2008/04/dscf0001mod.jpg)

You could try to hit F6 to enter extra kernel boot-parameters, and disable the framebuffer by adding "fb=false" (also explained under F1 -> Help).

---

### Post by mypetduck on 2008-04-27
> **Patsoe said:**
> There's an entry in the boot menu that let's you do that. See this image, second entry:

[http://learninginlinux.files.wordpress.com/2008/04/dscf0001mod.jpg](http://learninginlinux.files.wordpress.com/2008/04/dscf0001mod.jpg)

You could try to hit F6 to enter extra kernel boot-parameters, and disable the framebuffer by adding "fb=false" (also explained under F1 -> Help).

Both my Ubuntu and Xubuntu 8.04 alternates CDs are valid, as are all the checksums. 

What are the chances that my computer can't handle 8.04? Or, if the CDs and checksums are valid, is it still possible the CD didn't burn correctly? What parameters should I set up in Infrarecorder to burn the image?

---

### Post by Patsoe on 2008-04-27
I think if the "check CD for defects" tool on the CD doesn't complain, then your CD is fine. Did you see/try the "fb=false" idea? I'm just thinking that could help because your graphics chip is... old :)

---

### Post by mypetduck on 2008-04-27
> **Patsoe said:**
> I think if the "check CD for defects" tool on the CD doesn't complain, then your CD is fine. Did you see/try the "fb=false" idea? I'm just thinking that could help because your graphics chip is... old :)

That's my next step. What does it alter about the installation?

---

### Post by Patsoe on 2008-04-27
It means you'll miss out on this: [http://en.wikipedia.org/wiki/Linux_framebuffer](http://en.wikipedia.org/wiki/Linux_framebuffer) so your installer screens may look somewhat old-skool.

---

### Post by mypetduck on 2008-04-27
> **Patsoe said:**
> It means you'll miss out on this: [http://en.wikipedia.org/wiki/Linux_framebuffer](http://en.wikipedia.org/wiki/Linux_framebuffer) so your installer screens may look somewhat old-skool.

My F6 doesn't give me that option. I get Expert Mode, Noapic, Nolapic, acpi=off, and another I can't recall right now. In fact, the spelling is likely off on some of those--but at any rate, no option to turn off the frame buffer.

I might just have to reinstall Xubuntu 7.10.

---

### Post by Patsoe on 2008-04-27
That's when you hit F6 the second time, I think. The first time you get a list of kernel parameters.

---

### Post by mypetduck on 2008-04-27
Do I type it in after that string of boot options?

---

### Post by mypetduck on 2008-04-27
> **mypetduck said:**
> Do I type it in after that string of boot options?

I just did and it's moving forward. Fingers crossed for Xubuntu 8.04.

---

### Post by Patsoe on 2008-04-27
> **mypetduck said:**
> I just did and it's moving forward. Fingers crossed for Xubuntu 8.04.

Great. I'll keep my fingers crossed allright, but I'm also off to bed... Good luck!

---

### Post by mypetduck on 2008-04-27
Didn't work. I'm going back to Xubuntu 7.10. Thanks for your suggestions, it was worth a try.

---

