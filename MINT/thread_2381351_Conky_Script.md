---
title: "Conky Script"
date: 2017-12-30
forum: MINT
---

### Post by mesilikas on 2017-12-30
Dear friends, thank you very much for a good year to have. 
These days I decided to upgrade my good Ubuntu 14.04 Mate and go to Linux Mint 18.3 'Sylvia' MATE but I have not managed to restore Conky as I had made it the reason is the font I use I can not understand what has changed in this distribution...
I had backup all the hidden conky files on home.
You share my file "conkyrc" file, please I can get your help.
Thank you

[ATTACH=CONFIG]277959[/ATTACH]

---

### Post by howefield on 2017-12-30
Post moved to it's own thread and the "*MINT*" forum.

---

### Post by deadflowr on 2017-12-30
The screenshot looks like it's the mint 18.whatever.
So from that, what I see wrong is the bargraph_small.lua script needs adjusting.

Can be relatively simple as all you should need to do is reset the x,y coordinates for each entry
Quick example of what I'm meaning:
```
{	--[ Graph for CPU2 ]--
			name="cpu",
			arg="cpu1",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.95},
			bg_colour={0xFFFFFF,0.01},
			fg_colour={0x0000ff,1.99},
			mid_colour={{1.0,0x10FF00,0.55}},
			**x=35,y=495,**
			blocks=95,
			space=1,
			height=1,width=10,
			angle=90,
			smooth=true
			},
```
You would adjust the setting I've marked in bold in the lua script.
Most should use the same x coordinate (that's the left/right), and so you'll mostly need to adjust the y setting (that's the up/down).

(You'll need to do it to all your bar graph entries)

The adjustments will take as soon as you save the lua script, no need to reload conky.
So you might try making an edit to one bar, then save it and then see where it ends up on the conky .
Hope that helps.

---

### Post by mesilikas on 2017-12-30
@deadflowr Thank you for support

Fortunately, the solution:
It seems as though the 1.10 version of Conky is broken for now and some people are going back to the 1.9 version.
[https://askubuntu.com/questions/798999/conky-does-not-work-properly-on-ubuntu-16-04-gnome/805941]("https://askubuntu.com/questions/798999/conky-does-not-work-properly-on-ubuntu-16-04-gnome/805941")

Thanks for all.

---

