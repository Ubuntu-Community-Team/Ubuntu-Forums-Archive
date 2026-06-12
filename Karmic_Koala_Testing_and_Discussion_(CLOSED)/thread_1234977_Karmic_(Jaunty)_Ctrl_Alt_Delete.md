---
title: "Karmic (Jaunty?) Ctrl Alt Delete"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by AxelMan0 on 2009-08-08
I'm using Karmic alpha 3 right now and when I press ctrl alt delete it doesn't bring up the log out menu, it instead brings up the shut down menu. I have a power button for this--I find it rather silly to have two keyboard hotkeys bringing up the same menu. My keyboard hotkey config tells me ctrl alt delete is set to log out. I used Jaunty for a while but it crashed every ten minutes and I don't remember if this issue was present in that version or not (I had moved back to Intrepid before giving this alpha a shot). Is there any way to fix this?

---

### Post by overdrank on 2009-08-08
Moved to Karmic Koala Testing and Discussion

---

### Post by phenest on 2009-08-08
Quite right, it does. If you disable it Keyboard Shortcuts, it stops working altogether, which I think proves that nothing is conflicting with it. It is simply invoking the wrong dialog.

I'll see if there's a bug report.

EDIT: Which indeed there is: [bug 401372]("https://bugs.launchpad.net/ubuntu/+bug/401372")

I have confirmed it too.

---

### Post by phenest on 2009-08-08
Interesting to note that, in Configuration Editor apps/gnome_settings_daemon/keybindings, Ctrl/Alt/Delete comes under 'power' rather than 'logout'.

---

### Post by lswb on 2009-08-08
Jaunty is the same way, it appears to be an unintended consequence of making logout/switch user separate from the shutdown dialog. Personally I think the old unified logout/shutdown dialog from hardy and earlier was the easiest and most user friendly. My understanding is that the current way is the "gnome way" and the gnome developers decided that 6 options on a single dialog was too confusing for normal users.

---

### Post by ibuclaw on 2009-08-08
As a workaround, do the following:

Press **Alt+F2** and type in:
```
gconf-editor
```
Browse to the following key: **/apps/gnome_settings_daemon/keybindings/power**

Double click on the key, and highlight the value, and press **Delete**, then press "OK" to leave, and it should now be blank.

Close gconf-editor.

Press **Alt+F2** and copy the following text into the Run Command box:
```
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_1 "gnome-session-save --kill"
```
Press **Alt+F2** again, and the same for this text too:
```
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_1 "<Control><Alt>Delete"
```

Control+Alt+Delete should now work as you expect it.

Regards
Iain

---

### Post by phenest on 2009-08-08
Or, even easier, is to do it from the Keyboard Shortcuts applet. Go to logon and double click, press Backspace to disable the shortcut. Click Add, enter Logout as name, and gnome-session-save --kill as the command, and click apply. Then highlight the new Logout and choose Ctrl/Alt/Delete for the shortcut. Et voila!

---

### Post by AxelMan0 on 2009-08-08
Thanks for the fast replies! This is such a trivial problem for alpha software, I'm really suprised overall--this is the most stable version of ubuntu I've tried yet. And it's ALPHA lol. Can't wait for the full release.

---

### Post by ibuclaw on 2009-08-09
> **phenest said:**
> Or, even easier, is to do it from the Keyboard Shortcuts applet. Go to logon and double click, press Backspace to disable the shortcut. Click Add, enter Logout as name, and gnome-session-save --kill as the command, and click apply. Then highlight the new Logout and choose Ctrl/Alt/Delete for the shortcut. Et voila!

Oh I see ... didn't know you could do that.


Well, since we are on the Keyboard Shortcuts applet then, you **could** make this change too:

Press **Alt+F2** and type in
```
gksudo gedit /usr/share/gconf/schemas/apps_gnome_settings_daemon_keybindings.schemas
```

And locate the following section about 20% down the file:
[PHP]
        <schema>
            <key>/schemas/apps/gnome_settings_daemon/keybindings/power</key>
            <applyto>/apps/gnome_settings_daemon/keybindings/power</applyto>
            <type>string</type>
            <default>&lt;Control&gt;&lt;Alt&gt;Delete</default>
            <gettext_domain>gnome-settings-daemon</gettext_domain>
            <locale name="C">
                <short>Log out</short>
                <long>Binding to log out.</long>
            </locale>
        </schema>
[/PHP]

And change to the following:
[PHP]
        <schema>
            <key>/schemas/apps/gnome_settings_daemon/keybindings/power</key>
            <applyto>/apps/gnome_settings_daemon/keybindings/power</applyto>
            <type>string</type>
            <default></default>
            <gettext_domain>gnome-settings-daemon</gettext_domain>
            <locale name="C">
                <short>Shutdown</short>
                <long>Binding to shutdown.</long>
            </locale>
        </schema>
[/PHP]
Then save and quit.

That should prevent confusion with what the feature does too, as "log out" is rather contrary to what it actually does.

Regards
Iain

---

### Post by phenest on 2009-08-09
There should still be a shortcut for logout though. I use AWN instead of the gnome-panels. This means no access to any button for logging out. Even the AWN applet for logout, only invokes the shutdown dialog.

---

### Post by wayne_cat on 2009-08-09
> **phenest said:**
> There should still be a shortcut for logout though. I use AWN instead of the gnome-panels. This means no access to any button for logging out. Even the AWN applet for logout, only invokes the shutdown dialog.

Maybe it is missing because the fast-user-switch-applet and gdm-guest-session are incomplete at the moment ... I'm not sure ...but ... did not one of these functions
added the shortcut to logout?

---

### Post by phenest on 2009-08-09
> **wayne_cat said:**
> ... the fast-user-switch-applet and gdm-guest-session are incomplete at the moment ... 

Maybe, but I don't use these applets because I don't use gnome-panels. But, it's already been said that Ctrl-Alt-Delete doesn't logout in Jaunty neither. Intentional? A bug? I'm not sure.

---

### Post by lswb on 2009-08-09
> **phenest said:**
> Maybe, but I don't use these applets because I don't use gnome-panels. But, it's already been said that Ctrl-Alt-Delete doesn't logout in Jaunty neither. Intentional? A bug? I'm not sure.

I don't know that it could realy be called a bug, it is more of a design mistake IMHO. With the old unified shutdown/logout applet, ctrl-alt-delete (as well as the power button) brought up a single dialog with 6 choices: shutdown, restart, suspend, hibernate, logout, and switch user. Personally I preferred having these choices together and accessible with a single hotkey. This dialog was traditionally called the logout dialog, although it also contained power choices of shutdown, restart, etc.

When the powers that be decided to split logout/switch user from the power options of shutdown, restart, etc, the ctrl-alt-delete key stayed with the power options, leaving logout/switch user without a default hotkey. Part of the reason this was overlooked, I believe, was the excitement over the shiny new Fast User Switcher Applet and guest account.

---

### Post by phenest on 2009-08-10
> **lswb said:**
> I don't know that it could realy be called a bug, it is more of a design mistake IMHO.

Thinking about it, this is a papercut. This could be fixed by the devs in no time. Have the Ctrl/Alt/Delete shortcut called Shutdown instead, and add another for Logout. It doesn't matter what the shortcut is, because the user can change it.

---

