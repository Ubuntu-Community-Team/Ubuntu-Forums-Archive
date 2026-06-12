---
title: "how to enable control alt backspace"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mamamia88 on 2009-03-28
for some reason it's not working and i hear it's disabled by default which is stupid imo how can i enable it

---

### Post by jfernyhough on 2009-03-28
$ gksudo gedit /etc/X11/xorg.conf

Add the following to the end of the file:
```
Section "ServerFlags"
    Option        "DontZap"    "off"
EndSection
```

---

### Post by mamamia88 on 2009-03-28
thanks who's genius idea was it to remove cntrl-alt-backspace anyway?  seems like if you don't want to use it don't use it but imo thats one of the things that made ubuntu better than windows in the first place being able to not reboot when the whole system freezes

---

### Post by MacUntu on 2009-03-28
Wasn't it planned to make this easy to bring back via GUI? :(

Honestly, I don't mind enabling it by hand and if it prevents some users from data loss it's ok. It's not like they removed it for good.

---

### Post by tom56 on 2009-03-28
From the release notes:

> Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it in their xorg.conf, or via the command *dontzap --disable*. 

---

### Post by Hairy_Palms on 2009-03-28
you can just use Altgr + sysrq + K instead

---

### Post by ktp on 2009-03-28
> **MacUntu said:**
> Honestly, I don't mind enabling it by hand and if it prevents some users from data loss it's ok. It's not like they removed it for good.

I agree.  I am all for better user experience as long as I am not forced on it and I have way to option to change it if need be.

---

### Post by rburkartjo on 2009-03-28
hair tks for the info i will remember that

---

### Post by SunnyRabbiera on 2009-03-28
I think ctrl alt esc will be set to make an emergency log out now

---

### Post by amano on 2009-03-28
And until the next one steps in having overseen the long and daily resurrected "The Poll" thread:

[COLOR="DarkOrchid"]1) THIS WAS AN UPSTREAM DECISION. CTRL+ALT+BACKSPACE is destined to die out![/COLOR][COLOR="Purple"]

2) USE ALT**GR** + SYSRQ + K
or ALT**GR** + PRINTSCREEN + K instead.[/COLOR]

:guitar:

---

### Post by The Cog on 2009-03-28
My netbook hasn't got a SysRq key.

---

### Post by loomsen on 2009-03-28
Labeled Fn maybe? it's your key for hardwareswitches like altering your display brightness, volume and so on...

---

