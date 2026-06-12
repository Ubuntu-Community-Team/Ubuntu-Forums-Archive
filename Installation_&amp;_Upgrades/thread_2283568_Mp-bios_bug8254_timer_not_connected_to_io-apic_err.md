---
title: "Mp-bios bug:8254 timer not connected to io-apic error on 14.04.2 install"
date: 2015-06-22
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2015-06-22
this appears to be a very common problem but one which does not seem to have a clear solution.

I am trying to install 14.04.2 (ubuntu-14.04.2-desktop-i386) on a Dell Inspiron 1501 running Windows XP.
the usb install is failing on the above error (and then the screen goes all coloured stripes)

I have updated the Bios (which seemed to be one suggestion) but it still fails.

can anyone advise on next steps?

(I've rarely failed in a Ubuntu install and I don't want to start now.)

thanks

Peter

---

### Post by MAFoElffen on 2015-06-23
What you are describing sounds to me as being graphics related. That laptop has an early (AMD) ATI Xpress Radeon 1150 256MB HyperMemory (Integrated graphics) GPU... The default video on the install and first boot does not always do well recognizing Radeon or Nvideo without helping it/pointing it in the right direction. Before you can install the OS and intall / configure a graphics driver.

Until you can... On the boot, add 
```

radeon.modeset=0 noapic

```
... to the end of the Linux boot line as a boot option. If you have questons on how to do that, either ask or look at my sticky in the link in my sig line.

---

### Post by pjstock on 2015-06-23
I updated the video drivers (you didn't suggest that but what the heck) but I get the same problem.

Indeed, I do not know how to add that code to the Linux Boot Line. Or at least I do not know where I would add that.

(I tried reading the Sticky as suggested, but got lost in the detail.)

Can you direct me a little further?

Many thanks

Peter

Hmm, I just guessed and tried adding that code to the Syslinux.cfg file, 
but the usb install still failed.

so to which file am I adding this extra "**radeon.modeset=0 noapic**" code?

---

### Post by MAFoElffen on 2015-06-24
Not to a file...

Post #3 would help you... (The following is from memory, so bear with me)

Booting onto the live Image USB, it depends on how you created the LiveUSB image.

If from unetlogin, as it boots, arrow the menu to the option, press tab... go down to the line starting with "linux" go to the end of the line and add... "radeon.modeset=0 noapic" (without the quotes) Press <cntrl><x>

If other and it looks like the boot from LiveCD, on boot press the left shift key. When at the initial purplish panel with the keyboard/person icon at the bottom, Press <enter>. At the language selection press <enter>. You will be at the Advanced Install Menu. Press <F6>. Arrow down to noapic, press the <spacebar>, then <esc>. You should see a new line displayed under the main menu. Arrow right until just after the text "noapic" and type in "radeon.modeset=0" (no quotes, these quotes are just for you...). Press <Enter> to boot with those options.

---

### Post by pjstock on 2015-06-24
THAT was amazing!
those boot line mods did the trick perfectly (though I guess I am the only one surprised here)
many thanks
Peter

---

### Post by Ifch0o1 on 2015-11-12
My motherboard PCI-E slots not working, so I using an very old PCI video card (S3 Trio64V2)

I gettin' the same message "MP-BIOS bug 8254..." and I have very issues with the graphics.
Also I cannot login into Xubuntu xfce-seesion (The graphical login screen is half rendered and when I try to login - the monitor turning off and on again returning me to back to the half rendered login screen).
I can access the terminals.

Now I am using the same HDD and the same xubuntu installed on different PC with (nv6200) and everything working fine.

What option I need to use to disable the gaphic driver for this video card?

---

### Post by pjstock on 2015-11-12
I am not sure that I can help. this was a while ago. I basically just followed the directions I received here and it cleared it up. But if you are having trouble getting to Terminal because the display is messed up, you might have to connect to an external monitor until you can get your laptop video cleaned up. I expect that's what I did. good luck. peter

---

### Post by will109 on 2016-06-12
> **MAFoElffen said:**
> What you are describing sounds to me as being graphics related. That laptop has an early (AMD) ATI Xpress Radeon 1150 256MB HyperMemory (Integrated graphics) GPU... The default video on the install and first boot does not always do well recognizing Radeon or Nvideo without helping it/pointing it in the right direction. Before you can install the OS and intall / configure a graphics driver.

Until you can... On the boot, add 
```

radeon.modeset=0 noapic

```
... to the end of the Linux boot line as a boot option. If you have questons on how to do that, either ask or look at my sticky in the link in my sig line.


Hello, sorry to resurrect an old thread but I have the same issue as above and don't understand where I add this code? Are you able to point me in the right direction? Many thanks indeed!

---

