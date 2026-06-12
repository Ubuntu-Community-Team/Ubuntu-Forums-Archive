---
title: "Karmic -&gt; Lucid; various issues with keyboard shortcuts and window decoration"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by darius.k on 2010-05-01
Good morning everyone :)

After upgrading my Karmic installation to Lucid, I am now experiencing some issues that I cannot fix on my own.

1. Window decoration: regardless of which theme I choose, the window borders do not change, the Ambiance-borders always remain. Additionally the window controls are on the left even though I edited the related key in gnome-config-editor to have them shown on the right and even the appearance preferences shows them on the right.

2. The Super key doesn't work for all shortcuts except Super+E which enables Compiz' Expo function and Super+A which enables Compiz' Scale function. Super+Tab, which is also Compiz' Scale function does not work. Also Super+D to show the desktop doesn't work. I had Mod4+Left (Mod4+Right) to switch workspaces. This is what is shown in gnome-config-editor and the keyboard shortcuts preferences, but switching workspaces only works with Ctrl+Alt+Left (Ctrl+Alt+Right).

3. Keyboard layout is shown in the notification area, how can I hide it?

4. Compiz' screen edge mouse bindings do not work either.

Does anyone else experience these issues? And most importantly: can anyone help me with those? ;)

---

### Post by alvevind on 2010-05-01
> **darius.k said:**
> 1. Window decoration: regardless of which theme I choose, the window borders do not change, the Ambiance-borders always remain. Additionally the window controls are on the left even though I edited the related key in gnome-config-editor to have them shown on the right and even the appearance preferences shows them on the right.

It may be that you must to repeat the config hack every time you switch the theme.

Another easier way to restore the window button position for the default theme is to install the alternative right aligned theme:

Step-by-step procedure:
1. Download the modified theme [http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)
2. Open the menu "System" > "Preferences" > "Appearance"
3. Click the button "Install"
4. Open the folder "Downloads"
5. Select the file "Ambience_Radiance-Right.tar.gz"
6. Click "Open"
7. Select the new theme "Ambiance-right"

You then have both the standard unmodified left-aligned theme and the right-aligned theme available and can easily switch back and forth between them with a single click, and without having to repeat the config hack every time.

(Sorry I can't help you with the other issues, hopefully others can.)

---

### Post by darius.k on 2010-05-01
Thanks for the reply.
I didn't try the right aligned theme, but I suspect it wouldn't change anything as long as I am unable to change the window border, which always remain left-aligned Ambiance regardless of which theme I choose.

---

### Post by alvevind on 2010-05-01
> **darius.k said:**
> Thanks for the reply.
I didn't try the right aligned theme, but I suspect it wouldn't change anything as long as I am unable to change the window border, which always remain left-aligned Ambiance regardless of which theme I choose.
What happens if you do:
1: Open menu "System" > "Preferences" > "Appearance"
2: Click button "Customize"
3: Click tab "Window border"
4: Select another border theme

Does that change it or is it still stuck with the old one?

---

### Post by darius.k on 2010-05-01
Already tried that one, tried it again, it' still stuck with Ambiance. I'm really lost with that one :confused:

---

### Post by Turwaithien on 2010-05-01
I too am missing approximately a fourth of my shortcuts because of the lack of super key shortcuts. :(

But for the buttons, I went into gconf-editor, to apps > metacity > general and changed the value for button_layout to menu:maximize,minimize,close

Now my buttons are on the correct side. :)

---

### Post by darius.k on 2010-05-02
I'm feeling a bit embarrassed right now, because all my issues except #3 fixed themselves after a cold boot. :oops:

I tried rebooting multiple times in the process of trying to fix these issues, but... well I'm a happy camper.

@Turwaithien
Sorry, even though my problems are fixed now, I have no advice for you, because basically I changed absolutely nothing in my configuration. Just changed and reset some of the values, but to no avail up to today's surprise of correct window borders and working super key and mouse binding.

---

