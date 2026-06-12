---
title: "vodafone webbook armv7l - how do I upgrade?"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by keep-on-smiling on 2012-05-10
Hello All

I have a Vodafone Webbook which originally came with Lucid installed (despite the fact that the system was bought just before Christmas last year...).

lscpu gives me: Architecture armv7l (last letter is a lower-case L)

The list of repos points to:

[http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid ....

and there is one somewhat unusual aspect:

[http://charlotte.archive.canonical.com/](http://charlotte.archive.canonical.com/) lucid-charlotte public

I HAVE managed to find a link which might indicate that 12.04 should be available for this platform - assuming I have the right image - here: [https://wiki.ubuntu.com/ARM/MX5](https://wiki.ubuntu.com/ARM/MX5)

could somebody please verify that I am on the right track ? I confess that I am far more at ease in the normal world of 32 / 64 normal PCs...

also, the instructions from that link mention copying the install image to a microSD card - except that this system only has 2 USB ports... I was able to locate a microSD-USB adapter, but that did not seem to work by default and I have not yet managed to get to whatever this hardware uses for a BIOS in order to find out what the set boot order is.

sooo, to summarise then:

Is my choice of install image correct ?

How do I get the system to boot off the image, if it IS correct.

This link [https://wiki.ubuntu.com/ARM/](https://wiki.ubuntu.com/ARM/) indicates that 12.04 IS available for my system, but the download only shows Oneiric.

all help appreciated - I am out of ideas at this point !

Thanks

---

### Post by AndyRabagliati on 2012-07-29
Did you make any progress ?

I also got one from a dissatisfied user.

There is a switch behind that battery that changes the boot behaviour, and it looks for a CDROM for install media.                                                                                             
                                                                                                                                          
The 'net says that the ARMv7 can handle armhf (hard float) as well as the soft-float armel - but I am more concerned to get it up to 12.04.                                                                       
                                                                                                                                          
ports.ubuntu.com seems to go up to precise, but the "armel" kernel seems to come from lucid-charlotte - which does not appear to have an upgrade candidate.                                                      

Cheers,  Andy!

---

