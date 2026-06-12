---
title: "First root auth after Auto-login kicks me out to login manually"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-02-28
I've noticed this since I upgraded from Ubuntu 9.10, but I kept thinking it would be fixed with an update by now. I couldn't find any other mention of this problem anywhere, but I'm not exactly sure what to search for either.

Here is what happens:
1. I start Ubuntu and I have it setup to auto-login, so it loads my desktop and all seems well.
2. I open Update Manager, click check for updates then enter my password. This is where it immediately crashes gnome or something and kicks me out to the login screen.
3. Log in manually, everything works fine from this point forward.

I also noticed another thing. If I open empathy first thing after an auto-login, it says that the key or auth couldn't be obtained from the keyring. I clicked cancel (several times, I assume once per chat account registered) and it crashed gnome just like checking for updates did. Logging in manually had the same results as before as well.

Any idea if this is known or how I can fix it?

---

### Post by VMC on 2010-02-28
> **kyleabaker said:**
> 
I also noticed another thing. If I open empathy first thing after an auto-login, it says that the key or auth couldn't be obtained from the keyring. I clicked cancel (several times, I assume once per chat account registered) and it crashed gnome just like checking for updates did. Logging in manually had the same results as before as well.

Any idea if this is known or how I can fix it?

Regarding keyring. In the past if I remove "~/.gnome2/keyring" then it works again. Rename it to be sure. See if it rebuilds the folder/

---

### Post by Slug71 on 2010-02-28
Yeh i had been getting this too. I just disabled the auto-login for a while and was going to re-enable it to see if that fixed it but never got around to it.

Today i booted up and went to login and enter password and then it went back to login screen again so i had to do it again. weird. 

Perhaps time for a bug?

---

### Post by moomex on 2010-02-28
This is a Plymouth bug... The problem is fixed by removing plymouth
```
sudo apt-get remove plymouth
```

---

### Post by kyleabaker on 2010-03-26
With plymouth removed, I'm still getting prompted on login to enter my password for the keyring as soon as I start Empathy or Gwibber.

It no longer kicks me out to the login screen, but it does still prompt for the password which defeats the purpose of me setting it to auto-login.

Any ideas? Should I still attempt rename/deleting the keyring folder/files?

---

