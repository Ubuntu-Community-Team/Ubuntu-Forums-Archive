---
title: "[SOLVED] No window borders without desktop effects"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by El_Matthews on 2007-04-23
Hello,

Just upgraded to Feisty and all window frames have disappeared in the standard mode. as soon as I enable desktop effects the are coming back but all my desktops etc are also receiving window borders which I don't want.

any idea what's going on or where to start?

First make it work without desktop effects and than with the enabled.

PS: I had compiz and beryl installed and working before.

---

### Post by Spr0k3t on 2007-04-23
If you are using an nVidia card, then you need to do the following:

```
1. Backup your /etc/X11/xorg.conf
2. Edit your xorg.conf
    A. In the Screen0 section add the following:
        Option "AddARGBGLXVisuals" "True"
    B. Save new xorg.conf
3. Restart X
```

If your xorg.conf already has the option line, post your xorg.conf in a reply so others can help.

If you have an ATI card... I'm not sure what steps are next.

---

### Post by El_Matthews on 2007-04-23
thanks, I will test this this evening and let you know the results

---

### Post by Jerry Brimacombe on 2007-04-23
Sorry to hijack the thread but I have exactly the same problem, my xorg.conf has the line:

        Option "AddARGBGLXVisuals" "True"

it's in the screen section is this the same as screen0 ?

Please find attached the rest of my xorg.conf

If I log into Gnome using the Falisafe it correctly works. One other strange effect is that when I log in normally the small message stays in the centre of the screen - unless I click on it when it disappears.

>>PS: I had compiz and beryl installed and working before.

I also used to have Compiz and beryl working before

Any help would be much apreaciated.
.

---

### Post by El_Matthews on 2007-04-23
Indeed I also have the line. what's strange is when I log on with an other user I don't have the problem. All borders appear correctly.

Any help please

---

### Post by Yuzem on 2007-04-23
You can try this:

```
metacity --replace&
sudo killall emerald
```

Then enable Desktop Effects
If it works go to Preferences > Sessions > Startup programs
Uncheck emerald

---

### Post by rscarriere on 2007-04-23
> **Spr0k3t said:**
> If you are using an nVidia card, then you need to do the following:

```
1. Backup your /etc/X11/xorg.conf
2. Edit your xorg.conf
    A. In the Screen0 section add the following:
        Option "AddARGBGLXVisuals" "True"
    B. Save new xorg.conf
3. Restart X
```

If your xorg.conf already has the option line, post your xorg.conf in a reply so others can help.

If you have an ATI card... I'm not sure what steps are next.

Worked for me!  Thanks Spr0k3t

---

### Post by El_Matthews on 2007-04-24
> **Yuzem said:**
> You can try this:

```
metacity --replace
sudo killall emerald
```

Then enable Desktop Effects
If it works go to Preferences > Sessions > Startup programs
Uncheck emerald

"metacity --replace" starts the window borders again. Any idea why this isn't done by default anymore? Can I check somewhere everything that's started after logon (all scripts executed by gnome window manager). If I could do this I could compare it with a working users.

PS: I already compared everything found in session but that's the same for both users.

---

### Post by ggore on 2007-04-24
I have Feisty installed, the NVIDIA drivers are working, all the lines present in xorg.conf  that are suggested in the above posts, but when I Enable Desktop Effects, all the window borders disappear.   When I type metacity --replace in a terminal, this disables the desktop effects and brings back the borders.   Same thing happens when Beryl is installed, which was working fine before I did the upgrade to Feisty.    I reinstalled Beryl after the upgrade but that didn't help.   
Thanks for any ideas.

---

### Post by Cannaregio on 2007-04-24
Same here with Feisty on a Nvidia GeForce 6200SE
I even tried all the following lines (found on [other threads]("http://ubuntuforums.org/showthread.php?t=420047"))

```
 
# added 240407
Option "AddARGBGLCVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"
Option "XAANoOffscreenPixmaps" "true" 
# /added 240407

```

Noway, as soon as compiz/beryl is enabled the windows have no buttons/titlebar, you cannot move them.
Have to execute
```
 metacity --replace 
```
to get back to normal
Will keep on searching and will post back as soon as I find out what's going on.

Btw, shouldn't the thread name be 
"No window borders WITH desktop effects"?

---

### Post by DarkN00b on 2007-04-24
First, you need to make sure that in Section "Module" of your xorg.conf contains the following lines (the ones in bold):

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	**Load	"dri"**
	**Load	"dre"**
	Load	"extmod"
	Load	"freetype"
	**Load	"glx"**
	Load	"int10"
	Load	"vbe"
EndSection
```
This will fix if this problem for *most* people with this problem.

Also, make sure that this:

```
Section "DRI"
	Mode	0666
EndSection
```

is the last thing a the end of xorg.conf.

[COLOR="Red"]EDIT[/COLOR]
OOPS, I just went back and reread your first post and realized this won't help you much. You have no window borders because Metacity isn't running. Try typing metacity or metacity -- replace into a terminal.

---

### Post by Yuzem on 2007-04-24
Edit: The following should work if you can move windows (alt+clic) but the borders are trasparents.

Desktop Effects uses compiz. If you have emerald running compiz will fail, see here:
[http://forum.compiz.org/viewtopic.php?t=732&highlight=feisty](http://forum.compiz.org/viewtopic.php?t=732&highlight=feisty)

You can try this:

```
gtk-window-decorator --replace&
compiz --replace&
```

The first line will replace the window decorator and the second one the window manager.
That should give you Desktop Effects.

---

### Post by El_Matthews on 2007-04-25
Gents,

I think we have lost track of the original problem here. 

The problem is that I have no window decoration when I log on, as soon as I enable desktop effect I get window borders. This mans that nvidia driver etc are configured correctly.

To make it work without "desktop effects enabled" I have to do "metacity --replace". I have no emerald running.

How can I find everything that is started after I log on and compare this with a working user?
I need something to log the "logon process" to know what is started from where.

PS : I moved my profile dir and now everything is ok but I lost all my settings and I would like to avoid this in the future.

---

### Post by DarkN00b on 2007-04-25
Try this. Make sure you have Metacity running and go to System->Preferences->Sessions. Now click the Session Options tab. Finally, click Save the current session. 

That should solve your problem...hopefully.

---

### Post by Yuzem on 2007-04-25
There was an error on my post.

Now it is:
```
gtk-window-decorator --replace&
compiz --replace&
```

---

### Post by Rhune on 2007-04-29
> **El_Matthews said:**
> Gents,

I think we have lost track of the original problem here. 

The problem is that I have no window decoration when I log on, as soon as I enable desktop effect I get window borders. This mans that nvidia driver etc are configured correctly.

To make it work without "desktop effects enabled" I have to do "metacity --replace". I have no emerald running.


Partially found the answer elsewhere on the forum (thanks wwitzke) and after some fiddeling and testing I think I pinpointed the casue of this issue (that is Metacity not starting thus leaving you with no window borders). 

It's NOT related to nVidia drivers, ATI drivers, Beryl, Compiz or 3D desktops as most forum posts suggests.

It seems like a bug in the saving of sessions (in the .gnome2/session file). If the "Save sessions when logging out" in Prefs->Sessions is enabled and you have a Firefox running, the session data gets saved incorrectly and Metacity won't start when you log back in. Manually saving the session (by clicking the "Save current session" button) seems to work though. I'm not sure if this bug includes more apps than Firefox, but one guess is that all apps that's not session aware will cause the same problem.

So, your options would be:
1. Enable automatic session saving upon logout but be sure to kill all Firefoxes before logging out (or use Epiphany instead since it's session aware).

or

2. Save your session manually ones it suits your needs, then disable the automatic session saving function and use Firefox normally.

Hope this helps!

---

### Post by mrojas73 on 2007-04-29
> **rscarriere said:**
> Worked for me!  Thanks Spr0k3t

Worked for me too!

Thak you!

---

