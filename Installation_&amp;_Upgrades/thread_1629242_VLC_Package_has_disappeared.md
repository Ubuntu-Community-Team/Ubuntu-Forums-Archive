---
title: "VLC Package has disappeared"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by pauljam20 on 2010-11-23
I had a problem with moving the panel, and in order to be able to move it I had to delete a couple of launchers. I have now lost VLC (Video LAN Converter), it is installed, but has gone from system/preferences/main menu so I can't start it or even put it on the menu or create a launcher. If I use Ubuntu Software Centre to un-install and re-install it it still doesn't appear.

---

### Post by jocko on 2010-11-23
Can you start it from a terminal? (The command is "vlc")
If not, what error message do you get?

---

### Post by pauljam20 on 2010-11-23
> **jocko said:**
> Can you start it from a terminal? (The command is "vlc")
If not, what error message do you get?
Yes - works fine.

---

### Post by jocko on 2010-11-23
Ok, so it's only missing from the menu...
[COLOR=DimGray]Not sure what's the "proper" way of restoring it, but you could probably fix it by copying the vlc.desktop file to your home directory's applications folder. Run this in a terminal:
[/COLOR]```
[COLOR=DimGray]cp /usr/share/applications/rhythmbox.desktop ~/.local/share/applications[/COLOR]
```[COLOR=DimGray]That should bring it back to the menu.[/COLOR]

Edit: The proper way seems to be to REMOVE any vlc.desktop and vlc.desktop.undo-X files in your /home/username/.local/share/applications folder, so this command should do it:
```
rm ~/.local/share/applications/vlc.deskto*
```

---

### Post by theSuperman on 2010-11-23
You can also right click on "Applications" in the taskbar and go to Edit Menus to add/enable/disable programs

---

### Post by jocko on 2010-11-23
> **theSuperman said:**
> You can also right click on "Applications" in the taskbar and go to Edit Menus to add/enable/disable programs
He said in the first post that that did not work (the menu editor can be started from Systems-->preferences-->"Main Menu" or by right clicking anywhere on "Applications", "Places" or "System").

---

### Post by pauljam20 on 2010-11-23
@Jocko Your first command had no effect, but running your second command and de-installing VLC (can't remember the order I did it in) then reinstalling VLC works. A very quick and effective solution - thanks!

15 Dec: I have since had the same problem with Brasero, and this solution works for that as well - after adjusting the filename to match. Looks like it is a general solution to a common problem, well worth remembering.

---

### Post by pauljam20 on 2010-11-23
I would have preferred to sent this as a message but apparently I haven't go enough points. For non-Swedish speakers - it's just a compliment...

@Jocko
Ni läsa mitt budskap före besvara den. Ni kontaktade problemet logiskt. Ni bad mig att göra något. Ni förklarade hur det skall göras i enkla ordalag. Jag önskar alla experter kunde göra detta!

---

### Post by jocko on 2010-11-24
> **pauljam20 said:**
> I would have preferred to sent this as a message but apparently I haven't go enough points. For non-Swedish speakers - it's just a compliment...

@Jocko
Ni läsa mitt budskap före besvara den. Ni kontaktade problemet logiskt. Ni bad mig att göra något. Ni förklarade hur det skall göras i enkla ordalag. Jag önskar alla experter kunde göra detta!
Thanks. I'm no expert, but I like to try to help when I think I can...

---

### Post by nasul on 2010-11-24
I saw that you've found a soution to the problem - the terminal installation.

---

