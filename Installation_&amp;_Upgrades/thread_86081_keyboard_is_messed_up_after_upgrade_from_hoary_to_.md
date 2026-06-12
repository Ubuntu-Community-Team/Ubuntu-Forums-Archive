---
title: "keyboard is messed up after upgrade from hoary to breezy"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by metafor on 2005-11-04
it seems that i am not the only one having this problem, but none of the solution mentioned in other threads helped me. also installing the files libxkbfile1_7.0.0-3_i386.deb and xkeyboard-config_0.6-6_all.deb had no effect. the xorg.conf is set properly but if i log in and start gnome i receive the same error message from xkb. it happens on my laptop and my desktop, exactly the same. 

[INDENT]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/INDENT]

so it did as mentioned, thats my output
[INDENT]xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "de_CH", "nodeadkeys", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "de_CH", "nodeadkeys", ""[/INDENT]

and the other one:
[INDENT]
/keyboard/kbd
 layouts = [us,ch       de_nodeadkeys]
 model = pc105
 overrideSettings = false
 options = [grp grp:alts_toggle]
[/INDENT]

it seems that gnome just ignores the keyboard layout. 
i realised that i actually have no preview picture in gnome, in hoary i can remember that is saw the actual keyboard layout in black with some red.
now the keyboard picture is blank. are all the layouts missing?

i try to set it manually which gives me this error.
[INDENT]setxkbmap -layout 'de_CH' -model pc105 
Error loading new keyboard description [/INDENT]

i also reconfigured xorg. no success. it would be quite helpfull to have your language supported. i do not know what to do now. just writing text is now impossible which actually prevents me of having some of my work done. 
so i am quite desperate at the moment. 

any help welcome.

---

### Post by mulino on 2005-11-05
[QUOTE=metafor]it seems that i am not the only one having this problem, but 

i try to set it manually which gives me this error.
[INDENT]setxkbmap -layout 'de_CH' -model pc105 
Error loading new keyboard description [/INDENT]

any help welcome.[/QUOTE]

Try run setxkbmap with no parameters. This works for me as workaround although my keyboard is also not set correct in GNOME. My xorg.conf should also be ok.

Salids, mulino

---

### Post by metafor on 2005-11-06
thanks for your hint, but i already tried. i get this error:
root@ubuntu:/home/metafor # setxkbmap
Error loading new keyboard description

doesn't matter if i am root or user.

is there any other solution?

---

### Post by metafor on 2005-11-08
found a solution for my problem: 
i reinstalled the keyboard config according to this post 
[http://www.ubuntuforums.org/showthread.php?t=76261](http://www.ubuntuforums.org/showthread.php?t=76261)

still keyboard switch via gnome-settings was not possible, 
but i figured out, that somehow the keyboard description 
for swissgerman changed, i used de_CH in my xorg.conf 
before which can not be found with setkbmap. 

if i try setxkbmap "ch" i have the swiss german keyboard.

---

### Post by deleta on 2005-11-10
I don't know if I am having the exact same problem.  Where you able to log in? I have a a Thinkpad T42 and just upgraded from Hoary to Breezie (5.10) using Synaptic.  I can't even log in.  I can't type in anything at the login prompt because the keyboard does not work.  If I press the caps lock the system recognizes it and the mouse also works.  The command line interface also works and recognizes my Spanish keyboard perfectly. I tried plugging in an external USB (English) keyboard.  It was recognized OK and worked fine in the command line but, once again, it did not work in the login screen.

Any ideas?

Thank you,

Diego

---

### Post by deleta on 2005-11-10
I have an update:

For whatever it is worth, on the login prompt I was able to type something.  When I type SHIFT X, "(" comes out.  When I type ":" (colon), "$" comes out.  The colon in my keyboard is on top of the period "." (meaning I get it when I type SHIFT "."). When I type "_", which is on top of "-" (meaning, I type SHIFT "-"), I get ")".  This is not a US layout either because I am looking at a US keyboard and the period is in the same place, and the US "/" is where the Spanish "-" is.  So I don't think it is a keyboard layout problem only.

I don't know if this extra info helps anyone trying help me figure out what the heck is going on.

Diego

---

### Post by metafor on 2005-11-16
thanks for your info. seems also quite wired your problem...
but for me it's definetly just the layout, as i always have normal
us keyboardlayout if the swiss one is failing. at the moment i just
set the command in my gnome-sessions so i do not have to type
all the time. hope this keyboardprblems will be fixed sooner or later
as it is a serious one. 

so let's wait and apt-get upgrade if the time is right...

i am sorry that i can't help you with your problem. as i did not stumble
over something similar. try to use passwords without characters which
are moving on different layouts, i now not really secure but at least 
you will be able to login.

---

### Post by Chaneau on 2005-12-29
Hello all 

I just had the same problem: my HD had some problem so I put a new one then realised that I only had a hoary CD (the breezy one was at work) so I installed from CD then updated to breezy and my keyboard was not very functionnal in fact I was unabled to use the functions keys etc after some searching I discovered that somehow the pc file in /etc/X11/xkb/symbols was created as a directory and not a file (very very strange) so I remove it (using rm -f) and reinstall it from the  xkeyboard-config package and everything was fine.

The day after I reinstalled with the breezy cd and the problem did not occur

---

