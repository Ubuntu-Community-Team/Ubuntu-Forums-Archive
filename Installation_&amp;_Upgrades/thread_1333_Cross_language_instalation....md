---
title: "Cross language instalation..."
date: 2004-10-20
forum: Installation &amp; Upgrades
---

### Post by latrine on 2004-10-20
hello

I ubunted myself for the first time yesterday... it hasn't been a trivial experinence as I could not get anything to work properly....

A first question is...

I want to install ubunto in english, but i live in Portugal and even if I choose "other" in country selection, Portugal isn't listed. 

Is it possible to do this? 
Have an english instalations with localization for Portugal and a portuguese keyboard? wich are the steps to do this correctly?

have fun
Latz

---

### Post by hashimoto on 2004-10-20
During install (boot with expert option) you can select which language and which keyboard to use. 

I myself have english system with finnish keyboard 'cause I'm used to engllish system and couldn't make any sense of the translations... After installation I guess you can just aptget, but I haven't tried, though.

Hashimoto

---

### Post by im_ka on 2004-10-20
you can install ubuntu in english and then set your keyboard settings of x. just make sure you have the same keyboard settings in gnome (computer/desktop preferences/keyboard), otherwise gnome will complain about not having the same keyboard settings as x (it did at least complain in the preview release)

you can manually edit "/etc/X11/XF86Config-4" or you can reconfigure x by doing

```
sudo dpkg-reconfigure xserver-xfree86
```

it's handy to run dpkg-reconfigure if you have more x things to set up (screen resolution, video card, maybe some special mouse settings,...).

hope this helps

---

### Post by latrine on 2004-10-21
It worked.. thxs

---

