---
title: "[SOLVED] Keybinding issue in Intrepid"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by the real omni on 2008-09-30
I just updated last night from 8.04 to 8.10 alpha 5

One of the problems I've noticed is that my keybinding to launch nautilus doesn't seem to work anymore.

gconf-editor:

 apps -> metacity -> global_keybindings -> run_command_2  :  <SUPER>F

 apps -> metacity -> keybinding_commands -> command_2  :  nautilus

That worked just fine in Hardy, but having updated to Intrepid nothing happens whatsoever when I press <SUPER>F

I've tried changing the keybinding to other keys like <SUPER>D, <SUPER>N, <SUPER>Q, etc and nothing seems to make it work.

If I use system -> preferences -> keyboard shortcuts there's an option to set a keybinding for 'Home folder' but it doesn't let me use the super key as a modifier (if I press the super key, it sets the keybinding as <Super_L> and doesn't wait for any extra key so there's no way for me to set it as <SUPER>F afaik) so I can only use something like CTRL+ALT+F. Here's the weird thing - if I do use something like CTRL+ALT+F for the 'Home folder' keyboard shortcut, it works! 

I know it's not an issue with <SUPER>(key) keybindings in general, as I have a bunch of other global keybindings using <SUPER>(key) like <SUPER>W for a web browser, <SUPER>T for terminal, etc, and all of those work like a charm. It seems that it's only when trying to launch Nautilus that this bug comes into play.

So can anyone tell my why Intrepid would outright refuse to launch nautilus with a <SUPER>(key) keybinding, but it cooperates when using a CTRL+ALT(key) keybinding? 

More importantly, can anyone tell my how to smack Intrepid upside the head and tell it to do what I say? ;)

---

### Post by the real omni on 2008-09-30
Just tried something and the results confused me even further!

Since I know <SUPER>W successfully launches a web browser every time, I tried setting my firefox global keybinding to <SUPER>F and changed the nautilus global keybinding to <SUPER>W

Now NEITHER of those work! <SUPER>F won't launch Firefox when <SUPER>W would, and <SUPER>W won't launch nautilus when <SUPER>W WOULD launch FireFox.

Changing them back, <SUPER>W launches FireFox successfully again, and <SUPER>F still produces no results at all for launching nautilus.

So now I'm outright boggled.

---

### Post by nickzeff on 2008-10-18
I'm having this problem too!

Anyone know what's causing this?

---

### Post by richardjennings on 2008-10-25
Try typing ```
gconf-editor
``` into a terminal, i.e sans sudo if you had been previously. Works for me.

---

### Post by the real omni on 2008-10-25
That's what I've been doing all along (ie, omitting 'sudo')

I typically only use sudo gconf-editor when it's something specific to the root account.

---

### Post by GeBo on 2008-10-26
I had the same issue and just (one minute ago!) figured out that when I add /home/<id> to nautilus, it suddenly works! (Where id is off course your own login name.)

So just use the command: nautilus /home/<id>

Edit: After trying one and another I found out that  "nautilus ~"  works as well (off course without the quotes).

---

