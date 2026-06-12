---
title: "Unable to install Ubuntu, screen filled with blocks"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by Toasticuss on 2011-04-27
Anyone ever seen this? 

[[IMG]http://img860.imageshack.us/img860/5274/dsc02006d.jpg[/IMG]]("http://img860.imageshack.us/i/dsc02006d.jpg/")


This happened when I was trying to install Ubuntu 11.04 from a disc, when I boot from the USB or CD I create of Ubuntu it gets past the selection menu and then I get stuck at this screen, keyboard is completely frozen, no HDD activity light or anything.

This happened the same way when trying to install Ubuntu 10.10

This is an ASUS g60jx laptop, I would have assumed this was fixed by now, is their a special graphic mode I have to enter when installing?

---

### Post by mmad on 2011-04-27
My old desktop pc used to do things like that - I'm still not sure why because a later iteration fixed the problem. However I would suggest you use the text based alternate cd to get the installation done.

---

### Post by Toasticuss on 2011-04-27
> **mmad said:**
> My old desktop pc used to do things like that - I'm still not sure why because a later iteration fixed the problem. However I would suggest you use the text based alternate cd to get the installation done.

I've looked around on Google some more and someone said its a problem with the Nvidia 360m video adapter not getting the correct driver....

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2537900.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2537900.html)

He said use the xforcevesa kernel parameter before starting the install, I have no idea how to do that though.

Can you point me to the text based alternative install CD?


**Update:** I tried the disc again and pressed F6 and enabled ACPI=off for the boot mode, and I was able to get past the block of death screen, however, touchpad does not work so I navigated with the keyboard to install Ubuntu 11.04, its installing fine so far.

The F6 other options menu does not show up with the USB installation of 11.04.

**Update 2:** Install finished fine but it does not boot up correctly, it hangs at a black screen after showing this awful looking incomprehensible ubuntu boot screen. I guess the video drivers never installed....

Any ideas?

---

### Post by Quackers on 2011-04-27
Try the nomodeset boot option
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Bartleby Jones on 2011-04-27
I had the same problem. Same laptop, too. It's the videocard drivers, apparently. I installed 10.04, and that worked fine. Can't update to 10.10, though -- same driver problem.

How did you get F4 to do anything? I jammed on F4 in the 10.10 boot menu and nothing happened.

---

### Post by Toasticuss on 2011-04-27
> **Quackers said:**
> Try the nomodeset boot option
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thanks I'll give it a shot.

> **Bartleby Jones said:**
> I had the same problem. Same laptop, too. It's the videocard drivers, apparently. I installed 10.04, and that worked fine. Can't update to 10.10, though -- same driver problem.

How did you get F4 to do anything? I jammed on F4 in the 10.10 boot menu and nothing happened.

When you start booting from the disc, you'll see an icon at the bottom with a keyboard and a stick figure or something, press escape, it should bring up the normal install screen, Try Ubuntu, Install Ubuntu to HDD, Test Memory, etc, etc, otherwise it goes straight to the install....

At the bottom it gives you a list of options, F1 for language, F2 for keyboard language, **F6** is other options, it changes the install method, I apologize, for some odd reason I thought it was F4, it was F6 my mistake.


I've heard mixed reactions about 11.04, it looks like it took a big chunk of the Mac OSX operating systems GUI, I hope the full release allows customization of that, I can't stand to have a programs options and menus in the GUI of the operating system, but on the otherhand when I tried a live CD of it in safe mode it included all of the fixes and problems that were in 10.04 for the ASUS g60jx, the black light, and hibernation issues...

Now trying to install with nomodeset enabled, I'll let you know how it goes.

**Update 1:** Ubuntu install screen showed up fine, touchpad & wireless working, install is going fine...
[B]
Update 2: [/B]Install finished, removed media from tray, restarted, I saw a normal Ubuntu boot splash, then I saw the disconfigured broken screen, then it turned into a black screen, I heard the Ubuntu drum sound right after it though so I assume its sitting at the login screen and it failed to initialize the video driver, I think I remember seeing in one of the options on the install screen that I could install a video driver from somewhere, or is it possible to go into recovery mode and install the nvidia driver?

**Update 3: **Booted into Ubuntus recovery mode and chose the failsafe boot option to boot into low graphics mode. Checked out the additional drivers window under administration and it shows that the main propitiatory driver is installed and activated, I'm removing it to see if I can boot normally...

**Update 4: **Disabling the driver had no effect on the normal the Ubuntu boot ...still the same black screen....

[B]Update 5:

[/B][COLOR=SeaGreen][SIZE=4]SUCCESS!

[SIZE=2][COLOR=Black][[IMG]http://img849.imageshack.us/img849/2599/dsc02008b.th.jpg[/IMG]]("http://img849.imageshack.us/img849/2599/dsc02008b.jpg")

So I went back into Ubuntu's recovery mode, I choose the failsafeX option again, then on the small window I clicked reconfigure graphics options, it setup a new graphics config, then I clicked cancel to go back and booted into the low graphics mode, I checked the additional drivers to see what the status of the proprietary driver was and it was still deactivated, I clicked activate and it said it'll need to restart to complete. Instead of clicking restart I clicked shut down, the restart option said, restart and complete updates, On update 4 I tried restarting but I got stuck with a black screen with the HDD light on and it never shutdown so I had to do a cold shutdown.

So after shutting down with the driver activated, I turned the laptop on and let it boot normally into Ubuntu 11.04, it hung for a bit with the mouse cursor on the screen but eventually got to the desktop.

With that said, I assume this install procedure will work just fine for 10.10 users.

[COLOR=Red][B]$!@%!@!!@$!@$ I just accidentally saved over a huge installation guide I just wrote to install this properly, sorry guys =(

If any admin or mod could retrieve it that would be wonderful!
[/B][/COLOR] [/COLOR][/SIZE][/SIZE][/COLOR]

---

### Post by Bartleby Jones on 2011-04-28
Worked. Had to do the same cold restart/wait for things to pop up thing. Thanks.

Now to install 11 and do this again.

---

