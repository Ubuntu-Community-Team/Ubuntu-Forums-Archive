---
title: "Installation takes 500,000 years! ;)"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by catherine on 2006-06-11
I have been attempting to install Xubuntu 6.06 from the live cd onto a 5 year-old Toshiba laptop that has no other operating system (Windows 98 vanished mysteriously one day - the result of a virus I presume). The operating system loads without a hitch and functions perfectly, albeit a little slowly, as the cd drive is rather old. I have 128meg of RAM and the diskhas a capacity of 9.3gig.

When I go to install the operating system from the icon on the desktop however, it takes at least 20 minutes (if not more - it varies each time I do it) to go from screen to screen. In the first screen for example, loading all the language options that I can select from takes about 15 minutes, and sometimes it's hard to tell whether it will finish loading at all. It couldn't even load the window about partitioning at all: loading the program got to 48% over 2 hours, and then the system seemed to just freeze.

It seems to me that the problem is that the cd drive can't keep up with the installation program. Actually generating each window of the program can't be done in any reasonable time by my slow drive. The live cd interface requires too much interaction with the cd-rom.

Is there any other way in which I could install Xubuntu from a boot cd, without going through the live cd? I don't really care about dual booting - all I want is for Xubuntu to be my main operating system when I turn on my laptop.

Thanks so much for reading - I am totally new to all things Linux!

---

### Post by Ubuntuud on 2006-06-11
If you install as a server (you will need to download and burn another CD) you can "upgrade" it to xubuntu later.
Just follow the instructions of the CD (I haven't done it myself, but it can't be hard).
After that I assume you come into the "console", only text. Login. Then type "sudo apt-get install xubuntu-desktop". (Write this down if you can't remember it, you wont be able to access a browser). It will ask for a password, the root password, this is probably the same as your own, so enter yours. Answer yes on all questions.
This way it should work fine. (Although I think it'll still be slow.)

---

### Post by Ubuntuud on 2006-06-11
Oops.

---

### Post by sarhento_lobo on 2006-06-11
Hi Catherine, you may want to try the "alternate" version of the installer, which is text-based. At first run just leave all the settings at default and hopefully that would work. Also, you may want to take a look at the hardware compatibility list for Ubuntu.

Cheers,
sarhento_lobo

---

### Post by catherine on 2006-06-11
Thanks guys, I'm downloading the alternative installation disk image now. I'll let you know how it goes! Thanks for such speedy responses :)

---

### Post by glotz on 2006-06-11
I had a very similar experience, also on an older machine. It took forever for anything to happen. Once I actually got thru the process (must have taken hours) but then the hard disk wouldn't boot... I however never quite solved it but instead, since I'm on a very fast internet connection, installed the old 5.10 and used the package manager to upgrade to 6.06. I wonder if it would be possible to use the ubuntu 6.06 CD as repository for updating from an older version if you're on slow internet connection. I sincerely hope you get it working.

PS. One more thing that might be worth trying is try to make a rather large swap on the disk prior to rebooting the liveCD and installing. Then reboot and the liveCD will use the swap. For me gparted on the Ubuntu liveCD worked extremely slowly. There's a gparted liveCD available at the gparted website, dunno if it'd be any faster. I think it was only a 50 megs download or something like that...

---

### Post by PriceChild on 2006-06-11
Yup, i definately reccomend [sarhento_lobo]("http://ubuntuforums.org/member.php?u=81105") more than Ubuntuud as his will get you straight into a usable gui.

xubuntu uses the xfce desktop, which is much lighter than ubuntu (GNOME) meaning it will run faster on older systems, so you should probs get the xubuntu alternate disk rather than the ubuntu one.

---

### Post by glotz on 2006-06-11
Why is the installer so incredibly heavy? I'm on ubuntu dapper and it's working relatively smoothly on my speedy 450 MHz pentium III with whopping 192 megs of ram. The installer off the liveCD was trying to kill me and almost managed to do it. Never got it working.

---

### Post by catherine on 2006-06-11
Well, the text installer is about 60% of the way through, and it looks like all will work (touch wood!). Thanks again for your help. It does look like the text installer is the way to go for low-end machines. :D

---

### Post by catherine on 2006-06-11
Update: I spoke too soon :-( After what looked to be a successful installation, I booted the laptop up only to receive the same old message as ever: "Operating system could not be found." This suggests to me that something is seriously wrong with this laptop!

The only thing that seemed to wrong/didn't install was that the DHCP network configuration failed. But I doubt this has anything to do with the laptop being at a loss as to what to do after the BIOS.

---

