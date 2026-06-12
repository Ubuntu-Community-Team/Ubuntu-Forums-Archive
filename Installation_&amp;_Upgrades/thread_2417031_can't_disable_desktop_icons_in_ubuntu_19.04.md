---
title: "can't disable desktop icons in ubuntu 19.04"
date: 2019-04-19
forum: Installation &amp; Upgrades
---

### Post by tojonukokhadush on 2019-04-19
after network upgrade from ubuntu 18.10 to ubuntu 19.04, what issue i have been realizing is i can't disable desktop icons through gnome tweaks. i don't like the idea of keeping icons in my desktop. help me disable that.

---

### Post by deadflowr on 2019-04-19
Doesn't look like you can, currently:
[https://community.ubuntu.com/t/no-desktop-icons-already-arrived-in-19-04/9295/28]("https://community.ubuntu.com/t/no-desktop-icons-already-arrived-in-19-04/9295/28")
At least in the ubuntu-desktop session.
jbicha does give an alternative solution.
Other solution is to simply keep Desktop empty and turn off the show home/trash/whatever in the extensions tweak settings.

---

### Post by Dennis N on 2019-04-19
You can disable them. In Tweaks, click the gear icon by the switch for the 'Desktop Icons' extension. That will open a configuration dialog with switches to turn off the icons.

Edit: : If you put files in your Desktop folder, they will appear on Desktop itself.

---

### Post by mc4man on 2019-04-20
I suspect this will do the job
```
sudo apt purge gnome-shell-extension-desktop-icons
```
```
reboot
```

---

### Post by tojonukokhadush on 2019-04-22
i installed gnome session. and that's okay for now. the extension seems to be the problem anyway :) thanks for the help.

---

### Post by grn on 2019-04-24
> **mc4man said:**
> I suspect this will do the job
```
sudo apt purge gnome-shell-extension-desktop-icons
```
```
reboot
```

this also removes ubuntu-desktop

i would rather suggest:

```
cp /usr/share/gnome-shell/extensions/desktop-icons@csoriano/ ~/desktop-icons@csoriano_backup/
```
and then...
```
sudo rm -r /usr/share/gnome-shell/extensions/desktop-icons@csoriano/
```

---

### Post by tojonukokhadush on 2019-04-25
> **mc4man said:**
> I suspect this will do the job
```
sudo apt purge gnome-shell-extension-desktop-icons
```
```
reboot
```


this seems to solve my problem with no any error. also, i had installed gnome session previously. working perfectly fine all the sessions!

---

### Post by charneykaye on 2019-06-18
> **mc4man said:**
> I suspect this will do the job
```
sudo apt purge gnome-shell-extension-desktop-icons
```
```
reboot
```

Success! Thanks.

---

