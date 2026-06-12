---
title: "Lost ability to boot windows"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by Thomar on 2007-04-16
I had a major problem installing Efty Edge.

After burning the image onto a CD, I booted it up, got a very good impression from the system, and decided to install it.  Because I already have Windows on my Toshiba Satellite laptop, I had the partition manager cut up a little over 4GB of space off of my hard drive so I could dual-boot.  I noticed Firefox was working normally, so I started surfing a bit to stave off boredom.

However, after the installation got 90% through and was detecting drivers, it said something about detecting USB drives and then the install application stopped.  I noticed this because both the CD and the hard drive had been running nonstop, and they both stopped abruptly.  After waiting about 10 minutes with all other applications closed and the installer doing nothing, I closed the installation and quit Ubuntu.  When I tried to boot from the hard drive, I only got the following:

"j"

And that was it.  When I booted from the CD and told it to use the hard drive, I got a small "starting" message before the "j".  :( 

Being very grateful that I have an copy of the assignment due on Tuesday both in my keychain and at the computer lab on campus, but very afraid all my other work had been deleted, I booted up Ubuntu again.  I was  disappointed that I couldn't mount the hard drive from the CD.  However, the partition manager showed that the large (windows/media) partition was still present and was as full as it should be, so this helped me calm down significantly.

I tried the installation again, this time with my USB mouse out, and everything went fine (though I'm a bit suspicious of why the installer needs to put all the language files on disc and then remove them again).  I was very happy to find that I had access to all of my work and had not accidentally deleted everything.  However, after trying to use the dual-boot system (I think it's BLARG or something similarly aesthetic), booting Windows returned a "disc write error" message.

Ubuntu works just fine (besides the USB mouse, Windows Logitech, works intermittently, but the touchpad works fine and I'm familiar with all the standard keyboard controls), and if I'm stuck with an OS this is the one to have, but I'd *really* like to get Windows running again.  Can I get some help here?

---

### Post by Thomar on 2007-04-16
Well, it looks like it fixed itself.  Windows ran CHDISK when I booted it up this morning, and everything's working just fine now.  I think it found the new partitions on bootup, but they're probably not showing up until I reboot.

---

