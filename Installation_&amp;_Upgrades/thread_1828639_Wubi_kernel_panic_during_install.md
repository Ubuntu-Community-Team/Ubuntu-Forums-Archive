---
title: "Wubi kernel panic during install"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by dakukuu on 2011-08-19
I recently uninstalled my wubi because i had accidently installed gnome 3 and i prefered gnome 2, and it was suggested that a reinstall would be better. So i did the usual and uninstalled it.

However when i reinstalled i got this kernel panic. I'm afraid my camera couldn't take a picture of the entire thing in a readable quality so i took a pic around the kernel panic quote.

[IMG]http://dl.dropbox.com/u/2635293/Photo-0213.jpg[/IMG]

After i power off it appears not to have installed, and in fact returns straight back to installing it like i never ran it. I will provide any information that you ask for as i love Ubuntu and i would really want ti back. Preferably I don't want to be annoying but i'd rather wubi install not liveCD mainly because i don't want it to mess with my windows partiton (apparently creating partitons externally sometimes causes Windows to crash, and i have no windows CD). So any help with wubi is appreciated. Thank you :)

BTW this is installing Ubuntu desktop. I don't mind installing another desktop edition if that helps in any way?

EDIT: Also, does 10.04 LTS now use the latest PulseAudio? Otherwise does anyone know how to update it as the old pulseaudio doesn't support my realtek soundcard.

---

### Post by bcbc on 2011-08-19
Are you trying to install the same release you had before, or a different release? With some hardware, one might release might work. and another might have issues.

So... what computer brand/model/graphics card(s) do you have and what release are you installing.

---

### Post by dakukuu on 2011-08-19
The last wubi install i had was 10.10 i think, and i updated that to 11.04 

I have a compaq presario CQ62 laptop. On 11.04 it had kernel panics randomly during use of firefox, but now that im installing it (before was a version update from 10.10) it wont work, and keeps getting this error.

Would installing 10.04/10.10 through wubi be worth a shot?

EDIT: Sorry here's my computer stats.

Brand: Compaq
Model: Presario CQ62 (notebook edition)
Graphics card: Intel mobile chipset 4 series (i'm sad that i can remember that off by heart now lol)
Distro: Ubuntu 11.04 wubi

EDIT2: I've got hold of wubi 10.10 edition, so i'm gonna try that and see if it's sucsessful.

EDIT3: I decided to work around by installing 10.10 wubi and doing an upgrade. It's something to do with 11.04, but neithertheless I worked around it :)

---

### Post by bcbc on 2011-08-19
I can't find anything that indicates this computer has a problem with 11.04. So... I'm a bit stumped.

Hopefully 10.10 works okay - I don't see why it wouldn't if it worked last time.

PS it's a good idea to run chkdsk every now and then when uninstalling/reinstalling wubi. If you have similar problems with 10.10, then you could try that. Go to (My)Computer, right click on the drive you installed on e.g. C:, Properties, Tools, Check disk for errors, Fix automatically (or the longer check for bad sectors if you think it might be required). If it's C: you need to reboot into Windows to complete the check.

---

### Post by dakukuu on 2011-08-19
I got kernel panics on a often occasion when i updated my previous installation,probably due to a bad package. So i presumed it would be that, although i'm under the impression wubi wipes [/s]the entire drive[/s] the wubi files after uninstallation

Likewise, i'm on Ubuntu 11.04 now (installed 10.10 upgraded and now it's fine, no kernel panics). I hope nobody gets that god awful error in future :3 Hopefully not, because Ubuntu is very well compiled.

Good point there bcbc, i should probably do that next time i'm running my window OS. I only use Wubi because apparently sometimes dedicated partitons can break the windows partiton, and i can't risk borking my windows partiton because i have no install disk :/ so yeah. Well at least it's solved now :D

---

### Post by bcbc on 2011-08-19
Cool glad you got it sorted.

I suppose your computer might have an issue with the Natty kernel from the release - whereas with the upgrade you get the latest (just speculation). Wubi checks the install CD's md5sum before installing so it shouldn't be a corrupt kernel/initrd from the CD.
So no idea what the problem is ;)

PS when you want to try something adventurous, you can just boot windows and copy your virtual disks e.g. root.disk  - and then if you need to, just copy them back over after the experiment.

For Wubi it's best to [avoid hard shutdowns]("https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen"), playing with the boot managers (and don't install burg), and keep important data backed up. Then it works great.

---

