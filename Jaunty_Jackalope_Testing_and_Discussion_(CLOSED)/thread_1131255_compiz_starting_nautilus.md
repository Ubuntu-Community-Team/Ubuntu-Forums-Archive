---
title: "compiz starting nautilus"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rplantz on 2009-04-20
I installed 9.04RC and lost my Desktop icon display. I created another user and her Desktop is fine. I've found a difference in the ~/.compiz/sessions/ files.

Does not display Desktop:
```

<?xml version="1.0" encoding="UTF-8"?>
<compiz_session id="108e9cd46de08c5c69124025652177884300000035350030">
</compiz_session>

```

Displays Desktop:
```

<?xml version="1.0" encoding="UTF-8"?>
<compiz_session id="10c3395473266dd896124026085762076200000069780025">
  <window id="10c3395473266dd896124026085764288100000069780027" title="x-nautilus-desktop" class="Nautilus" name="desktop_window" command="nautilus">
    <geometry x="0" y="0" width="1280" height="1024"/>
  </window>
</compiz_session>

```

I already figured out that starting nautilus manually paints my Desktop icons. It's clear that I have to tell compiz to start nautilus for me.

Can anyone tell me how to fix my compiz configuration so that it starts nautilus for me in my account?

---

### Post by uBeer on 2009-04-20
I seem to have this problem too. When my session starts the icons are displayed, but once I click them they disappear and all desktop functionality is then lost.

Is that what you're seeing too?

---

### Post by rplantz on 2009-04-20
> **uBeer said:**
> I seem to have this problem too. When my session starts the icons are displayed, but once I click them they disappear and all desktop functionality is then lost.

Is that what you're seeing too?

No. I don't recall exactly when me Desktop icons went away, but it was some time after I upgraded to 9.04RC (from 8.10). The strange thing is that it works just fine on my other computer (a laptop) and when I create a new user on this computer.

Anyway, coffeecat suggested a technique at [http://ubuntuforums.org/showthread.php?p=7109646#post7109646](http://ubuntuforums.org/showthread.php?p=7109646#post7109646). I tried it, and it worked for me. If I can paraphrase:

1. Use ps -A | grep naut (in a terminal window) to see if nautilus is running. If not, start it by simply typing nautilus.

For me, that brought back my Desktop icons. If this seems to be working for you, then

2. Use System -> Preferences -> Startup Applications and select the Options tab. Check the box next to Automatically remember ...

3. Do NOT quite the terminal that you started nautilus in. This will kill nautilus. Quit all other applications, then log out.

4. Log back in.

Now you can remove the check in the Automatically remember... box.

---

