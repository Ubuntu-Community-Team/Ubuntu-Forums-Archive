---
title: "Splash screen doesn't appear on Intel Chipset under Feisty"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by cccnutty on 2007-06-08
The Ubuntu splash screen doesn't appear during the loading process for my install.  The computer boots fine and the GRUB displays for my options to boot, and then it just sits at a black screen where the splash should be before it brings up the GNOME interface.  This isn't a major problem since everything else seems to work fine, but I would like to know if anyone else has had this problem and if there is a fix.

The computer is an IBM ThinkCentre A30 8198-32U, that has the Intel 845G chipset.

Thank you for any information you may have.

---

### Post by stami on 2007-06-08
Hi,
I don't think you can resolve your problem unless you install Ubuntu. If your live cd boot up, install Ubuntu and then install packages for your chipset. If I don't get wrong after installing packages for your chipset you have to use vesa driver in you xorg.conf. I played some time ago with a acer travelmate with a similar chipset (it seem to me i945), and it didn't get the right resolution until I installed the package 915resolution, but I don't know if you can use this package also for your hardware.

Bye.

---

### Post by cccnutty on 2007-06-08
Sorry, but I probably should have been more specific with the problem, I booted off the disk, no splash and it came up horrible resolution (640x480).  I installed and the same with the first boot.  I then found and installed the new package for the intel chipset and it worked so I have a good resolution, but when the computer is starting there is still no splash.

The only problem this gives me is that my impatient desktop users in the company want to constantly mash the power button when the screen goes black for more than five seconds so I am getting lots of support calls.  I plan on disabling the splash so there will at least be the screens of text for them to watch while it starts, but it would be nice if it was there.

---

### Post by merlinus on 2007-06-08
Can you post your /boot/grub/menu.lst  

or do you not use grub?

-merlin

---

### Post by bobsp on 2007-06-08
I am getting the same issue on a DELL Dimension 2350, which also has the 845 video chipset. In my case, however, the resolution of the screen using the live CD was ok (1024 x 768) and showed the splash at startup. On install of Feisty, everything was great until I pressed the restart button to re-boot off the installed OS - the screen went blank for the duration of the shutdown. On re-boot, the GRUB screen shows, followed by "starting.." then blank until the login window appears.  Are restricted drivers needed for this Intel chip?

Cheers,
Bob.

---

### Post by wrongo on 2007-06-08
following instructions located at:

[http://ubuntuforums.org/showthread.php?t=399913&highlight=dell+inspiron+E1705](http://ubuntuforums.org/showthread.php?t=399913&highlight=dell+inspiron+E1705)

specifically under the INITIAL INSTALL & PREP, instruction number 2...

-----------

Typing this message USING resulting ubuntu operating system (apparently running live from the CD)

ISSUE: THERE IS NO INSTALL BUTTON ON MY DESKTOP

HOW DO I INSTALL UBUNTU WITHOUT AN INSTALLATION BUTTON ON MY DESKTOP?

---

