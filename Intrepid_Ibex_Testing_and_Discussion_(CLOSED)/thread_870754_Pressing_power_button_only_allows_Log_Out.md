---
title: "Pressing power button only allows Log Out"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-07-26
When I press the power button, the only options I have is to switch user, or to log out. With Hardy, you could shutdown, restart, etc. Is this there a reason for this new behaviour?

---

### Post by spamzilla on 2008-07-26
It seems to be a bug

Following quote taken from here [http://www.ubuntu.com/testing/intrepid/alpha3](http://www.ubuntu.com/testing/intrepid/alpha3)

> 
On Ubuntu systems, the "Shutdown" button on the GNOME desktop does not shut down the system, but instead logs the user out. Investigation of this issue is ongoing. As a workaround, to shut down the system you can log out of GNOME and then shut down from the login screen. [https://bugs.launchpad.net/bugs/250506](https://bugs.launchpad.net/bugs/250506)


---

### Post by pressureman on 2008-07-26
Right click somewhere on your panel, "Add to Panel...", and add the "Shutdown" app to your panel.

Now you can have a logout-only, or a shutdown button.

Edit: disregard that - it still just returns to GDM.

---

### Post by scradock on 2008-07-26
> **pressureman said:**
> Right click somewhere on your panel, "Add to Panel...", and add the "Shutdown" app to your panel.

Now you can have a logout-only, or a shutdown button.

Still doesn't get you out - you end up at the log-in window whatever you choose and have to choose Restart or Shutdown from the Options menu (Alt-T, R, Alt-R).

---

### Post by rouge568 on 2008-10-07
This has been registered as a bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/252795](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/252795)

However, there is a permanent and effective fix. Add Ted Gould's Launchpad repository, and use the gnome-power-manager package from there. This source was provided in the bug discussion. 
[https://edge.launchpad.net/~ted-gould/+archive](https://edge.launchpad.net/~ted-gould/+archive)

Instead of the logout options, the power-down options are displayed, with the automatic 60-second shutdown. Very nice!

---

