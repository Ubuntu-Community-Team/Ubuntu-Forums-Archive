---
title: "Karmic 9.10 login screen colors reset"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nasp on 2009-10-24
I just installed Karmic Koala and i was messing around the accessibility options in the login screen. I checked the "use contrasted colors" options which switched the UI elements to a lighter theme but when i unchecked it it switched back to another lighter color theme and not the original dark on which look way better IMO.

Anyone knows how i can reset the original colors? I tried rebooting and checking and unchecking the option but it didn't fix it.

Is this a known issue? Else I'll report it but i was wondering if there was a way to fix it since Karmic removed the "Login Screen" modification GUI.

Thanks a lot!

---

### Post by nasp on 2009-10-24
Thanks for the move. Anyone has an idea on this one?

---

### Post by ranch hand on 2009-10-25
Check to see what is in the file /usr/share/images/xsplash.

The login screen uses the background bg_2560x1600 in that file.

---

### Post by nasp on 2009-10-25
Yeah i can see those are the images used on the login.

However the UI image are ok on the screen. What i mean is that the GUI theme (dialog boxes, panel, buttons, input) in the login screen is changed to a lighter color one instead of the darker one.

It's like if i had changed the GUI theme with the Preference->Appearance|Theme but only for the GUI in the login screen and i can't set it back to the original because even if the contrast option is unchecked it keeps switching between lighter color themes instead of the original one.

UI is supposed to look like that : [IMG]http://i37.tinypic.com/wraxxl.jpg[/IMG]
And since i pressed the accessibility button and checked, unchecked the contrast option I'm stuck with white and blue GUI.

I'll investigate in those folder, it must be a file specifying the login screen gnome GUI theme,

---

### Post by ranch hand on 2009-10-25
I misunderstood you.  That color may be set by a script, I don't know.  I don't know where it would be either.

---

### Post by nasp on 2009-10-25
Ok found  [something]("http://www.lathund.nu/2009/10/16/anvand-samma-tema-i-gdm-som-for-gnome-i-ubuntu-9-10/").

```
sudo -u gdm gconftool-2 –set –type string –set /desktop/gnome/interface/gtk_theme <GTK Theme>
```

Now to find the name of the original gtk theme.

---

### Post by ranch hand on 2009-10-25
Hey, that is great.

Themes are, I think, in /usr/share but I don't remember after that.  /local is one but I think there are 3 sub directories in there with theme stuff.

---

### Post by nasp on 2009-10-25
Gotcha!

```
sudo -u gdm gconftool-2 -t string -s /apps/metacity/general/theme HumanLogin
sudo -u gdm gconftool-2 -t string -s /desktop/gnome/interface/gtk_theme HumanLogin
sudo -u gdm gconftool-2 -t string -s /desktop/gnome/interface/icon_theme HumanLogin
```

[Report]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/446439")

---

### Post by ranch hand on 2009-10-25
WOW, I think I will play with that.

Thanks

---

