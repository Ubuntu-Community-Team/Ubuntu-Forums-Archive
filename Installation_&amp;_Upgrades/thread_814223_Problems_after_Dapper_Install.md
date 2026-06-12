---
title: "Problems after Dapper Install"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by theravenproject on 2008-05-31
I could not get Hardy to install on my new CPU becuase of the graphics card-I followed the advice I got from one (Suspectly Inept) person here at the Forums-the only person who would answer my posts for about four days but I am not complaining...So...I went with my old Dapper Live Cd (The last version of lINUX i EVER USED AMD WAS EVER FAMILIAR WITH-bARELY) AND I have no sound...I have a Gig Mobo The new X48t line with DDR3 Mem and A Q9300 Quad core...it has High def audio onboard from Realtek...Not working!  Any time I run or try to run a program in terminal I get this and this Is what I am posting about right now...can someone explain what this means in terms of my system?

(evolution-2.6:6287): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
Setting up initial mail tree
addressbook_migrate (0.0.0)
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

Ignore the Evolution part becuase it does this when I run any prog I believe!  Any and all help is greatly appreciated!

---

### Post by theravenproject on 2008-05-31
Help

---

### Post by kyphi on 2008-05-31
I used Dapper for two years and always had glorious sound with a Soundblaster Live 5.1 audio card.

Onboard sound and video are incorporated to keep costs down (they are cheaper than adding cards).

First of all, you can type ```
asoundconf list
```in a terminal and that will tell you what sound device you have installed.

The simplest option is to buy a Creative Soundblaster Live 5.1 card and install it.  If you do that, you will have to disable the onboard sound in the BIOS so as not to cause confusion between the BIOS and the operating system.

---

### Post by zvacet on 2008-06-01
> I could not get Hardy to install on my new CPU becuase of the graphics card

Did you tried to install Hardy with alternate CD?

---

