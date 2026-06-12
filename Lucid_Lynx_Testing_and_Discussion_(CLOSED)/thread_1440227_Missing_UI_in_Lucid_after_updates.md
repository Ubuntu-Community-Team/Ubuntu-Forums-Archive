---
title: "Missing UI in Lucid after updates"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by serosis on 2010-03-27
After updating a few minutes ago I lose a crucial part of the UI:

[[IMG]http://img687.imageshack.us/img687/2466/screenshotkkn.th.png[/IMG]](http://img687.imageshack.us/i/screenshotkkn.png/)

Not only is the bar along the top of the windows gone but the windows don't even show up on the "taskbar".

On the restart after I updated it said something about not finding plymouth, might be relevant but I don't know.

I know there is a forum specifically for Lucid but I'm too tired to find it, I'm about this | | close to passing out in my chair. :)

---

### Post by Helkaluin on 2010-03-27
Looks like Compiz not loading the 'Window decoration' plug-in for me.

Try enabling and checking the settings for that?

---

### Post by Mark Phelps on 2010-03-27
Lucid is still in beta testing.  Please post your Lucid-related issues to the correct forum ... Development & Programming, Luci Lynx Testing.

I'm requesting the Mods move this thread to that subforum.  Look for any replies there.

---

### Post by serosis on 2010-03-27
Anybody have an idea on how to fix this?

Short of a complete re-install of Lucid?

---

### Post by Sophont on 2010-03-28
> **serosis said:**
> Anybody have an idea on how to fix this?

Short of a complete re-install of Lucid?

Yup - looks like a Compiz problem that used to happen a lot in the past and only rarely now.

A fix:
Go to Synaptics and install fusion-icon.
Alternatively via command line:
```
sudo aptitude install fusion-icon
```

Shows up under Applications -> System Tools

When you run it you get an icon in the notification area.
Right-click on that and select "Reload Window Manager"
If that fails you can "Select Window Manager" and toggle between Metacity and Compiz.
With Metacity you will surely get your window decorations back and switching back to Compiz will probably also restore them to Compiz.

Worked for me.
Used to happen a lot when Compiz was new - by now I get it about once every few months.

---

