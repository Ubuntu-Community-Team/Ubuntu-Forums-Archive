---
title: "Cannot run UBUNTU"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by AcAi on 2005-09-20
After i finish install Ubuntu 5.04
it will askme for a login and password
i put the login and the password
but afer that it show 

" You have new mail "
acai@Azfar :~$\

and it stop right there
what must i do to to make my Ubuntu run?

---

### Post by moopere on 2005-09-20
[QUOTE=AcAi]After i finish install Ubuntu 5.04
it will askme for a login and password
i put the login and the password
but afer that it show 

" You have new mail "
acai@Azfar :~$\

and it stop right there
what must i do to to make my Ubuntu run?[/QUOTE]


What do you mean 'its stops right there"?  Does the machine freeze/lockup?  It looks like Ubuntu _is_ running to me....can you type anything or has the keyboard locked?

Cheers,
Craig

---

### Post by heimo on 2005-09-20
What happens if you try to?
 ```
sudo /etc/init.d/gdm start
``` 

If your graphical user interface (X Window System, Gnome and all related stuff) is not properly installed, you could try:
 ```
sudo apt-get install ubuntu-desktop
``` 

What you're seeing is console / terminal / shell - text mode interface. Your graphical user interface hasn't started as it should. Were there any problems during install? Did you use default install method (not expert mode or server mode)?

Thanks!

---

