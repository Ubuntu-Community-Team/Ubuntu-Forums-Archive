---
title: "Problem after upgrading"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by eldersoares on 2008-04-25
hi folks... one more problem.. i know these days must be difficult. i searched the forums for a problem similar to mine but didnt find....

well, i left upgrading all night. when i woke up, the screen was black and frozen. i had to force reboot. since then, when i start gnome, it tells me there are errors in hal, nautilus, bonobo. the panels and icons dont appear. so i tried:

sudo dpkg --configure -a

it changed a bit... i still can't enter gnome. but those messages dont appear anymore. actually, if i enter gnome in safe mode, i can do everything very well... everything seems to be working fine

my questions are?

- how can i check which packages have problems, are not installed or broken or something?
- how can i solve these problems?
- if i cant solve, how can i come back to my little gibbon????


thanks all of you!!! this community is great
seeya

---

### Post by Malikius on 2008-04-25
I just did a complete reformat and install of the Ubuntu 8.04 and it isn't updating properly. Have internet etc. Did I do something wrong on the install?

---

### Post by eldersoares on 2008-04-25
but if you installed 8.04 from cd, that's the newest version, you can't upgrade more... yet...

anyone knows something about my problem???

---

### Post by Victormd on 2008-04-25
> **Malikius said:**
> I just did a complete reformat and install of the Ubuntu 8.04 and it isn't updating properly. Have internet etc. Did I do something wrong on the install?

What are you trying to update? the programs or the distro?
```
sudo apt-get update
sudo apt-get upgrade
```
from the terminal should do the trick. However, it's taking a while (longer than with gutsy), probably due to extreme server activities due to the release.

---

### Post by eldersoares on 2008-04-26
things changed a bit... i tried
dpkg-reconfigure -a

[LIST]
[*]i can only enter in gnome safe mode
[*]sound doesnt work anymore
[*]compiz effects either (because i'm in safe mode, i believe)
[*]when i enter gnome in normal mode, it tells me: "cant open nautilus" "failed bonobo-activation"
[/LIST]
 did anybody have a good experience with hardy in a dell inspiron 6400? should i downgrade to gutsy? or maybe download hardy cd and install it?

PLZ HELP!!!!!!!!!!!!

---

### Post by rhombus on 2008-04-26
I had the same problem after upgrading from Gutsy to Hardy.

The only way I could get in was to start a session using the menu at the bottom-left of the login window and selecting Gnome failsafe mode.

I tried uninstalling all the Mono 1.2x packages from Synaptic (since Bonobo is part of Mono I guess) and tried reinstalling Nautilus, but neither helped.

After searching a while I realized that I had installed Mono 1.9 previously, and since I only formatted my OS partition and not the one reserved for my /home folder, somehow Mono 1.9 was still installed. There is an uninstaller in the Mono 1.9 folder. I ran that, rebooted, and I was able to start a normal session, no errors. I reinstalled Mono 1.2x from synaptic as well and everything has been running smoothly since then. I don't know if this is the case for everyone getting this error, but it helped me, so check if you have a wayward Mono 1.9 installation somewhere.

-e

---

### Post by eldersoares on 2008-04-26
thank you very much rhombus, the problem was with mono, i had a old installation, version 1.2...
now i can login to gnome normally!!!!!!

BUT...
i still have some problems:
- when i trying to make things work, i followed a dell wiki ([http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound)) that explained about sound issues. it was worst! before, the players didn't play but i could hear the gnome's sounds. now, any sound works and the volume control in notification bar has an "X". in system -> preferences -> sounds, there's no device to choose....
- another problem is with wifi that seems to work, but the led in my dell laptop (inspiron 6400) never turns on!
- when changing screen brightness through the keyboard, it jumps a very large step... i can't choose an intermediate brightness... only completely dark, medium or maximum bright

meanwhile, thats it!
thanks

---

