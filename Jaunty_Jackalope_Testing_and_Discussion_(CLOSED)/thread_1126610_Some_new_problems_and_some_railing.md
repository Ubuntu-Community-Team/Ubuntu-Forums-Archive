---
title: "Some new problems? and some railing"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-04-15
I just noticed some new problems - maybe just on my end that's why I'm asking here first if anybody can confirm those:

console autocompletion doesn't work as before
e.g.: apt-get inst"Tab" doesn't work (should give you install)
or modprobe -r ipw"Tab" -> shoudl give ipw2200

The save as/open dialog takes ages to show up.
e.g. in Firefox -> File -> Save Page As "wait wait wait wait" -> dialog

The tracker crashes after some time with "index corrupted" and asks to reindex -> loop 



the ranting and raving part
_____________________________________________________________

I feel like blowing off some steam (calmly I hope).
. := (dot) - I mean it


You cannot disable stuff that I manually enabled.
e.g. Ctrl+Alt+Backspace

You cannot enable sounds again after I disabled them.

Probably ... if I click somewhere ... I want it to happen.
Give me an option to get rid of unneseccary dialogs asking "do you really want to". (if I mess it up - I can take it)
Or are you trying to be Windows now?

**Make it work or don't give me the option.**
If I plug in a second monitor - ahhh - I don't even want to start.
(yeah... now if at least my ctrl+alt+backspace still worked ...)

---

### Post by Bakon Jarser on 2009-04-15
Autocomplete and page saving both working fast and well on my end (fully updated).  But I am sick of it changing certain stuff back to default settings.

---

### Post by Darkshade on 2009-04-18
About the autocomplete:
comment out the following part in your /etc/bash.bashrc file
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```
and restart the terminal. Should work fine now.


No idea about the rest though.

---

