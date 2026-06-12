---
title: "install desktop and other apps to minimum install"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by umfufu on 2008-04-01
I have installed minimal ubuntu from the alternate cd on my old laptop.
I would like to install a desktop environment to it and some other packages to keep it as small as possible.

How to install for instance the enlightenment desktop with no internet connection available on the laptop, i have an internet connection on my desktop pc.

Probably it is the same for all the packages i might install later also?

regards.

---

### Post by kerry_s on 2008-04-01
okay, that's just foolish.
can you hook the laptop to the internet to get what you need?

dependency's are the biggest road block when installing applications, not only do you need the program, but you need everything the program uses to run.

for example, first you'll need X
xorg is many,many packages around 250mb
enlightment is not bad, has 4 dependencys
etc....

---

### Post by umfufu on 2008-04-02
> okay, that's just foolish.
can you hook the laptop to the internet to get what you need?

No i can not do this, there's no network card in it, and i d'ont want to buy one because.

but is it possible to download the needed packages  and libraries with my other computer an put it on cd for instance to install them on the laptop?
i Know this is not the common way but there is no other possibilty.

regards

---

### Post by aysiu on 2008-04-02
> **umfufu said:**
> No i can not do this, there's no network card in it, and i d'ont want to buy one because.

but is it possible to download the needed packages  and libraries with my other computer an put it on cd for instance to install them on the laptop?
i Know this is not the common way but there is no other possibilty.

regards
It's possible but extremely annoying.

Good luck: [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by aquinashub on 2008-04-03
Hmmmn.. just as an experiment, I attempted to go through all of Enlightement and Xorg's dependencies via the Ubuntu packages site... man, I think I did pretty well, but after a while, you just get lost in it! There are A LOT of packages - I guess that's why the linux packaging system has always been a source of stress: it's just very complex. Not to mention making sure you have compatible versions and then to install them all correctly.

I'd say, for a very minimal Ubuntu install on your laptop - try Fluxbuntu. I had it for a while, and it's quite nice. Those developers are doing a good job at keeping it light - and yet still Ubuntu-style.

Just for fun, I'll give you my partial package list before I got too tired to continue:

xorg libgl1-mesa-glx libc6 libgcc1 gcc-4.2-base libdrm2 libx11-6 x11-common debconf debianutils lsb-base ncurses-bin libncurses5 libgpmg1 sed libx11-data libxau6 libxdmcp6 libxdamage1 libxfixes3 libxext6 libxxf86vm1 libglu1-mesa libstdc++6 xbase-clients appres libice6 libsm6 libxt6 beforelight libxaw7 libxmu6 libxpm4 libxss1 bitmap editres fstobdf libfs6 iceauth ico listres mesa-utils oclock smproxy viewres perl-base debconf-english apt-utils libapt-pkg-libc6.6-6-4.5 apt libdb4.4 x11perf libxmuu1 xauth xbiff xcalc libxaw7 xclipboard xclock libfontconfig1 fontconfig-config ttf-dejavu-core ttf-dejavu-extra ttf-bitstream-vera defoma x-ttcidfont-conf file libmagic1 zlib1g perl libdb4.4 libgdbm3 perl-base perl-modules whiptail libnewt0.52 libslang2 libfribidi0 libpopt0 xfonts-encodings xfonts-base xutilslibexpat1   xfonts-utils libfreetype6 libfontenc1 libxfont1 ttf-freefont gsfonts-x11 gsfonts ucf coreutils libacl1 libattr1 libselinux1 libsepol1 libexpat1
 ----- I actually FINISHED the Enlightenment list, so you may still want to try it ----- 

enlightenment enlightenment-data dpkg coreutils libacl1 libattr1 libc6 libgcc1 gcc-4.2-base libselinux1 libsepol1 libaudiofile0 libesd-alsa0 esound-common libasound2 esound-clients libice6 x11-common debconf perl-base debconf-english debianutils lsb-base ncurses-bin libncurses5 libgpmg1 gpm ucf debconf-utils sed libimlib2 libbz2-1.0 libfreetype6 zlib1g libid3tag0 libjpeg62 libpng12-0 libtiff4 libungif4g libx11-6 libx11-data libxau6 libxdmcp6 libxext6 libsm6 libxinerama1 libxxf86vm1 esound libwrap0 menu libstdc++6 e16keyedit gdk-imlib11 imlib-base libglib1.2 libgtk1.2 libgtk1.2-common libxi6 libgdbm3 e16menuedit enlightenment-theme-bluesteel enlightenment-theme-brushedmetal enlightenment-theme-ganymede enlightenment-theme-shinymetal epplets libepplet0 ttf-bitstream-vera defoma file libmagic1 perl libdb4.4 perl-base perl-modules whiptail libnewt0.52 libslang2 libpng-dev libfribidi0 libpopt0 libft-perl libttf2 fontconfig fontconfig-config ttf-freefont ttf-dejavu-core ttf-dejavu-extra gsfonts-x11 gsfonts xfonts-utils xutils libfontenc1 libxfont1 xfonts-encodings sessreg xcursorgen libxcursor1 libxfixes3 libxrender1 xutils-dev cppcpp-4.1 libexpat1 libfontconfig1 eterm libast2 libxt6

Happy minimizing!

---

### Post by aquinashub on 2008-04-03
Ah, what the heck?

apt apt-utils coreutils debconf-2.0 debconf-english debconf-utils debianutils dpkg fontconfig-config gcc-4.2-base gpm libacl1 libapt-pkg-libc6.6-6-4.5 libattr1 libbz2-1.0 libc6 libdb4.4 libexpat1 libfontconfig1 libfreetype6 libgcc1 libgpmg1 libice6 libimlib2 libid3tag0 libjpeg62 libncurses5 libpng12-0 libselinux1 libsepol1 libsm6 libstdc++6 libtiff4 libungif4g libx11-6 libx11-data libxdmcp6 libxau6 libxext6 libxft2 libxinerama1 libxpm4 libxrandr2 libxrender1 lsb-base menu ncurses-bin perl-base sed ttf-dejavu-core ttf-dejavu-extra ucf x11-common zlib1g fluxbox fluxconf fluxdesk fluxpager

There's all of the Fluxbox dependencies if you like. But you'll still need all of xorg (which shares so many of these packages) As you can see, it's quite tedious work. I wouldn't advise going about it this way if you haven't done this sort of thing before - but if you do: READ lots, QUADRUPLE check EVERYTHING, and then come back here and tell us how your manually installed laptop's doing, and of course, your sanity!

---

### Post by kerry_s on 2008-04-03
:lolflag:

use the alternate cd to install xorg, then work from there.

custom install with out internet, is not a good idea.

---

### Post by RedSquirrel on 2008-04-04
> **aquinashub said:**
> Hmmmn.. just as an experiment, I attempted to go through all of Enlightement and Xorg's dependencies via the Ubuntu packages site... man, I think I did pretty well, but after a while, you just get lost in it! There are A LOT of packages - I guess that's why the linux packaging system has always been a source of stress: it's just very complex. Not to mention making sure you have compatible versions and then to install them all correctly.

Now you truly appreciate all the hard work your package manager does for you. :)

---

### Post by dstew on 2008-04-04
You can update and install off-line using the [nonetdebs]("http://nonetdebs.homeip.net/") service. You upload to them a file with your current system status, and they assemble a bunch of links to the packages you need, including dependencies. You download the packages to your internet computer, wherever that is, and can then copy them onto a USB stick or CD. Then,  put them onto your no-internet computer, and install them.

---

### Post by aquinashub on 2008-04-04
> **RedSquirrel said:**
> Now you truly appreciate all the hard work your package manager does for you. :)

Absolutely.

And that 'nonetdebs' site is yet **another** extension of that complex system, making it easier for *anyone* to get Linux (or at least bits of it) on their machine.

That's a great resource, could have used it during those installs of more obscure debian-based distros, when my wireless wouldn't work!

---

