---
title: "HELP!!!! acer aspire 5735 laptop"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by npm1 on 2010-02-25
hello poeple,
 i have an ACER ASPIRE 5735 LAPTOP with: 
4GB DDR2 RAM,
A MOBILE INTEL GRAPHICS MEDIA ACCELERATOR 4500MHD GRAPHICS,
15.6 HD ACER CINECRYSTAL LCD,
INTEL CORE 2 DUO PROCESSOR T6400(2.0 GHZ,800MHZFSB,2MB L2 CACHE),
500GB HARD DRIVE,
DVD-SUPER MULTI DL,
IN-BUILT CRYSTAL EYE WEBCAM AND
802.11A/B/G/DRAFT-N$ WLAN.
[IMG]http://ubuntuforums.org/images/smilies/star.png[/IMG]
it currently has 32bt vista home premium installed with the hidden partition that acer provides i.e. for resseting to factory settings.
----------------------------------------------------------------
when i attempt to install the 64bt ubuntu 9.10 on this laptop,
the menu where i choose the language is produced-
 i choose english (uk),

then i choose the next menu option-
"try without making any changes".... the splash with the light shining on the ubunu logo props, then the screens turn BLACK.

i come out of this by pressing down on the laptops off butten then...[IMG]http://ubuntuforums.org/images/smilies/confused.gif[/IMG]
do same again, attempting the option- "install ubuntu to hard drive"
the same BLACK SCREEN comes up...... please help-------[IMG]http://ubuntuforums.org/images/smilies/confused.gif[/IMG]

by the way, i have been into ubuntu for 2 years thus familier with the terminal and man command

---

### Post by khelben1979 on 2010-02-25
I think the kernel don't like your hardware. Have you tried installing an older version of Ubuntu?

---

### Post by npm1 on 2010-02-25
i haven't tried any other ubuntu distro
would the older versions of ubuntu come in 64bt
whats wrong with my laptops hardware

---

### Post by khelben1979 on 2010-02-25
If your hardware works well with Windows there's nothing wrong with it. The problem is that newer hardware has not always been implemented in the Linux kernel, depending on what hardware which is supported inside the Linux kernel.

So there's probably nothing wrong with your computer. And yes, older versions of Ubuntu support 64 bit.

---

### Post by npm1 on 2010-02-25
once i've installed the 64bt of ubuntu say 8.04 would i be able to update to 9.10, then downgrade the kernal

---

### Post by khelben1979 on 2010-02-25
At the time you upgrade the Linux distro, a new Linux kernel will be installed, so I'm not sure if it's the solution you are looking for.

The most important thing if you decide to use an older version of Ubuntu is whether Ubuntu works on your hardware or not. If it doesn't, you might be forced to change to another Linux distribution if none of them seem to work out to get something working.

As an advanced Linux user you have the possibility to compile your own Linux kernel, but for now I think you need to use what is provided, and if it doesn't work, then you must decide if you want to go for another Linux distribution or not.

---

### Post by dE_logics on 2010-02-25
Install 9.04 first.

I got a feeling the disk is not well.

Do an md5 of the downloaded image, if the text matches, reburn it to a RW (preferably) at slow speed and do the check disk option in the boot menu.


You should have asked the vendor if the Laptop is Linux compatible.

I'm getting a bad impression over Acer...they are VERY Linux incompatible.

They use an alps touchpad to top it off -- the worst touchpad manufacturers. It causes more issues in Linux.

---

### Post by npm1 on 2010-02-25
cheers peeps

---

