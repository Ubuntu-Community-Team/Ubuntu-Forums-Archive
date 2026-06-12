---
title: "Vga not supported ati 2100"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by Vyse21 on 2011-04-03
Hi i have tried to install via usb ubuntu 10 - but after the boot menu my pc monitor says vga not support - i know some ati 2100 cards have a problem with ubuntu (onboard), is there anything i can do?

At the moment i am trying wibi install -- circa 64hrs remaining for download lol

ps my pc runs fine on xp.

specs amd x2 4400+ @ 2.3GHZ Brisbane, 1Gig ram, ati onboard 2100, i think a amd 740G chipset.

Thanks in advance

ps i used unetbootin to get the iso onto usb

i think the iso i used is called Lucid

---

### Post by Dutch70 on 2011-04-03
Have you tried to see if it works from the usb if you select "Try Ubuntu" instead of install Ubuntu?

A couple other things to easily rule out are the md5sum of the downloaded .iso.
[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

And of course checking the cd/usb.
[[COLOR="Red"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

If selecting Try Ubuntu doesn't work, hopefully you'll find something wrong with one of these, they are usually easy to fix.

---

### Post by Vyse21 on 2011-04-03
thanks for the reply. Yes i have tried the "try" option. Also burned netbook and desktop to cd - same thing, tried to install via windows xp - using wubi - installs ok, then on reboot loads! - but the screen goes blank after grub and then get droped into a shell after 5 mins telling me root is missing?

I think it is a problem with ati cards. I used mandrake years ago on a geforce agp card which ran ok (no 3d) and was really hoping linux had com a long way since then so i could quickly boot my pc and check emails and such without waiting for xp to boot my firewall and antivirus and 10+ add-ons.

Gonna download the alternative text based installer now. Does anyone know if there are some special options to activate? I thought having on-board video would have made 2d support simple.

Is this a known issue?

PS works great on my eee pc - but can't use it on hdd as it may damage the hidden partition which has the laptop recovery or factory reset and win xp on it.Hence the reason to install on desktop.

---

### Post by Dutch70 on 2011-04-03
You shouldn't have grub with a wubi install.

Have you tried boot options like nomodeset?

---

### Post by Vyse21 on 2011-04-03
well it pops up with the windows xp pro or ubuntu then grub pops up with something like default, recovery, or winxp on sda1. Anywhoo i am downloading 11.04 alternative and gonna burn that to cd - hopefully wubi is on the iso so i can try that first. 

Please tell me how to do that command? - i tried startx - nothing. The reason is ask is because i do not see a commandline before the vga not supported comes up. Do i need the login as root first? I guess so.

---

### Post by Dutch70 on 2011-04-03
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by Vyse21 on 2011-04-04
Hi got it working - sort of. Load in vga low res graphics boot up, changing grub to add nomodeset does not work but i can get it up and running, perhaps 11.0 will work better. Any clue as to when open source ati drivers will be working with the ati 2100 - as its no longer supported by ati/amd - supported ala intel integrated?

Signing off, thanks for the link

---

