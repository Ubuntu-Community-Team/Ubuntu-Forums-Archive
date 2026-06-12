---
title: "Start xububtu straight to desktop"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by s-p-constantine on 2014-05-02
Hi,

I recently installed xubunbtu 14.04 to my daughter's desktop.

During the install I erroneously knocked the keyboard at the point where it asks whether you want to start/login using a password or not.

I now have to enter a password via a login screen, which is not what I want.

I've searched and searched to no avail; it's nothing to do with Settings > Users > Change User Password [Don't ask for password at login].

Which config file do I need to tweak so that my PC boots straight into my daughter's user session, by-passing a login screen?

Thanks for any help - Steven.

---

### Post by HiRez_L on 2014-05-02
Try this:

sudo leafpad /etc/lightdm/lightdm.conf
[COLOR=#000000][FONT=Arial]Add the following line to the end and save...[/FONT][/COLOR]
autologin-user=YourDesiredAutoLoginUserName

---

### Post by grahammechanical on 2014-05-02
There should also be a utility somewhere in the Xubuntu menu system dealing with User Accounts and there you should be able to turn Automatic Login On and Off. I cannot give better directions as I am not at the moment using Xubuntu 14.04 although I do have it installed.

The installer usually defaults to requiring a password to log in. You did set a password, didn't you? We need to set a password and to confirm it even if we intend to automatically log in. It may be simpler to re-install.

Regards.

---

### Post by s-p-constantine on 2014-05-02
> **HiRez_L said:**
> Try this:

sudo leafpad /etc/lightdm/lightdm.conf
[COLOR=#000000][FONT=Arial]Add the following line to the end and save...[/FONT][/COLOR]
autologin-user=YourDesiredAutoLoginUserName

Thank you.

Using my daughter's PC to search the WWW, I'd read several posts saying the same thing - but when I checked /etc/lightdm I found that lightdm.conf was not present.

Reading this post on my xubuntu laptop (64bit install *vs*. my daughter's 32bit), I see that MY machine does have that .conf file.

I therefore created the lightdm.conf file on my daughter's machine, using:
```

[SeatDefaults]
autologin-guest=false
autologin-user=>>my daughter's name<<
autologin-user-timeout=0
autologin-session=lightdm-autologin

```

That worked a treat.

I have no idea why that file should be missing on my daughter's fresh (32bit) install, but be present on my fresh (64bit) install.

Anyway - sorted, thank you!

---

