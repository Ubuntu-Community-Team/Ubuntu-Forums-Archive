---
title: "Edgy blank screen install help"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Meshuggah27 on 2007-02-05
I just installed ubuntu edgy 6.10 through the alternate iso disk in text mode and everything installed fine

Now when i restart my computer,  After the bios screens and everything,  The computer just sits at a black screen and i cant do anything

I think it has something to do with my video card

My PC Specs are

Gigabyte K8N 939 Mobo (Nforce4)
Athlon 64 3200+
ATI Radeon x800GTO
2GB Kingston HyperX Ram
20gb WD HDD (IDE)

Hope someone can help! :(


I also cant get into recovery mode,  I dont know whats wrong.  If i could get to a console i could probably get it running.

---

### Post by Meshuggah27 on 2007-02-05
bump

help please! :'(

---

### Post by Dylnuge on 2007-02-05
Can you boot of the CD?

---

### Post by Meshuggah27 on 2007-02-05
I can boot off the cd if i do this.

Hit f4, set VGA to 1024x768 (16)

Then highlight safe visual mode or whatever and in the boot options, type

irqpoll pci=noacpi noapic nolapic acpi=off

Then it loads that ubuntu screen, gets to the end of the progress bar,  then i get the mighty xserver error.  I hit ok on all the errors then it goes to a blank screen

Then i hit cntrl+alt+f2 to get into console.

THEN i type

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

and thats how i get the live disc to boot so i can install ubuntu.  Then when ubuntu is done installing and it restarts my PC,  After the bios runs its checks and **** it just hangs at a black screen.  I left it on overnight and nothing happened.  I really hope this is all the information you need because its all i have.  Thanks!

---

### Post by Meshuggah27 on 2007-02-05
bump :(

---

### Post by Mr_Shush18 on 2007-02-07
I had the same problem with me X800xl (X server error, black screen)
I had to do basicly the same thing with the Live CD (get to a consule and install the fglrx drivers) and then again after the install.  Try installing them a second time and see what happens.

---

### Post by eapache on 2007-02-07
I had the same problem with a slightly different video card. This is the response I got from aberry5555

> This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line.

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!

I'm assuming that you want to do this to boot with the graphical liveCD, then mount your harddrive and make the same config changes to the xorg.conf file on your hard-drive. Hopefully this will solve the problem.

---

### Post by seeingwhite on 2007-03-05
> **eapache said:**
> I had the same problem with a slightly different video card. This is the response I got from aberry5555

[I][B]This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line.

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!
[/B][/I]
I'm assuming that you want to do this to boot with the graphical liveCD, then mount your harddrive and make the same config changes to the xorg.conf file on your hard-drive. Hopefully this will solve the problem.

Sorry to resurrect this old thread, but I wanted to bump this because I had the exact some problem and this FIXED it! :KS  I have an ATI 9800 Pro, and i had to change it to "vesa" for it to work.  FYI, when I tried "radeon", I had the same blank screen.  Thanks for the help with this.

---

