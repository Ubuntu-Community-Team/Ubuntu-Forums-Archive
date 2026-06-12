---
title: "Installation difficulties on ancient old Sharp notebook"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by John the Fish on 2011-02-24
First, some background. I have an ancient Sharp notebook (PC-FS2518, AMD Athalon 1900+, 30G hard drive, 1G main/video RAM, Insyde Software SCU BIOS). It used to run XP, so to revitalise it and make it more usable I have been trying to get EasyPeasy 1.6 running on it. The idea is to have something simple my 82-year old Mother-in-law can use to browse the web and write the occasional email or letter.

I already have a successful EasyPeasy system running on an EeePC and like the simplicity and speed. On the EeePC it runs perfectly. 

The Sharp's USB/BIOS is so ancient it can't boot from USB, so I did a live install from an iso DVD. To install I had to F6 and select all of:
[LIST]
[*]acpi=off
[*]noapic
[*]nolapic
[*]nodmraid
[*]nomodeset
[/LIST]

(I have experimented with lesser combinations)

The CD/DVD drive is slow and it took about 18 hours to install. From the live iso DVD and during the install, any program launched would get repeatedly minimised. But the system was so slow with the iso on DVD that I had time to do stuff before the window I was working in shank away and had to be clicked to get it back again from the taskbar.

All OK, I was expecting it to be slow with everything on such an ancient DVD drive. 

Then I came to booting the newly installed EasyPeasy on the Sharp. I needed to  edit Grub and select all the same options again to get EasyPeasy to load (acpi=off noapic nolapic nodmraid nomodeset).

Now I have a couple of problems I need help to solve:

[LIST=1]
[*]Multiple random problem messages including OAFIID:GNOME_GoHome, _IndicatorApplet, _ClockApplet, _NotificationAreaApplet (and others), typically 3 or 4 of them at random on any start-up.


[*]Any application or applet clicked on flashes up and is almost instantly and repeatedly minimised so I barely have time to read it (pretty much the same as during the install from iso DVD, but faster). When I click on the task bar icons, they flash up and get minimised again. I can't even get a terminal window stable enough to reliably enter any commands.
[/LIST]

Any suggestions (short of repeating the 18 hour install) would be appreciated.

Thanks

John

---

