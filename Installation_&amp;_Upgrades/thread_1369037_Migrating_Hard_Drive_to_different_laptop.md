---
title: "Migrating Hard Drive to different laptop"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by minimustangs on 2009-12-31
Recently I seem to have had very serious main board failures on the laptop I was running Ubuntu on. Such is the way it is. I really liked the Ubuntu platform, but can't commit any of my desktops to that just yet. I do have another laptop which I still must run M/S OS on due to business reasons. 

HOWEVER....

Both systems used the same IDE interface for the hard drives. I realize that I can't just take the Ubuntu configured drive, plug it into a totally different laptop and expect it to work. What I was thinking though is that I could use the 9.04 install CD to do a Repair Install ( I think that's an option ) and reconfigure that installation to work with the new laptop hardware. The only problem I see with that is I did upgrade to 9.10...

The 2nd part of this question...

Either way -  repair install or full blown wipe and fresh install, I will have a drive to install Ubuntu on. Because I need the M/S OS as a dedicated option, I would consider removing the internal hard drive to install the Ubuntu loaded drive. The other option is using the Ubuntu drive via USB or maybe even firewire, since this laptop support those.

I suppose I should just try it and see, but what would be considered the best way to load Ubuntu onto the 2nd drive? Should I install Ubuntuon to it as an internal, as a 2nd USB/Firewire drive, or as the only drive on USB/Firewire.

Thanks for your suggestions...

---

### Post by dandnsmith on 2009-12-31
Linux systems, such as Ubuntu, are much more flexible than M/S stuff - you might be pleasantly surprised if you did try the HDD in the other laptop without any mods (the most likely problem area is the screen, as these are, typically, much more idiosyncratic than the rest of the hardware).

I wouldn't, as a personal preference, like to have to swap HDDs to change OS.
The fact that you say you need to keep M/S stuff available suggests that you go for a dual-boot system using the second HDD as  USB-connected.

The tricky part of the operation is sorting out the dual booting, to leave it so that it will still boot with the 2nd HDD disconnected.
I'd back myself to sort it out on my own system - but you may not have the relevant experience, or the tools, to do it. I think you'd probably already have tried it if you felt thoroughly competent, and, unfortunately, I don't think I could give a tutorial which would lead to guaranteed success.

---

### Post by minimustangs on 2009-12-31
I usually am the "tutor" not the student. One of my first avenues of research is to ask the relevant community what their experience is/was with something I may not have tackled before. 

Changing out h/w is no more concerning for me as would be making toast..laff. I was mostly looking for opinions on which avenue to investigate first. I'm not sure how the BIOS was set to enumerate the disks, so I don't know if there will be issues translating between M/S OS'es or Linux OS'es, one of the reasons that dual-booting fails most of the time. 

I was extremly reluctant to have to use this laptop for anything other than the intended use, it's that important. Isolating software and environments by using 2 separate drives solves my concerns, unconventional and awkward as it might be.

---

### Post by cnja on 2009-12-31
I just went from a Dell latitude CPx-J to a Dell Latitude D610, the only problem that I ran into was the wireless network card... on the CPx i was using a orinoco-cs and on the D610 it has a broadcom 4309 on board.  after downloading the windows drivers for the 4309 and using NDISWRAPPER, everything is up and running.

---

### Post by minimustangs on 2009-12-31
Dell to Dell might not be so bad, I'm going from ACER to Toshiba. At least they both use ATI video cards, although the ACER is an AMD and the Toshiba is an Intel...

Let the fun begin...

---

### Post by minimustangs on 2009-12-31
Well...

I just did the switch ACER HDD to TOSHIBA. I'm happy to report that I didn't even have to repair the install...everything JUST WORKS. The geek in me wants to scream "How Awesome is that!", the adult in me says "well that's better"....

---

### Post by dandnsmith on 2010-01-01
I'm glad to see my surmise confirmed.

---

### Post by Bartender on 2010-01-01
That's one of the things I love about open source.  

Try to swap a HDD with Windows installed.  Windows will go, "You must be a pirate.  Here's your BSOD".

Linux goes, "Hey, these parts aren't the same as last time, but we'll give it a shot."

---

### Post by minimustangs on 2010-01-01
I've managed to replace a main board on an XP installed system -  which sort of amounts to the same thing I've done here. Do I want to do that again? Do I ever recommend it? Not on your life. Re-activation was just one of the PITA's. 

I had a feeling that switching the Ubuntu-loaded drive would work, but had to ask about the perils just the same. My biggest concern were the ATI drivers. Since both laptops used ATI chipsets I think I managed to reduce the impact. Whatever, excellent.

---

