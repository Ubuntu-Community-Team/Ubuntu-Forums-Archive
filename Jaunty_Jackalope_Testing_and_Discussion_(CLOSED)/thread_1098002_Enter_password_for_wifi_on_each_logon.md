---
title: "Enter password for wifi on each logon"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Asham on 2009-03-16
Every time I logon to the desktop environment I get a request to enter the password for connecting to the WiFi. Can it be done so that its automated? /Adam

---

### Post by ildfroe on 2009-03-16
[http://ubuntuforums.org/showpost.php?p=6904872&postcount=2](http://ubuntuforums.org/showpost.php?p=6904872&postcount=2)

Edit: 
And make the new password blank

---

### Post by hexion on 2009-03-16
Follow the instructions here:
[http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/](http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/)

If you use autostart, the only way is setting your keyring password to blank (apart from following the instructions above), but this is NOT recommended for obvious security reasons.

---

### Post by biasquez on 2009-03-21
> **hexion said:**
> Follow the instructions here:
[http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/](http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/)

If you use autostart, the only way is setting your keyring password to blank (apart from following the instructions above), but this is NOT recommended for obvious security reasons.

is it possible to use not-blank password and not disable autostart?

---

### Post by scaine on 2009-03-21
Yep, you can use autostart and still have a certain WIFI connect without prompting, but you need to authorise your user to do so.

Open a terminal and do this :
```
sudo -i
polkit-gnome-authorization 

```Scroll down to "network-manager-settings" / "system" / "Modify system connections"

Click on that last one and the right-hand side where it says "Explicit Authorisation", hit the "Grant" button, then choose your username. No need to add any constraints - just leave it on "none".

Now, right-click on network manager and choose "Edit Connections", then find the WIFI network you want to be the default.  Edit it and put a tick in the "Available to all users" box.

Give your PC a reboot to test it out.  Even a log off/in should do the trick to see if it'll connect automatically.

---

### Post by caryb on 2009-03-21
> sudo -i
polkit-gnome-authorization

I would be careful with this command! If my powers of observations are correct Asham is using KDE (Kubuntu)


Cary

---

### Post by biasquez on 2009-03-21
> **scaine said:**
> Yep, you can use autostart and still have a certain WIFI connect without prompting, but you need to authorise your user to do so.

Open a terminal and do this :
```
sudo -i
polkit-gnome-authorization 

```Scroll down to "network-manager-settings" / "system" / "Modify system connections"

Click on that last one and the right-hand side where it says "Explicit Authorisation", hit the "Grant" button, then choose your username. No need to add any constraints - just leave it on "none".

Now, right-click on network manager and choose "Edit Connections", then find the WIFI network you want to be the default.  Edit it and put a tick in the "Available to all users" box.

Give your PC a reboot to test it out.  Even a log off/in should do the trick to see if it'll connect automatically.


ok, this solved my problem, thanks!

---

### Post by scaine on 2009-03-21
> **caryb said:**
> I would be careful with this command! If my powers of observations are correct Asham is using KDE (Kubuntu)
Cary

Good point!  At least it helped biasquez.  Sorry Adam.  I don't know much about how policykit is integrated into KDE, or how Network Manager looks/behaves in that environment.

---

### Post by Asham on 2009-03-22
Don't worry about it. At least this thread proved to be helpful! :)

I'm sure there will be fixes out when 9.04 is finalized. I can live with entering the password until then.

---

### Post by Windsurfer619 on 2009-04-14
> **scaine said:**
> Yep, you can use autostart and still have a certain WIFI connect without prompting, but you need to authorise your user to do so.

Open a terminal and do this :
```
sudo -i
polkit-gnome-authorization 

```Scroll down to "network-manager-settings" / "system" / "Modify system connections"

Click on that last one and the right-hand side where it says "Explicit Authorisation", hit the "Grant" button, then choose your username. No need to add any constraints - just leave it on "none".

Now, right-click on network manager and choose "Edit Connections", then find the WIFI network you want to be the default.  Edit it and put a tick in the "Available to all users" box.

Give your PC a reboot to test it out.  Even a log off/in should do the trick to see if it'll connect automatically.

I find it a lot easier to just leave the password blank. Ubuntu never bothers you for the keyring password again.

---

