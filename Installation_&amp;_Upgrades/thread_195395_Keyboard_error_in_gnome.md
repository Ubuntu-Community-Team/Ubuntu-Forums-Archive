---
title: "Keyboard error in gnome"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by waltervalderrama on 2006-06-12
Hi, I just updated my system. Had the xserver problem. Fix it with installing nvidia-glx and then dpkg-reconfigure gdm.

But when i rebooted my system, gnome keyboard was in a strange language. I cannot log on gdm because everything i type, every letter is shown with strange symbols. i am only admitted to type numbers and some symbols as / or $.

I can normally boot in a terminal. Xkb is correctly configured with "la" keyboard. 
What can i do to copy my xkb keyboard configuration to gnome, or to reconfigure gnome kbd without loging in (in text mode).

Please help me

:sad: :sad: :sad: :sad:

---

### Post by pyromithrandir on 2006-06-12
Check the keyboard Input Device section of you /etc/X11/xorg.conf
>         Option          "XkbLayout"     "*whatever is here*"

Make sure that's what you want it to be. I'm a little unclear as to whether that's what you mean to say you did or something else, but that should be that layout that your login screen uses.

---

### Post by waltervalderrama on 2006-06-13
Yes. I guess Xkb is correctly configured. I am a little confused. What configuration is used in the login screen? Gnome or Xkb? I 've already configured everything of Xkb using dpkg-reconfigure xserver ......... How can I changed my gnome keyboard configuration without loggin in?

I found a file in /etc/gconf/.....peripherals/kbd
but i dont undertand it, it's dificult to edit it. Is it the right one?

---

### Post by ayoli on 2006-06-13
if you want to view/edit gconf keys use gconftool-2:

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd #list all kbd dir entries recursively
gconftool-2 -s /path/to/thekey key_val # wil set key_val as value for thekey
hope it helps

edit: actually i have this output:
```
[17:23:54@ayoli.zone]:~ >$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model =
 overrideSettings = true
 options = []
```
so i'm not sure that's the right way to resolve your pb. couldn't it be a locale pb ?

---

### Post by waltervalderrama on 2006-06-13
I am going to try it later. Thanks a lot. By the way what is locale? I 've seen this word many times when installing/updating.
Is the path /desktop/g..............? desktop?, please confirm

---

### Post by ayoli on 2006-06-14
the localesre the language/encoding you use, actually it's  he first thing you are supposed to choose at install, but if it's messed up you can try:
sudo dpkg-reconfigure locales
that might do the job.
cheers

---

