---
title: "Installation login problem"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by Splatmantom on 2011-01-16
[SIZE=3][FONT=Arial]Hello there.

I recently decided to have  a go at running kubuntu on my desktop PC after building it and installing windows 7 Home Edition on the primary hard disk.

Recently i bought a second hard disk and moved all my games/music/pictures onto it. This left me with a lot of free space on the hard drive with windows installed on it.

So i decided to partition that drive, i could only shrink the windows installation down to around 316gb/465gb (bit miffed as there is only currently 61GB of data on the windows drive). That still left me with 148gb to stick kubuntu onto.

I decided to go for the full installation option and downloaded a disc image, burned it onto a disc and then booted my system from the dvd drive. Unfortunately whenever i hit the install kubuntu option it goes through to the loading screen and then this error message pops up after around 10 seconds:

[I](process:374) GLib - WARNING **: getpwuid_r(): failed due to unknown user_id (0)

[/I]nothing else happens after that so i have to crash the system and reboot it to windows. I was wondering if there is something blindingly obvious that i'm missing, such as the editing of a configuration file, or a way of setting a user id and password without ever getting into kubuntu in the first place.

I have already tried ubuntu itself through wubi, but on further reading i thought i'd prefer the KDE environment over GNOME

Please excuse my noobiness when it comes to kubuntu/linux, but i had to ask somewhere, and this would seem to be the best place to ask.  
[/FONT][/SIZE]

---

### Post by kn0w-b1nary on 2011-01-16
i've run into this problem before on computers w/ either crappy graphics cards or very low amounts of RAM.

You could try using the alternate install CD, but if you have less than 1 gig of RAM, i'd recommend that you give up on KDE :( It's loaded with features and eye candy, but that makes it pretty bloated.

Hope this helps!

---

### Post by bcbc on 2011-01-16
Boot from the DVD again, but hit the space bar when you see the little keyboard icon (and man icon) at the bottom centre. This will give you a menu with more options - select Check disk for errors.

---

### Post by Splatmantom on 2011-01-16
Thanks for the quick respnse kn0w-b1nary, but i have 4 gigs of ddr3 ram running on this computer at 1333mhz with a sapphire hd4890 graphics card, so i'll keep plugging away at kubuntu unless the situation becomes hopeless. Thanks for the fast response though :)

---

### Post by Splatmantom on 2011-01-16
i'll give that a shot bcbc, but i don't think i've ever seen the icons that you are talking about. However, i will have to check the disk for errors as you say, should've done that the first time really.

---

### Post by bcbc on 2011-01-16
If that all checks out - you might want to try some boot up workarounds - try 'nomodeset' ([http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)). There have been problems since 10.04 with many graphics cards at boot up.

---

### Post by kn0w-b1nary on 2011-01-16
> **Splatmantom said:**
> Thanks for the quick respnse kn0w-b1nary, but i have 4 gigs of ddr3 ram running on this computer at 1333mhz with a sapphire hd4890 graphics card, so i'll keep plugging away at kubuntu unless the situation becomes hopeless. Thanks for the fast response though :)

you're welcome. :)

---

### Post by Splatmantom on 2011-01-16
unfortunately there seemed to be a single error on the disc, so i re-burned the disc, this time making windows verify that it had burned correctly. This then threw up "Error Code: 000x80004005" or something very similar to thta, so i have decided to no longer pursue installing kubuntu and have opted for plain ol' Ubuntu. Thanks to all that have tried to help me.

Unfortunately attempting to boot in nomodeset didn't help me either bcbc, it just made the kernel panic :s

---

