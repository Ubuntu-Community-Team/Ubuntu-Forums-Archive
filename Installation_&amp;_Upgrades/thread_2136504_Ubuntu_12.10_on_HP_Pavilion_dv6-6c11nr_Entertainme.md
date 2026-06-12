---
title: "Ubuntu 12.10 on HP Pavilion dv6-6c11nr Entertainment"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by The Catboy on 2013-04-17
Hey everyone! ^_^ A little new here to the forums, although not new to Ubuntu since I've been using for many years actually. But recently my boyfriend and I got a new laptop, which is an HP Pavilion dv6-6c11nr Entertainment. And I have been trying to install Ubuntu on it for quite some time, but can't seem to get it to boot into the desktop. It loads the mouse, but either loops or just stays on the boot screen with the mouse there.Does anyone know how to fix this and how to install Ubuntu on my laptop? This has been bugging me for weeks now.Any help would be appreciated!-Lucario

---

### Post by AnaheimSam on 2013-04-18
What works for me is if I install my video drivers. Go to your oldest Linux kernel, boot in recovery mode, and select boot.
Login, and go to software sources (System Settings>Software Sources). When you get there, you should see a tab that says "Drivers." Click that tab, and get the drivers you need. You have a laptop, so best to plug it into an Ethernet connection rather than wi-fi, just in case you don't have your wi-fi driver installed. In which case, get your wi-fi driver, too. Do this, then restart. You should now be able to get into your regular desktop in a normal fashion.

---

### Post by The Catboy on 2013-04-18
I tried that and it still didn't work. Oddly enough distros like Bodhi Linux, JoliOS, and other Ubuntu based distros work just fine, just not the default Ubuntu.

---

### Post by illmattic on 2013-04-18
Sorry to jump in on your thread but I have the same problem. I have a hp Pavilion dv6 and the processor is AMD A8-3510MX APU with Radeon(tm) HD graphics 1.80. I'm trying to dual boot Windows 7 and Ubuntu 12.10 together. I created the allocated space but when I put in the live-dvd and reboot windows comes up. 

Matt

---

### Post by AnaheimSam on 2013-04-18
The Catboy:
Same with me...
Thats why I use Xubuntu instead of the original Ubuntu.

For me, it was just easier to switch to an official derivative rather than fix the issue. In my case, Xubuntu and Kubuntu work like a charm.

Besides which, if Joli or Bodhi work on your machine, why not use those?

---

### Post by The Catboy on 2013-04-18
I tried Xubuntu and it does the same thing. I am not sure, the hardware to this laptop seems to be extremely picky to what will work on it. I didn't do much research on this laptop before I got it because it was the only laptop in my budget at the time.I am going to try Lubuntu and see if that works on it. If I can least get it to boot, I can install it and work on it from there.

---

### Post by The Catboy on 2013-04-18
Lubuntu didn't work either.

---

### Post by AnaheimSam on 2013-04-18
I apologize. I misunderstood you. I thought you had already installed Ubuntu 12.10, but you said you are having problems installing it.

My bad.
Again, I had the same issue.

Try to boot into your installation media. When you first do so, you will find a screen that looks much like this, with the two symbols on the bottom.[IMG]http://2.bp.blogspot.com/-Fjw6yl1x3Zc/TVUlk_57J_I/AAAAAAAAAEg/cljA9QoAW7o/s1600/boot.png[/IMG]

Hit the space bar.

You should then be taken to a screen that looks like this.
[IMG]http://www.dedoimedo.com/images/computers_years/2011_1/kvm-ubuntu-booting.jpg[/IMG]

Press F6 (or fn+F6 if that is how you fashioned your machine to work) and select nomodeset by highlighting it and pressing Enter. Make sure there is an "X" next to "nomodeset" before you proceed.
After this, press ESC, highlight "Install Ubuntu", then press enter.

You SHOULD see something like this on your screen next...
[IMG]http://www.comoinstalarlinux.com/wp-content/uploads/como-instalar-ubuntu-12.10-001.jpg[/IMG]

This means you are in nomodeset. Try to install as you normally would.

Try that and tell me about what happened.

---

### Post by The Catboy on 2013-04-18
> **AnaheimSam said:**
> I apologize. I misunderstood you. I thought you had already installed Ubuntu 12.10, but you said you are having problems installing it.



My bad.

Again, I had the same issue.



Try to boot into your installation media. When you first do so, you will find a screen that looks much like this, with the two symbols on the bottom.



Hit the space bar.



You should then be taken to a screen that looks like this.





Press F6 (or fn+F6 if that is how you fashioned your machine to work) and select nomodeset by highlighting it and pressing Enter. Make sure there is an "X" next to "nomodeset" before you proceed.

After this, press ESC, highlight "Install Ubuntu", then press enter.



You SHOULD see something like this on your screen next...





This means you are in nomodeset. Try to install as you normally would.



Try that and tell me about what happened.
Try that and after getting past the boot screen, the screen went crazy and became all static.

---

### Post by The Catboy on 2013-04-19
I've tried pretty much everything thus far and still can't seem to get Ubuntu, Xubuntu, nor Lubuntu to boot. I really didn't want to try Kubuntu since I am not a big fan of KDE, but I guess I will try it anyways just to see if that will boot.

---

### Post by The Catboy on 2013-04-19
So I tried Kubuntu and that did the same thing :/

---

### Post by The Catboy on 2013-04-19
Interesting note, just for sake of it, I ran 11.10 on my laptop and it ran just fine. This isn't the first time I had to install an older version of a Linux distro to make things work.

---

### Post by superdaveozzborn on 2013-04-19
hmmm

just a thought. Have you tried the Ubuntu alternate edition, it uses a text based install instead of the Live Desktop.

---

### Post by The Catboy on 2013-04-20
I didn't try that actually, but it's a bit late now. I was able to install 11.10 and upgrade from that to 12.04, then to 12.10 just fine.
So I guess this is solved, just not sure why 12.10 didn't work to began with :/ Then again my laptop seems to do whatever it wants half the time.

---

