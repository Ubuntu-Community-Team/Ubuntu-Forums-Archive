---
title: "quakelive mouse not working"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by realzippy on 2010-01-27
Just installed lucid for testing...
in Quakelive my mouse pointer disappears...
in 8.1 /9.1 it works...

Anyone else had this issue?

---

### Post by realzippy on 2010-01-30
Bump.No idea how to fix it...
Anybody running quakelive on Lucid?

---

### Post by MacUntu on 2010-01-30
Give me some minutes, I'll test it.

Edit: works fine with FF and nvidia-current 190.53.

---

### Post by realzippy on 2010-01-30
Thanks.
Will downgrade nvidia (currently running 195.30)..
could you post your xorg.conf's "InputDevice" Section ???

---

### Post by MacUntu on 2010-01-30
My xorg.conf is pretty default:

```
Section "InputDevice"

    # generated from default
    Identifier      "Mouse0"
    Driver          "mouse"
    Option          "Protocol"          "auto"
    Option          "Device"            "/dev/psaux"
    Option          "Emulate3Buttons"   "no"
    Option          "ZAxisMapping"      "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier      "Keyboard0"
    Driver          "kbd"
EndSection
```

Will try 195.30 now.

---

### Post by Starks on 2010-01-30
Quakelive crashes my Firefox.

<__<

---

### Post by MacUntu on 2010-01-30
195.30 works just fine. I'm on 32-bit, if that's different.

Maybe try to uninstall the plugin (plus deleting any leftovers at '~/.mozilla/firefox/<YOURPROFIL>/extensions/quakeliveplugin@idsoftware.com' - don't forget to backup your config :P) and reinstall it?

---

### Post by realzippy on 2010-01-30
No,reinstalling plugin did not help.Also reinstalled FF...
Strange;since it would be a software issue,I could not believe I am the only one who is affected...but same hardware works on Jaunty/Karmic...

---

### Post by MacUntu on 2010-01-30
Strange. :-(

[[img]http://img.xrmb2.net/781034.jpg[/img]](http://img.xrmb2.net/images/781034.png)

Also tested fullscreen mode.

---

### Post by realzippy on 2010-01-30
..did you play yourself?(not sure about your screenshot..)
When I select a gameserver,I do not reach the "joinmatch" screen as usual,
I am dropped into kind of spectators mode directly...(and mouse is gone)

---

### Post by MacUntu on 2010-01-30
Yes, I played a practice map and also joined a CTF server - works same as with FF under Windows.

---

### Post by Asraniel on 2010-01-30
i just installed latest backports in kubuntu 9.10 and now my mouse stoped woring too.. have to restart computer perhaps.

---

### Post by realzippy on 2010-03-24
working since today's updates...

---

