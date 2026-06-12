---
title: "Ubuntu won't install, can't get past bootscreen!"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by wontstoptalking on 2008-03-26
I'm trying to install Ubuntu 7.10, and when I boot up the Live CD and hit the first install option (called "boot live cd or install" or something like that) it gives me something that says something about acpi=force (but I googled that and it's not helping), then it shows me this endlessly flashing underscore in the top left corner of my screen that never does anything or goes away. I then tried installing in the alternate text mode, and not only found it extremely confusing, but it also would not install the Linux kernal, and so I had to install the alternate generic kernel or whatever the other one is. Then the alternate CD froze up. I checked both CD's for errors and all that stuff and turned up with nothing.

What I really want it to be able to install ubuntu using the regular CD, because the alternative text mode is a lost cause for me, and it isn't working anyway. 

My problem again: After booting up normal Live CD, and seeing splash screen with options such as "start live cd or install" and all those others, I hit enter on "start live cd or install" and it flashes pretty quickly: "acpi force is required to enable acpi" and then does the normal loading screen with the Ubuntu logo and the little orange bar bouncing left and right, like it's going to work. Then it shows the flashing underscore in the top left hand corner.

I'm trying to do this on an HP Pavilion A440.

Please help!

---

### Post by wontstoptalking on 2008-03-26
Oh, and I heard that you could hit F6 in the boot screen and enter some options, and so I thought that maybe I could pull off adding "acpi=force" to the boot options, but it was no good. I tried several different types: I tried "acpi=force", "force=acpi", and "force acpi". None worked. So I really am lost here.

---

### Post by wontstoptalking on 2008-03-26
And I hate bumping this thread but I am on limited time (I only have today) and so I need all the help I can get as soon as I can get it.

And by the way, I have Ubuntu running on two of my desktops at home, so I am familiar with how it works, and I love it. It just beats me why this isn't working this time. I have never met a machine that did not work with Linux without any tweaks.

---

### Post by damispyderbyte on 2008-03-26
Acpi wont work with many HP pc's disable it with command acpi=off

I had the same problem also

Hope this helps! :grin:

---

