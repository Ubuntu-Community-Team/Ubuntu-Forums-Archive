---
title: "upgrading to lucid"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by enceladus47 on 2010-03-16
my first contact with ubuntu was karmic so i never upgraded, so when i get lucid (whether alpha beta or final), do i have to do a clean installation or is there a way to upgrade?

---

### Post by sandyd on 2010-03-16
> **enceladus47 said:**
> my first contact with ubuntu was karmic so i never upgraded, so when i get lucid (whether alpha beta or final), do i have to do a clean installation or is there a way to upgrade?

yup.
you can upgrade through the upgrade manager

---

### Post by mick222 on 2010-03-16
you can either press alt and f2 and type in update-manager -d or when the full release happens there is an option in update manager to upgrade

---

### Post by fatality_uk on 2010-03-16
I would always suggest using the update manager. It will also update the applications you have installed as well as your system.

---

### Post by enceladus47 on 2010-03-16
thanks, so what will change and what will not in my system?, i mean do i get new programs that come preinstalled with lucid, what about new hardware drivers or little changes even like desktop changes and so?

---

### Post by ENigma885 on 2010-03-16
To update to Lucid 
> To upgrade from Ubuntu 9.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '10.04' is available. Click Upgrade and follow the on-screen instructions.   

To upgrade from Ubuntu 9.10 on a server system: install the update-manager-core package if it is not already installed; edit /etc/update-manager/release-upgrades and set Prompt=normal; launch the upgrade tool with the command sudo do-release-upgrade -d; and follow the on-screen instructions. 
from [http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

***[COLOR="Red"]Be aware that:-
1- Alpha2 in way to early to upgrade to especially if it's ur primary machine. And expect more than just stability issues!
2- As a personal recommendation and based on what u wrote above "my first contact with ubuntu was karmic". **DON'T** upgrade from a stable release, i.e. Karmic 9.10, to an unstable Alpha one.[/COLOR]

---

### Post by phillw on 2010-03-16
> **ENigma885 said:**
> To update to Lucid 

from [http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

***[COLOR="Red"]Be aware that:-
1- Alpha2 in way to early to upgrade to especially if it's ur primary machine. And expect more than just stability issues!
2- As a personal recommendation and based on what u wrote above "my first contact with ubuntu was karmic". **DON'T** upgrade from a stable release, i.e. Karmic 9.10, to an unstable Alpha one.[/COLOR]

Indeed do not switch to a solely testing version. 
Just as a note. 10.04 is on alpha3 and goes beta1 on Thursday. Whilst you should not run it as your only system, if you have 10GB of hard-drive space free, why not pop it on there ? It will happily live with 9.10 and you can ensure that all your hardware is happy with the Lynx, transferring a **_copy_** of your things from your home directory is quite painless.

If you'd like to keep abreast of what goes on in the Lucid Lynx area, pop over to [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)  We don't bite :-D

Regards,

Phill.

---

### Post by enceladus47 on 2010-03-16
Thanks for that! i was actually planning to wait for the beta stage to upgrade, and i won't mind running into a few problems :)

and i'll consider the idea of running it alongside karmic, have till thursday to decide, so ya, expect me in the lucid area soon;)

---

### Post by albert s on 2010-03-16
as an aside to this, Im in the middle of adding an additional 80g HD to my system,
I currently have an 80g on 9.10
and now Im considering perhaps doing a dual install, 9.10 on 1 drive, and lucid on the other, any problems/issues I should be aware of?
and is this just the same as a dual boot?
thanks.

---

