---
title: "Another, Linux won't boot after installation."
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by PopnPaul on 2008-03-17
I installed ubuntu 7.10 and it starts the loading bar and doesn't go farthe than 1/10. I have an 8800GT, might that be why? I read some other topics and people said that my ubuntu doesn't have a "/" so it doesn't have a root volume. How would I go about changing it? Thanks

---

### Post by Ecclesia on 2008-03-17
How did you install?  Did you boot off the live CD or did you use the alternate installer?

I had to boot the cd with the safe video option, install that way and then manually use the Nvidia beta drivers to get my video card working (it's a 7150, but I've heard people have similar problems with the 8800s).

---

### Post by PopnPaul on 2008-03-18
I installed using the alternate cd, GRUB loads and picks ubuntu. Then ubuntu gets stuck on the loading bar. Ubuntu is now reporting an xfer mask error 0x40. For some reason ubuntu can't find my hard drives.

---

### Post by Ecclesia on 2008-03-18
That's odd, I suppose you would want to post what hard drive controller your motherboard is using and hope that someone has a work around (this is beyond my expertise).  You might search for your motherboard model number and see if others have had the same issue.

Does the live cd boot?  Is this the reason that you tried the alternate installer?

---

### Post by PopnPaul on 2008-03-18
Alright I read a lot on this forum and here is what happened.

I have a P35 chipset and an 8800GT, the worse combo for installing linux, especially for a linux nub like me. 

I had to use the alt cd cuz the Live cd does not work with the 8800 series, G80 and G92 cores.

After installing I got random errors that said

"failed to set xfer mask (0x40)" or something like that. 

I read up on the forums, and I had to move my hard drives to the highest sata port on my motherboard. So for example, I moved my 2 hard drives from sata ports 1/2 to 5/6

This fixed ubuntu starting up, but gave me GRUB Error 17. I loaded up SUPER GRUB and I ran the auto fix and now it works.

Now I have to install the 8800GT drivers.

The only error now, is when I plug in my 3rd SATA hard drive, these failed to set xfer mask errors return. I'm really not sure on this one. So ima go read more, but if anyone knows what happens please tell me.

---

