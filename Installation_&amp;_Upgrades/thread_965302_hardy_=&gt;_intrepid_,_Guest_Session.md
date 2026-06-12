---
title: "hardy =&gt; intrepid , Guest Session"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by tomcheng76 on 2008-10-31
Hi there,
  Just upgrade from hardy to intrepid (amd64), so far so good.
  Btw, guest session is not workable under the switch user applet
  It just creates a background image wallpaper, gnome wont load.
  After ctrl+alt+bksp , entering the password, i am back.
  How can i solve this problem
Tom

---

### Post by tomcheng76 on 2008-10-31
little bump ~

---

### Post by niyonk on 2008-10-31
Please, no bumping BEFORE at least 3-5 hours. ('little bump' means the same)
You also did not specify your system spec, CPU RAM, to see whether that might be the cause. Also upgrade is either through update manager or a clean install with saved settings.

Cheers! :)

---

### Post by Harmshi on 2008-10-31
When I choose to start a guest session from the FUSA, X restarts, but the screen remains black. Fans are running fast so probably cpu load is high. Sysytem completely locks, no ctrl-alt-backspace possible.

This error occurs for with compiz enabled AND disabled. I've tried to use another login theme, but no result. Does this sound familiar to anyone? Can it be caused by the fglrx driver?

---

### Post by tomcheng76 on 2008-10-31
I upgrade from update manager.

CPU Intel C2D 8200
Ram ADATA DDR2 800 2G x2
Display xFx 8600GT 256M
Mainbroad Gigabyte GA-P35-DS3L

the background image color is the colour specify here
/etc/gdm/PreSession/Default
```

        # Default value
        if [ "x$BACKCOLOR" = "x" ]; then
                BACKCOLOR="#404040"
        fi

```

---

### Post by tomcheng76 on 2008-10-31
Also, disable compiz or not is the same.

---

### Post by tomcheng76 on 2008-11-01
It seems that this solve the problem
reinstall gdm-guest-session package
set Gnome as Default Session in gdmsetup

---

### Post by Harmshi on 2008-11-02
Reinstalling the package didn't change anything for me. System hangs when changing to guest session. Can this be a problem with the fglrx driver?

---

