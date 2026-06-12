---
title: "authorizations?"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by scradock on 2010-02-15
Does anyone know what has happened to the Authorizations tool? It used to be available under System | Administration, and called polkit-gnome-authorization, allowing specific tasks to be pre-authorized for specific (or any) user(s).

Now there is no such tool, how does one, for instance, allow NetworkManager to start up at Login without raising an authorization dialog?

---

### Post by jpeddicord on 2010-02-16
> **scradock said:**
> Does anyone know what has happened to the Authorizations tool? It used to be available under System | Administration, and called polkit-gnome-authorization, allowing specific tasks to be pre-authorized for specific (or any) user(s).It was removed when polkit-1 was released and no one was available to rewrite it. It's unfortunate, but there's a bug somewhere on GNOME (or freedesktop?) bugzilla tracking it.

> Now there is no such tool, how does one, for instance, allow NetworkManager to start up at Login without raising an authorization dialog?


That's actually not PolicyKit; that's your local keyring. If you have auto-login turned on, the keyring will not be automatically unlocked and so it must prompt you for your password to decrypt it.

---

### Post by scradock on 2010-02-16
> **jpeddicord said:**
> It was removed when polkit-1 was released and no one was available to rewrite it. It's unfortunate, but there's a bug somewhere on GNOME (or freedesktop?) bugzilla tracking it.



That's actually not PolicyKit; that's your local keyring. If you have auto-login turned on, the keyring will not be automatically unlocked and so it must prompt you for your password to decrypt it.
Thanks - that clears things up. I agree it's unfortunate, and hope someone can get around to sorting this out. I can't be the only one who runs a machine with auto-login and doesn't want to be prompted for my password every time I log in (which is why I use auto-login.....).

I did try removing the nm entry from the keyring, but it made things worse - then nm wanted the wireless connection password. The funny thing is, the network itself connects up BEFORE I enter the login password; it seems that only the nm applet requires authorization. I could try removing the nm applet, I suppose...

---

### Post by cariboo on 2010-02-16
Why not just remove the keyring password and replace it with a blank one. I would think that would be much easier than removing any programs that need authorization.

---

