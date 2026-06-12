---
title: "There is nothing on the Desktop"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by Sridharrao85 on 2008-05-22
Hello,

  I uninstalled some packages using synaptice package manager.
Most of them are related to Evolution. After the reboot, there is nothing on the desktop. There is just a empty screen of ubuntu8.04. There is no top panel and bottom panel. It is not showing my previous files, which were on desktop.

  I think, i unnecessarily uninstalled some packages. Is there anyway i can restore my system. I don't remember the package names which i uninstalled. One last thing, If i cannot restore my OS, Is there a way to reinstall without effecting my other os vista.

  Even if you don't know the answer, some suggestions with direction are appreciated.

Thanks

---

### Post by jolx on 2008-05-22
mabye u uninstalled gnome-panel?

---

### Post by christianxxx on 2008-05-22
Which would be very easy to install again.... :)

---

### Post by iaculallad on 2008-05-22
Or you could try this:

Press Alt+F2 and enter the commands below:


killall gnome-panel

or

kill `pidof gnome-panel`

then restart

---

### Post by Sridharrao85 on 2008-05-22
Thanks guys for suggesting me sth. But, it didn't work.

After booting into Ubuntu, I can see my mouse cursor on the desktop, other than that, i cannot see anthing. If i try to right click or left, nothing is happening.

When booting, it saying that, it is mounting my windows drive, but i cannot see that drive on the desktop.

If i press Alt+F2 also nothing is happening. But, If i press ctrl+alt+del it is giving me the logout screen.

---

### Post by vanadium on 2008-05-22
I would start reinstalling "ubuntu-desktop" (which will reinstall all packages you erroneously deleted, but also evolution) to see if this brings your account back to life.

---

### Post by Sridharrao85 on 2008-05-25
aa

---

### Post by Sridharrao85 on 2008-05-25
It is working now. Thanks a lot buddy.

---

