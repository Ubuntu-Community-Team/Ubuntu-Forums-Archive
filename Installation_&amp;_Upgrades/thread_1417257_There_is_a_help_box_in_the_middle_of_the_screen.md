---
title: "There is a help box in the middle of the screen"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by stevepett on 2010-02-27
and it won't go away or move.
It is in Ubuntu colours, with 2 side by side boxes and if you type in it, you get help - except on how to move it or close it!
It has an inverted triangle at the top which you would think would close it, but it has no effect.
Please help - I need to see the whole screen!!

Steve

---

### Post by spectralblue on 2010-02-27
Try rebooting or press Alt + PrtScn + K (will log you off and kill all open apps)

---

### Post by stevepett on 2010-02-27
> **spectralblue said:**
> Try rebooting or press Alt + PrtScn + K (will log you off and kill all open apps)


Neither works - the blooming thing is right in the middle of the screen - magnifying glass in the left pane, stopping me seeing anything properly!

Steve

---

### Post by spectralblue on 2010-02-27
Are you able to post a screenshot here?

---

### Post by SecretCode on 2010-02-27
Sounds like the GNOME Do screen. Click on it and press Esc?

Do you have a gnome-do icon in the top panel - sort of purple with a white cog in it. A left click should dismiss the box, right click should have a quit option.

If not, kill the gnome-do process - something like /usr/lib/gnome-do/Do.exe

---

### Post by stevepett on 2010-02-27
[QUOTE=spectralblue;8889874]Are you able to post a screenshot here


I can copy it - but it won't paste - CTRL click etc didn't help either.
Command line prompts don't mean anything - I have only started trying to use Ubunto today when the Windows OS refused to re-install on my laptop.

I suspect it may be one of the free additional programs, so I may have to re-install
Steve

---

### Post by stevepett on 2010-02-27
> **SecretCode said:**
> Sounds like the GNOME Do screen. Click on it and press Esc?

Do you have a gnome-do icon in the top panel - sort of purple with a white cog in it. A left click should dismiss the box, right click should have a quit option.

If not, kill the gnome-do process - something like /usr/lib/gnome-do/Do.exe

Click escape worked third time - THANKS!!

Steve

---

### Post by SecretCode on 2010-02-27
Now that you've got rid of the box, you might want to starting using GNOME Do - it's very neat!

Rather than giving help, it's actually a launcher. Like the windows "Run..." box only more powerful. Just starting typing the first few letters of an application name, document or directory (or various other things) and it'll let you launch it with enter - or press the down arrow for other alternatives, or tab to choose different actions on the selected object.

---

### Post by spectralblue on 2010-02-27
> **SecretCode said:**
> Now that you've got rid of the box, you might want to starting using GNOME Do - it's very neat!

Rather than giving help, it's actually a launcher. Like the windows "Run..." box only more powerful. Just starting typing the first few letters of an application name, document or directory (or various other things) and it'll let you launch it with enter - or press the down arrow for other alternatives, or tab to choose different actions on the selected object.


Ahhh what was I thinking lol! I must be tired haha. Gnome Do is great!

EDIT: @ [stevepett]("http://ubuntuforums.org/member.php?u=561841") you probably installed Gnome Do somehow. The shortcut for it is the Super (Windows Key or Command Key for Mac I believe) + Space Key, then start typing the application you want. You can also click on the arrow in the upper right to change the theme to docky, which looks like the menu in Mac OS, but personally I just like using the search feature. If you really want to remove gnome do follow this: open the terminal by pressing Alt + F2 then type ```
gnome-terminal
```then press enter. then type the following

```
sudo apt-get autoremove gnome-do
```

enter your password, hit enter

When it prompts you, press Y.

---

### Post by stevepett on 2010-02-27
Thank you all - mystery solved!

Steve

---

