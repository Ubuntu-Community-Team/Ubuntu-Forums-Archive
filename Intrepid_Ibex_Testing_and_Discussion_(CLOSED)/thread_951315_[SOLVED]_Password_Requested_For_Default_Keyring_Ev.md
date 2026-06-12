---
title: "[SOLVED] Password Requested For Default Keyring Everytime I Connect To Wireless Route"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-10-18
I have a laptop with 8.10 on it, and after I connected to my wireless router for the first time, it saved the password and would automatically connect whenever I start my laptop.

After a week or so, I decided that the password to log on to Ubuntu was too easy to guess, so I changed it. Ever since then, the keyring manager for Gnome comes up and asks for my password to unlock the default keyring when I boot up in order to connect to my wireless. The thing is, the only password the keyring manager will accept is the old one.

I went into the "encryption and keyrings" icon (or whatever it's called) and I didn't see an option there to correct it.

I guess for some reason when I changed my password it didn't change it for the keyring manager. Does anyone know how I can change it there too?

---

### Post by psyke83 on 2008-10-18
> **jlacroix said:**
> I have a laptop with 8.10 on it, and after I connected to my wireless router for the first time, it saved the password and would automatically connect whenever I start my laptop.

After a week or so, I decided that the password to log on to Ubuntu was too easy to guess, so I changed it. Ever since then, the keyring manager for Gnome comes up and asks for my password to unlock the default keyring when I boot up in order to connect to my wireless. The thing is, the only password the keyring manager will accept is the old one.

I went into the "encryption and keyrings" icon (or whatever it's called) and I didn't see an option there to correct it.

I guess for some reason when I changed my password it didn't change it for the keyring manager. Does anyone know how I can change it there too?

The problem is that your user password and default keyring password are now different - therefore, PAM can no longer open the default keyring automatically.

Applications -> Accessories -> Passwords and Encryption Settings.
Menu: Edit-> Preferences

In the Password Keyrings tab, click on the default keyring, and click Change Unlock Password. Set the password to your username's password in order to allow the automatic unlock of the keyring.

---

### Post by jlacroix on 2008-10-19
Thanks! I wonder if this was supposed to happen automatically when I changed my password? Is this a bug?

---

### Post by psyke83 on 2008-10-19
> **jlacroix said:**
> Thanks! I wonder if this was supposed to happen automatically when I changed my password? Is this a bug?

That's an interesting question... I would say it's not a bug. The default keyring inherits the user password upon creation - which is done as a matter of convenience, especially considering NetworkManager integration; but from that point on, the user and keyring passwords should be left apart (IMHO).

---

