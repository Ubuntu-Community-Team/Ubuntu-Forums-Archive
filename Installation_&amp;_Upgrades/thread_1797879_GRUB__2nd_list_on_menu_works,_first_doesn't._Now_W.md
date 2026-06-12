---
title: "GRUB : 2nd list on menu works, first doesn't. Now What?"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by rreyes3713 on 2011-07-05
I was messing with my setting of my video card (Nvidia GeForce FX 5200 video card) so I can use dual monitors.

Anyway, I messed up the setting and now I don't get a display on the monitor after I select the first list on the GRUB menu. But the second list on the menu does works. 

I suppose I could troubleshoot my settings or just select the second list on the menu.

Here's my question, what happens when the Administrator Manager comes up asking if I want to "Update"? 


[LIST]
[*]Does it update the first menu on the GRUB list and keep the same settings which I won't get a display?
[*]Should I erase the first list on the GRUB menu and maybe the update will be o-kay?
[*]Any suggestions would help me out in the dilemma I'm in.
[/LIST]
Sorry if I getting the jargon wrong. I'm new at Ubuntu Linux vocabulary.

---

### Post by oldfred on 2011-07-05
Print this as this has the settings that grub will do on an update. Only a grub or kernel update will write a new entry.

gksudo gedit /etc/default/grub

If you want to see full boot info:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

