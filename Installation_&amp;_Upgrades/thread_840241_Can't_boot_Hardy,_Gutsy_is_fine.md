---
title: "Can't boot Hardy, Gutsy is fine"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by anandus on 2008-06-25
Hello!

I've been using Ubuntu on my laptop for one and a half year now, always worked quite well, no serious problems.

But for some reason I can't install Hardy.
I had a 7.10 installation, and when Hardy came out I upgraded my laptop and on reboot the laptop didn't boot properly.
no problem, a clean install is always better, so I downloaded the iso, MD5 checked it, burned it and booted my laptop.

And again it's stuck during boot, at about one-third of the bar.

When I use 'nosplash', I can see it's stuck when it's "setting up the system clock" or "Activating swapfile swap"
I used the 7.10-cd to remove all partitions on the hard disk, to no avail.

What's happening here?
Is the latest kernel not compatible with my laptop?
(Medion 40100)

---

### Post by PmDematagoda on 2008-06-25
Try booting the Live CD using a few options like "noapic" or "irq=default" and see if that makes any improvement.

---

### Post by anandus on 2008-06-25
Oh, I forgot to mention that! I tried noapic and some other options, to no avail :(

---

### Post by Michelexub on 2008-06-26
Hi anandus,
which laptop have you got?

I had the same problem with an Acer Aspire.
Frustrated, I decided to install (again) 7.10, then upgrade to 8.04.

Now everytime I use the CD (listen to a CD or to load some data) the laptop freezes.

I have posted on the forum and also in Launchpad, but for the moment I am still stuck.
But maybe you'll be more lucky!
M.

---

### Post by anandus on 2008-06-26
Hi Michelexub,

I have a Medion 40100, but if I'm not mistaken the Acer Aspires and the Medions often come from the same manufacturer.

(Also, to make the extra buttons to work, I need to install AcerHK-module, which also makes me think that it's nearly the same to some Acers)

---

### Post by Michelexub on 2008-06-27
> **anandus said:**
> to make the extra buttons to work, I need to install AcerHK-module

Never heard of that module, I will try it!

I guess that we should both check the CD-R/DVD and verify if they are the same.

I will try to post my findings in the next few days.

M.

---

### Post by anandus on 2008-06-27
Here are the specs for my laptop:
[http://home.conceptsfa.nl/~revdmeer/md40100/](http://home.conceptsfa.nl/~revdmeer/md40100/)

And here is a list of laptops for the Acer Hotkey driver:
[http://www.cakey.de/acerhk/](http://www.cakey.de/acerhk/)

---

### Post by Michelexub on 2008-07-06
> **anandus said:**
> 
And here is a list of laptops for the Acer Hotkey driver:
[http://www.cakey.de/acerhk/](http://www.cakey.de/acerhk/)

Hi. I finally had time to dig out the spec of my Acer.
Booting from Windows and using Belarc Advisor I have the following:
QSI CDRW/DVD SBW-242

Will try to find some drivers and install them.

I have downloaded the Acer Hotkey drivers, but cannot install them.
Guess that I have to learn a bit more about Linux before doing so.

M.

---

### Post by cipri_ on 2008-07-15
The solution is the following:
if you didn't install from the beginning with the additional option: acpi=off 
than you must add it in grub by hand.
In grub, at the "ubuntu entry" press "e", than go to the entry of the kernel, press "e" egain. At the end of the line append the following option: acpi=off
press enter
press "b"
Now Ubuntu should start without problems.
Now go to /boot/grub/.../menu.lst  and edit the lines where the kernel options are, and add at the end again "acpi=off"

Well, it works, but the price is.... for example , the status of the battery is not shown.

---

