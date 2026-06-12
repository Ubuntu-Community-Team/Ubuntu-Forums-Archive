---
title: "Ubuntu-Server 20.04.3 immediately crashes after installer loads"
date: 2021-12-27
forum: Installation &amp; Upgrades
---

### Post by adriele on 2021-12-27
[COLOR=#232629][FONT=-apple-system]TL;DR: Ubuntu-Server immediately crashes after installer loads, I'm in desperate need for some help, details below

Info: Ive also posted this here: [/FONT][/COLOR]https://askubuntu.com/questions/1383964/ubuntu-server-20-04-3-immediately-crashes-after-installer-loads[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]So I need an Ubuntu-Server rather urgently and was given some random hardware that was lying around. It's a Dell Power Edge 230 with only 8GB of RAM, and a 3Ghz Quad core. I haven't yet figured out what the RAID config is or what drives are installed (if you have any pointers on what information to look for and how, feel free to share).

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Here is what I've done so far: Used this tutorial to make a bootable Flash-Drive, than plugged it into the rear USB port of my Server, pressed F11 to load boot Manager, selected One-Shot BIOS Boot menu, selected USB-Drive;

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Now onto the the Problem, when I select the drive it goes on to boot Ubuntu, starting with this whole screen in the dark purple-ish ubuntu color and a logo of a keyboard, an arrow and a person (wich I've never seen before), then it loads the regular stuff (cloud init etc) and then gives me the select language screen, after a few seconds (no matter if I interact or not) it displays a message saying that an unknown error occurred

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Ive tried with different USB-Drives same result

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]If you need some more info, let me know

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I would really appreciate some advice, or what you have done if you've had this problem

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]TL;DR: Ubuntu-Server immediately crashes after installer loads, I'm in desperate need for some help[/FONT][/COLOR]

---

### Post by MAFoElffen on 2021-12-28
> **adriele said:**
> [COLOR=#232629][FONT=-apple-system]Here is what I've done so far: Used this tutorial to make a bootable Flash-Drive, than plugged it into the rear USB port of my Server, pressed F11 to load boot Manager, selected One-Shot BIOS Boot menu, selected USB-Drive;

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Now onto the the Problem, when I select the drive it goes on to boot Ubuntu, starting with this whole screen in the dark purple-ish ubuntu color and a logo of a keyboard, an arrow and a person (wich I've never seen before), then it loads the regular stuff (cloud init etc) and then gives me the select language screen, after a few seconds (no matter if I interact or not) it displays a message saying that an unknown error occurred

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Ive tried with different USB-Drives same result

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]If you need some more info, let me know[/FONT][/COLOR]
Which tutorial did you follow? There was no link or specific mention of... Also which boot mode is set? Legacy CSM, or UEFI?

Which Perc Card model is in it? What kind of drives and how are the drives setup in the PERC Card?

Did you verify the downloaded image with MD5SUM to verify that you have a good image?

Because from what you described, it sounds like it was booting as CSM/Legacy boot, instead of UEFI... And the BIOS is UEFI, where the last firmware update was critical, version 2.12.0, with a release date of 2021.0.16. You said it was lying around on a shelf... You might want to apply that BIOS firmware update.

There was also an HBA firmware update marked urgent, for non-SAS storage, that was specifically for systems running Linux OS'es.... Version 16.17.01.00, released 2020.05.18.

I didn't check on updates for your PERC Card as you didn't say which one it was... You also said you where unsure of your RAID Settings on the PERC, and had changed/tried different drives... Which i would think if connected to the PERC card, that the configuration for that would be 'confused'.... As drives connected to a PERC, if not using RAID, then single drives had to be configured as either JBOD (which some models do not have this as an option) or configured as single-drive RAID0 arrays, to use those a single-drives... Just saying that they are locked to specific ports after that configuration.

---

