---
title: "During installation of 10.10 scren goes black"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by ba0bab on 2010-10-17
Hi

I have a show-stopping problem while installing 10.10, and I hope you guys can help me – I've searched high and low for an answer, and I can't find one!

It's pretty straightforward: At some point during installation, the screen shuts down, just like it would if there wasn't any signal (if the screen is on but the PC is off, for instance). This means that I can't finish the installation. I've tried both the desktop and the alternate installer, and I've tried enabling all the “other options” when pressing F6 – also the expert-option available in the alternate installer. 

 No matter what, at some point, it seems to loose the signal, or go into sleep mode or something. I have an ATI Radeon 4890. 

I've also tried editing the boot options by pressing F6 and instead of the ending looking like this:

cdrom/preseed/ubuntu.seed vga=788 initrd=/instal/initrd.gz quiet --

then, in a desperate attempt I followed this: [http://tutorial.downloadatoz.com/how-to-fix-black-screen-issue-when-installing-ubuntu-10-10.html](http://tutorial.downloadatoz.com/how-to-fix-black-screen-issue-when-installing-ubuntu-10-10.html)

so the parameters looked like this:

cdrom/preseed/ubuntu.seed vga=788 initrd=/instal/initrd.gz nomodeset single

Still the same. It seems to happen mostly when installing the base system, but has also happened while configuring timezone etc. I can't really figure out a pattern.


I also tried using “OEM mode” when pressing F4.

I would be very grateful for an answer!

This guy seems to have the same problem:

[http://www.oblurb.com/ubuntu-update-killing-my-installation.html#comment-137](http://www.oblurb.com/ubuntu-update-killing-my-installation.html#comment-137)

---

### Post by ba0bab on 2010-10-17
I also tried adding:

xforcevesa in the boot options. I also tried changing the vga=788 option, but that didn't work either - actually it seemed like the screen shutdown even quicker, although it might be by chance.

---

### Post by Rubi1200 on 2010-10-17
You might want to give the Alternate CD a try:
[http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

Scroll down to the relevant section

---

### Post by ba0bab on 2010-10-17
Hi,

thx for your reply, but as I wrote, I already did that :)


I tried with these boot options as well:

acpi=off, noapic, nolapic

When I did that, it got longer than the other 15+ times I have tried installing today, but still went into standby mode.

I tried updating my BIOS as well. Also, I tried an 9.10 Karmic Koala CD, just running the installer untill "choose language" just to see if it went into standby. And it did! Makes no sense, this is the third Ubuntu version I have installed on this PC with this exact hardware, so for the life of me I can't figure out why it is a problem now

---

### Post by Rubi1200 on 2010-10-17
Have you tried turning of AHCI in BIOS to see if that makes a difference?

And, do you, by chance, have a RAID setup?

---

### Post by cbusick on 2010-10-17
I am having a similar problem.  After I select the Try or Install option, the bottom 3/4 of my screen flickers purple for a few seconds then continuously flickers gray colors.  I've never seen ubuntu do this before and it makes me sad.  Any suggestions?

---

### Post by ba0bab on 2010-10-17
Just googled to figure out what AHCI was - and it doesn't seem like there is anything about it in my BIOS? It's a Asus M4A79T deluxe motherboard.
And no, I don't have RAID.

It also suspends when I'm in the BIOS, not only when installing an OS! Perhaps it's my screen? But I have installed several OS with it before, and I tried disabling all sleep-related features in it with no luck.

cbusick: I'm not sure it's the same problem - my screen just goes into sleep mode, as if the pc has gone into standby (or shutdown, which it definetely isn't). I don't get funky colors or anything like that.

---

### Post by cbusick on 2010-10-17
I just figured out my screen problem.  I switched out my 30" monitor for my older 21" and the problem went away.

ba0bab: Maybe try a different monitor?

---

### Post by Rubi1200 on 2010-10-17
> It also suspends when I'm in the BIOS, not only when installing an OS!

To be honest, I have never heard of this happening before; how odd?!?

As cbusick just suggested, try switching to another monitor.

---

### Post by union two levers on 2010-10-17
annoying isn't it ! one of my computers has a celeron 733mhz processor and 256mhz memory...it will not allow installation of xubuntu above 9.04 but will mostly run the live cd ok, however tried linux mint 9 based on ubuntu 10.04 and hey presto perfect...i have the same question why oh why will one version of ubuntu run perfectly ok but subsequent versions completely fail ? if we are to get ordinary people try ubuntu surely any machine that can run windows should be more than happy to run ubuntu...DOH !!!!

---

### Post by ba0bab on 2010-10-17
I FINALLY got it working! 

In the end, it was so simple... I was so focused on a very technical solution, that I hadn't thought of something very simple: I started a livesession with the normal desktop CD, and then made sure that all options about standby and such was just disabled - not with kernel parameters, not through the BIOS, but just plain and simple from within Ubuntus "power management" and "screensaver"...Jesus! 

Thanks for your suggestions though!

---

### Post by Rubi1200 on 2010-10-18
I am really pleased you got things sorted out :)

Sometimes, we miss the most obvious solutions because we expect it to be something complicated!

Enjoy!

---

