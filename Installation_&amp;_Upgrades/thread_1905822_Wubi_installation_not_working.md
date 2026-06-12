---
title: "Wubi installation not working"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by bobthe on 2012-01-07
I just installed Wubi and after the installation and letting it reboot, nothing happens. My laptop rebooted and there were things that were being typed up on the screen and then all of a sudden there was nothing there. My screen was completely empty (black). I waited for a couple of minutes before shutting my computer down manually. When i turned my laptop on again, i saw the windows boot os loader with windows 7 and ubuntu. And after picking ubuntu, all i saw was a purple screen and nothing else. And then again, nothing happened and I was forced to manually shut down my laptop.

These are my laptop specs: 

HP Pavilion dv6-6135dx 
AMD A8 APU with Radeon HD Graphics 1.50 GHz
RAM: 6 GB
64 bit OS

I had a hard time installing Ubuntu the traditional way with partitions 3 months ago when this laptop was brand new and I got to know (through this forumn) that my laptop's hardware werent compatible with ubuntu. So thats why I decided to give Wubi a try.

Can someone please help me?!

---

### Post by bcbc on 2012-01-07
You probably need to use 'nomodeset' to get things working, then go to 'additional-drivers' and install a driver for your graphics card.

See [this post]("http://ubuntuforums.org/showthread.php?t=1613132") for more info on supplying nomodeset. Wubi-specific info is in post#8.

---

### Post by bobthe on 2012-01-09
i added the nomodeset, but again, when i select ubuntu to be booted, i see a purple screen with nothing there and then eventually see a dark screen. Nothing happens and i'm forced to manually shut down. 

someone please help!

---

### Post by bcbc on 2012-01-09
With linux operating systems you can safely reboot by holding [Alt+SysRq and pressing R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot").

If you do hard shutdowns you can corrupt your file system.

So, please describe what happens when you boot - you see the grub menu? And you've tried adding the 'nomodeset' to the first entry, but it still freezes?
Have you tried removing 'quiet splash' to see if there is some output when it hangs up?
Or have you tried booting the second entry (recovery)? Does that work?

More info helps to diagnose so describe in detail what you are doing and what happens. Thanks

---

### Post by bobthe on 2012-01-10
I actually don't even make it to the grub menu. When I turn my laptop on, I see the windows OS boot loader with Windows 7 and Ubuntu under it thats it. I pick ubuntu and see a purple screen with NOTHING THERE. After a few minutes there is a dark screen and nothing is responsive and this is usually when I need to do hard shut downs. and will removing the quite splash make a difference?

---

### Post by bcbc on 2012-01-10
> **bobthe said:**
> I actually don't even make it to the grub menu. When I turn my laptop on, I see the windows OS boot loader with Windows 7 and Ubuntu under it thats it. I pick ubuntu and see a purple screen with NOTHING THERE. After a few minutes there is a dark screen and nothing is responsive and this is usually when I need to do hard shut downs. and will removing the quite splash make a difference?

Hold shift when it boots. That should pop the grub menu (for some newer wubi installs it seems to be hidden). But if that doesn't change anything you may need to edit the \ubuntu\install\wubildr-disk.cfg (see post #8 on that thread I linked to).

---

### Post by bobthe on 2012-01-10
I have already edited that file..which is how i added nomodeset to it...
I'll try pressing shift but i dont expect anything to happen. ill get back to you in a bit

---

### Post by bobthe on 2012-01-10
nothing happened. can someone please help?! i dont wanna resort to vmware but if worst comes to worst ill have to do that. i really wanna dual boot

---

### Post by bcbc on 2012-01-10
> **bobthe said:**
> nothing happened. can someone please help?! i dont wanna resort to vmware but if worst comes to worst ill have to do that. i really wanna dual boot

Change the wubildr-disk.cfg:
Instead of 'quiet splash nomodeset' make it 'nomodeset' or 'noacpi nomodeset'.

If that doesn't make any difference, burn an Ubuntu CD and boot from it, select "try ubuntu" and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Post the results.

---

### Post by IWantFroyo on 2012-01-10
I had a problem that looked exactly like this. It turned out to be an ACPI error.

Try adding "noacpi" in the way bcbc suggested. If it works, you can try replacing it with "pci=noacpi", which should give you back some of your computer's ACPI functions.

---

### Post by bobthe on 2012-03-02
i came back to this post to maybe try to re install ubuntu through wubi. but now after installing it, the file :  \ubuntu\install\wubildr-disk.cfg is not even in the \ubuntu folder anymore. i'm so confused as to why this is happening to me.

---

### Post by bcbc on 2012-03-02
There are two distinct ways to install with Wubi. The one uses an ISO and doesn't have that file, and the new method introduced with 11.10 downloads a diskimage and it uses the new file.

If you run wubi.exe standalone it uses the diskimage. If you run it from a CD or with the ISO present it doesn't. It's not very clear or intuitive.

---

