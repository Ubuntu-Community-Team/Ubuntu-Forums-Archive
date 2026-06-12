---
title: "Gutsy kernel xx22 borked by nVidia Xorg"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by f1uxam on 2007-07-20
I updated to Gutsy Tribe 3 from within Feisty but forgot that my Xorg.conf was customized for the nVidia driver that I installed using Envy.  So, I can boot into Gutsy only with Feisty's xxx16 kernel.
I'd like to mod the Xorg.conf so as to use the generic video driver for booting the xxx22 kernel -- isn't it just something like nv rather than nVidia on one line? -- and then once again use Envy to install nVidia's latest driver for the xxx22 kernel.  This Vaio notebook has the nVidia 7400 mobile.
How should I edit the Xorg.conf to load GDM with the new Gutsy kernel ?
I'm contrite because I know this is asked in many ways and very often ...

---

### Post by renzokuken on 2007-07-20
open up a TTY terminal screen with Ctrl + Alt + F1 login and type the following :-

first backup your current xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

then edit it

```
sudo nano /etc/X11/xorg.conf
```

use the arrow keys to scroll down to the "Section **Device**" part and change it from this

```

Section  "Device"
       Identifier    "some description of your card"
      Driver          [color=red]"nvidia"[/color]
End Section
```

to this

```

Section  "Device"
       Identifier    "some description of your card"
      Driver          [color=blue]"nv"[/color]    # could also use "vesa"
End Section
```

press Ctrl+X, Y and Enter to save your changes

and reboot

you can then boot into your new kernel, reinstall the nvidia drivers (you need to install nvidia drivers for every new kernel)

---

