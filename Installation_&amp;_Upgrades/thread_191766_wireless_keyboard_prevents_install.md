---
title: "wireless keyboard prevents install"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by scratching my noggin on 2006-06-07
Is there a way to get the drivers for my logitech wireless keyboard to load in initial boot? At present the Cd takes me to having to press 'Enter' to continue install, and I cannot because the keyboard is non operative at this stage. Is their an automatic boot program that will allow the install to proceed? :confused:

---

### Post by nanotube on 2006-06-08
[QUOTE=scratching my noggin]Is there a way to get the drivers for my logitech wireless keyboard to load in initial boot? At present the Cd takes me to having to press 'Enter' to continue install, and I cannot because the keyboard is non operative at this stage. Is their an automatic boot program that will allow the install to proceed? :confused:[/QUOTE]
seems it might be easiest to just plug in a wired keyboard during install, and then worry about getting the wireless kb drivers on after it is installed. it might also be prudent to check and see if the drivers for your wireless keyboard are available for linux, because if they are not, then you are just out of luck on this one.

---

### Post by scratching my noggin on 2006-06-08
Hmmm, I thought this might be the case. Can you tell me where to go to find out if there are drivers available for my KB? U might have guessed I am very new to Linux. :(  Thanks for the answer though.

---

### Post by nanotube on 2006-06-08
[QUOTE=scratching my noggin]Hmmm, I thought this might be the case. Can you tell me where to go to find out if there are drivers available for my KB? U might have guessed I am very new to Linux. :(  Thanks for the answer though.[/QUOTE]
well, what i would do is take the model number of my keyboard, and search for it +linux on google, and see what comes up. ;)

also, there is a hardware compatibility list somewhere on the ubuntu wiki, you can look through that - but that is not necessarily exhaustive.

you can also search for "wireless keyboard" on this forum, and see if anything useful comes up.

as you can guess, i don't have a wireless keyboard myself, so i don't know any specifics. i can just tell you where to look. :)

the easiest way to find out is to get a wired keyboard, boot the livecd with it, then plug in your fancy wireless keyboard, and see if it is autodetected.

---

### Post by mozetti on 2006-06-08
One thing that worked for me was to go into my BIOS and turn on USB Legacy support for keyboard and mouse. I had the same issue when I installed Breezy, and I couldn't even enter my BIOS setup because the wireless keyboard wasn't recognized.

Go into your BIOS (hook up a wired keyboad, if necessary), look for the USB Legacy Support option and use the Keyboard and Mouse setting to see if that fixed it.

---

