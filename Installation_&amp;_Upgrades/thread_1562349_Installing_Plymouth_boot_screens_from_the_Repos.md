---
title: "Installing Plymouth boot screens from the Repos"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by jack frost on 2010-08-27
If you want to add plymouth boot screens that are in the repos I found this link:

 [http://crashsystems.net/2010/04/chan...ymouth-themes/]("http://crashsystems.net/2010/04/changing-plymouth-themes/")

use the command  [I][SIZE=5][B]apt-cache search plymouth-theme

[/B][/SIZE]-it will list all the plymouth boot screens in the repos.
then just type[SIZE=4]** sudo apt-get install (name of the theme)**[/SIZE]
ubuntu will install in :  libs/plymouth/themes

run this : [/I][SIZE=6]sudo update-alternatives --config default.plymouth

[/SIZE][I]it will make a window pop up and you can choose from what  theme you want to install corresponding to the theme name. Each theme  will have a number next to it. just type in the number and hit enter.

then type:  [/I][SIZE=6]sudo update-initramfs -u

Reboot and enjoy the new boot theme.[/SIZE]

I like the solar one so far from the repos; but I think the sunrise may  have it beat. There is another theme called plymouth-orange 10.4 that is  good too.  The ones in the repo's do not did require any manual copying  etc. to work.

---

