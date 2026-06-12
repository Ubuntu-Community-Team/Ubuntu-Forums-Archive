---
title: "Stuck on desktop after boot, no panels"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by seragx99 on 2011-02-22
I recently installed Ubuntu 10.10 on my laptop and it was running all  smoothly, but all of a sudden when i booted, the only thing i could see  were the desktop wallpaper and mouse icon, no panels, no shortcuts,  nothing, meaning i can do pretty much nothing, i can move the mouse but can't click anything, the last thing i did was  download and goof around with compiz and i was too happy because it  worked and looked really great, even though i didn't want to activate  restricted drivers for my ATI video chipset, but again, it was working  cool and then boom, only wallpaper and mouse, nothing more, please help!


Laptop Sony VPCEE27FL AMD Athlon II 2.1 ghz (64) 4gb RAM

---

### Post by FoxEWolf on 2011-02-22
Press ALT+F2 to bring the run dialog box up. select terminal.
 
in terminal: type
 
[LEFT][COLOR=#ff0000][FONT=Verdana][SIZE=2][COLOR=black]gconftool-2 &#8211;-shutdown (enter)[/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#ff0000][FONT=Verdana][SIZE=2][COLOR=#000000][/COLOR][/SIZE][/FONT][/COLOR] [/LEFT]
[COLOR=#ff0000][FONT=Verdana][LEFT][COLOR=#ff0000][COLOR=black]gconftool &#8211;-recursive-unset /apps/panel (enter)[/COLOR][/COLOR]
[COLOR=#ff0000][COLOR=#000000][/COLOR][/COLOR] [/LEFT]
[COLOR=#ff0000][LEFT][COLOR=#ff0000][FONT=Verdana][SIZE=2][COLOR=black]rm -rf ~/.gconf/apps/panel (enter)[/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#ff0000][FONT=Verdana][SIZE=2][/SIZE][/FONT][/COLOR] [/LEFT]
[COLOR=#ff0000][FONT=Verdana][LEFT][COLOR=#ff0000][FONT=Verdana][SIZE=2][COLOR=black]pkill gnome-panel (enter)[/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#ff0000][FONT=Verdana][SIZE=2][COLOR=#000000][/COLOR][/SIZE][/FONT][/COLOR] 
[COLOR=#ff0000][FONT=Verdana][SIZE=2][COLOR=#000000]NOTE!!!: This will restore the panels to their default settings. I am not sure about your desktop icons though.[/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#ff0000][FONT=Verdana][SIZE=2][COLOR=#000000][/COLOR][/SIZE][/FONT][/COLOR] 
[COLOR=#ff0000][FONT=Verdana][/FONT][/COLOR] [/LEFT]
[/FONT][/COLOR][LEFT][COLOR=#ff0000][FONT=Verdana][SIZE=2][COLOR=#000000][/COLOR][/SIZE][/FONT][/COLOR] 
[COLOR=#ff0000][FONT=Verdana][SIZE=2][COLOR=#000000][/COLOR][/SIZE][/FONT][/COLOR] [/LEFT]
[/COLOR][LEFT][COLOR=#ff0000][COLOR=#000000][/COLOR][/COLOR] 
[COLOR=#ff0000][COLOR=#000000][/COLOR][/COLOR] [/LEFT]
[/FONT][/COLOR]

---

### Post by seragx99 on 2011-02-22
I logged in, tried to run terminal but it doesn't show up, firefox did and here i am, by the way i already tried the recovery console but it doesn't even load, it just gets hung, please help! thanks for the reply : )

---

### Post by Hakunka-Matata on 2011-02-22
try ```
Ctrl Alt T
``` for a terminal while in GDM

---

### Post by FoxEWolf on 2011-02-23
> **Hakunka-Matata said:**
> try ```
Ctrl Alt T
``` for a terminal while in GDM

Yeah... That actually is the better way to get to the terminal. Well I can't always be right. (humble IT moment)

---

### Post by Hakunka-Matata on 2011-02-23
```
Ctrl - Alt - T
```

> Yeah... That actually is the better way to get to the terminal. Well I can't always be right. (humble IT moment)

@FoxEWolf, not to worry, I was using Alt F2 myself until recently, when I saw the 'Ctrl Alt T' posted in these forums a few days ago.  Thought I'd share.  It *IS* about open source, isn't it?

---

### Post by seragx99 on 2011-02-23
No good, tried the CTRl Alt T and nothing, a friend told me to go ctrl alt f5, it only showed the flashing cursor but no option to login and hence no chance to write anything, it's getting creepy : s

---

### Post by Hakunka-Matata on 2011-02-23
sorry to hear that, works for me:  Ubuntu 10.10 32bit Desktop

---

### Post by seragx99 on 2011-02-23
I'm sorry too : s anymore clues guys?

---

### Post by Hakunka-Matata on 2011-02-23
What is your current condition?  Are you able to get into a Terminal?

---

### Post by Hakunka-Matata on 2011-02-23
Of course you need to be able to get to a Terminal to run it.............

```
    gconftool-2 --shutdown

    rm -rf ~/.gconf/apps/panel

    pkill gnome-panel
```

that has always fixed my missing panel problem, I've used it many times.

---

### Post by seragx99 on 2011-02-25
Nope. I'm simply thinking of reinstalling everything.

---

### Post by Hakunka-Matata on 2011-02-25
Have you tried booting to the recovery mode?  Holding down Shift key during boot should open the Grub menu when it gets that far, in case you didn't know.  If  you can get there you may be able to boot to an earlier kernel or to recovery mode.

---

### Post by viipu on 2011-02-26
So you can't get the Virtual Console running? Can you right-click on the desktop? Cause I had a similar situation just today, and those two were the only things that actually worked. If they don't, seems like you might be in big trouble (or maybe your shortcuts have been thoroughly raped?).

Maybe you could try getting a Live CD (USB) and booting through that, get the user config files and post them here? Altho, if it's a new install anyhow maybe you won't mind doing it all over again :P

What worked for me: Virtual Console: [CTRL]+[ALT]+[F2] (Technically anything between F1 and F6, altho I think F1 is special somehow)
If it loads up (takes a few seconds for me at least), log in (as admin), then type
> **lidex said:**
> 
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

Reconfigures the Gnome Display Manager, for me at least brought all my previous settings back but left the problematic clock app out. I've got a bare desktop to begin with so no idea what it does to your icons and shortcuts, sorry.

Typically just made a whole thread about the same thing and only then found this. But mine's [here]("http://ubuntuforums.org/showthread.php?t=1695471"), anyhow.

Hope you manage to fix it!

---

