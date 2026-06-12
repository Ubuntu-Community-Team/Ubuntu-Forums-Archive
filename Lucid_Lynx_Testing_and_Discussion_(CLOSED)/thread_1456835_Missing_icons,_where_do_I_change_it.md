---
title: "Missing icons, where do I change it?"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SpinningAround on 2010-04-17
I don't have a single icon in the 'system' menu preference/admin/help/gnome/ubuntu, I also missing icons in the noscript menu in firefox. I had a similar problem in 9.10 but managed to change it problem is that I can't remember where. Some guidance please.

---

### Post by howefield on 2010-04-17
Try pressing Alt + F2 and in the run box type

```
gconf-editor
```

and press enter.

Navigate to  desktop > gnome > interface and place a check beside menus_have_icons. I also check off buttons_have_icons.

---

### Post by Didius Falco on 2010-04-17
Alt-F2  or a Terminal windows and type in ```
gconf-editor
```

Then go to desktop/gnome/interface and tick the radio buttons next to ```
buttons_have_icons
```

and 

```
menus_have_icons
```

Then enjoy your icons!!

Regards,

Didius

---

