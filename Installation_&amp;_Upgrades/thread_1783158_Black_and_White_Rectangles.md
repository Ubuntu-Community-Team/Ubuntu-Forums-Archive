---
title: "Black and White Rectangles?"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by precond on 2011-06-15
Hello everyone,

I’m a MS Windows user who wishes to install Ubuntu on a partitioned hard drive. I work on a Toshiba Qosmio X500 with Windows 7 Ultimate 64-bit pre-installed.

I recently downloaded the Ubuntu 11 64-bit from the Ubuntu website and made my Ubuntu DVD (Disc) and a new partition (31.4GB) to install it on.

I tried to boot it directly from the Disk, I didn’t had to touch anything:
[LIST]
[*]It made my screen go purple with Ubuntu in the center and 4 points under it (Animated with color changing white-purple)
[*]Then black
[*]Then purple back again with the same animation and branding stuff exept it became on the top-left of the screen and smaller.
[*]Then some installation proof lines under it
[*]Then the screen: [http://nexus-holding.com/screenshots/ubuntu.jpg](http://nexus-holding.com/screenshots/ubuntu.jpg) (The white space was purple the first time)
[*]Then nothing else
[/LIST]
I decided then to run the CD in Windows but had the same result after reboot (the only difference was that it clearly asked me to choose an OS) and I might need some help.

I’m less than a newbie (in Linux things) and searched the web. Found errors about white stripes but (for them) it happened after the installation.

[SIZE="1"]PS: And I read the extension to the code of conduct, there’s a typing mistake on Section II number 17. “The the” should be “that the”.[/SIZE]

Advanced thanks.

---

### Post by sanderd17 on 2011-06-15
When you see the first purple screen if you boot from the CD, press a key, you will arrive in a text based menu.

Choose your keyboard layout and your language and select the last menu (I think it is F5) and try different options. I should certainly try nomodeset and acpi=off.

Then continue booting and see if it works.

---

### Post by Quackers on 2011-06-15
Welcome to UF :-)

It looks like a video problem. What graphics card are you running there?
You may need the nomodeset boot option as explained below (or another)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by precond on 2011-06-15
Sorry for late reply, had some other, easier to resolve, problems with the installation.

@sanderd17: Great thanks. It worked for me. (and it's F6 for me)

@Quackers: My graphic card is an NVidia 400 something.

---

### Post by Quackers on 2011-06-15
So you can boot the live cd desktop now? With the nomodeset option?
If so you can install and on first boot of the new system you will need to use that option again, but it is applied in a different way. See the link I gave earlier for details (lower down the page).

---

### Post by precond on 2011-06-15
Yeah. It seems. When I install it from the CD, it won't show me the "Choose an OS" screen.
When I install it from Windows, the screen appears but I can't set options so it breaks.
I will check your link.

---

### Post by sanderd17 on 2011-06-16
Yep, certainly check his link (I have the same link in my signature). First you have to press the 'e' in GRUB (the OS chooser) to edit the command and add you nomodeset. Secondly, you need to add that command permanently via changing a config file and updating grub.

---

### Post by precond on 2011-06-16
Thanks. Did everything in the link and it works great now.

---

### Post by Quackers on 2011-06-16
Nice one :-)
Glad to hear you are up and running.

---

