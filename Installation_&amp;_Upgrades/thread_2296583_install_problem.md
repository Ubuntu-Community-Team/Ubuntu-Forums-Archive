---
title: "install problem"
date: 2015-09-27
forum: Installation &amp; Upgrades
---

### Post by afrancis-ozonline on 2015-09-27
I wanted to install Ubuntu alongside windows on a laptop, so I created a Bootable USB Stick using a windows program called Rufus and a 15.04 iso.
When I boot from usb a white rectangle fllashes up momentarily and then the following message appears:
[ 0.460941 Ignoring BGRT: Invalid Status 0 (expected 1)
[ 11.083721 ]ACPI Probe failed. Starting version 219

Then that's it nothing else happens.
Any Ideas?

---

### Post by sandyd on 2015-09-27
Could be that Ubuntu is having trouble with the graphical drivers

At the Ubuntu grub menu, press e.

Move down to where it says "quiet splash".
Using the keyboard, remove the word "splash", and replace with "nomodeset". No quotes are needed.

Press control+x to boot.

---

### Post by afrancis-ozonline on 2015-09-27
There is no grub menu, just the message I mentioned.

---

### Post by sandyd on 2015-09-27
I'm unfamiliar with rufus, so this might be a shot in the dark.

When you boot up, do you see the purple Ubuntu boot screen that allows you to choose a language, and whether or not you want to install or try Ubuntu?

If so, press tab, and replace "splash" with "nomodeset"

---

### Post by Bucky Ball on 2015-09-28
*Thread moved to **Installation & Upgrades**.*

---

### Post by sudodus on 2015-09-28
Is the computer running in UEFI mode or in classical BIOS mode?

When you know, you can add some **boot options** according to the following tips

**nomodeset** is good if the graphics is the problem, **acpi=off** might be good in this case. You can add several boot options at the same time.

See these links

For syslinux boot (in BIOS mode)
[BootOptions](https://help.ubuntu.com/community/BootOptions)

For grub boot (in UEFI mode and BIOS mode)
[Editing the GRUB 2 Menu During Boot](https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot)
[Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

See the section about **GRUB_CMDLINE_LINUX**

---

### Post by afrancis-ozonline on 2015-09-28
No there is no purple screen just a dark screen with the message I posted.

---

### Post by sudodus on 2015-09-28
It is time for some more details for trouble-shooting.

- Have you checked with md5sum, that the downloaded iso file is good?

- Did you try with boot options as I suggested in post #6?

- Please specify your computer

. Brand name and model
. CPU
. RAM (size)
. graphics chip/card
. wifi chip/card

It will make it easier for us to give good advice.

---

### Post by afrancis-ozonline on 2015-09-28
Became frustrated with this approach, so I formatted the usb stick downloaded the iso again and tried to make a bootable usb stick. However, I have tried using unetbootin - Startup Disk Creator and usb-creator and have had no success at all.
Have no idea what to do next.

---

### Post by sudodus on 2015-09-29
If you tell us about your computer, it will be easier to help. Otherwise we can only guess or give very general advice.

---

### Post by afrancis-ozonline on 2015-09-30
I have found that this is not just an Ubuntu problem. I also went through the whole procedure in Windows 10 and came up with the same result. (The same message and the same no boot)

---

### Post by afrancis-ozonline on 2015-09-30
The plot thickens. I have tried to install from usb on another  laptop I have access to and it boots and gives me the choice of trying or installing Ubuntu. However, only the try option seems to work, when I try to install the first screen asks for a choice of language then the next screen is Wireless, when I click on "continue" the button goes grey and the the following message comes up: ' The installer encountered an unrecoverable error. A desktop session will now be run so you may investigate the problem or try installing again"
Then it reverts back to the "Try" screen.
Don't know what to do next.

---

### Post by Bucky Ball on 2015-09-30
Well, the kernel probably doesn't have the drivers for your wireless device. Try plugging in an ethernet cable or not downloading updates and third-party drivers during the install. You don't need to do that. You can add them later.

---

### Post by afrancis-ozonline on 2015-10-01
When I first had the problem I had clicked on wireless network, so this morning I plugged in an ethernet cable but still had the same result.

---

### Post by Bucky Ball on 2015-10-01
Are you ticking the boxes to install third-party software and updates as you install? If so, don't, and try that.

---

### Post by afrancis-ozonline on 2015-10-02
Tried that no difference.

---

### Post by sudodus on 2015-10-02
- Have you checked with md5sum, that the downloaded iso file is good?

- Did you try with boot options as I suggested in post #6?

And it is time for some more details for trouble-shooting:

- Please specify your computer :-)

. Brand name and model
. CPU
. RAM (size)
. graphics chip/card
. wifi chip/card

It will make it easier for us to give good advice. (Otherwise we can only guess or give very general advice.)

---

### Post by afrancis-ozonline on 2015-10-03
I am very grateful for your advice regarding this problem. However , in regard to the computer  there is not much point in giving you computer details because
I am looking after updates for 7 laptops belonging to a Seniors Computer Group and I just thought I would put Ubuntu on one of them to show the group that there is a very viable alternative to Windows. I will attempt to check that the iso is OK and also try again to change that Grub menu as you previously mentioned.
THANKS.

---

### Post by sudodus on 2015-10-03
Computers differ a lot. Many computers work with Ubuntu without any problems. But others have some hardware component, that needs special attention. This is when it is useful with ***boot options*** as described in post #6, and maybe later to install a proprietary driver.

If the computers are middle-age it is often rather easy to make them work with standard Ubuntu or a flavour of Ubuntu. If they are brand new, there is one set of problems (mainly that there are not drivers for some of the hardware yet). If they are old, there is another set of problems (mainly that drivers for some of the hardware may be dropped, and that some features used by modern web sites cannot run in the old hardware). Some old computers work well will a medium light desktop environment like Xubuntu and Ubuntu MATE, some need the ultra light desktop environment of Lubuntu. These flavours of Ubuntu have the same Ubuntu program packages under the hood, and they make it possible to keep old hardware useful.

I suggest that you make a crude list of the hardware in those 7 laptops, or at least make a list of brand name and model. I think some of them should be easy to run with Ubuntu, but some of them need a lighter desktop environment, and some of them need boot options or proprietary drivers. Finally some computer may to too old to work with a modern linux system.

---

