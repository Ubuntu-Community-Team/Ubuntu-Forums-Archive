---
title: "Kaffeine Mozilla Plugin"
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by 93viking on 2005-03-21
I'm _very_ new to Linux so please forgive me. I installed Kaffeine by typing this into the Terminal and it installed just fine...

[INDENT]sudo apt-get install kaffeine[/INDENT]

I also tried this to install the plugin for FIrfox and its not working. I typed...

[INDENT]sudo apt-get install kaffeine-mozilla[/INDENT]

and get this...

[INDENT]Reading Package Lists... Done[/INDENT]
[INDENT]Building Dependency Tree... Done[/INDENT]
[INDENT]E: Couldn't find package kaffeine-mozilla[/INDENT]

Any help would be great. Also I see on some desktops that people have a system monitor for CPU temp etc. Can anyone help me with how to set this up. My dumb Prescott is too hot. Should have went AMD 64.

Thanks

---

### Post by bored2k on 2005-03-21
[QUOTE=93viking]I'm _very_ new to Linux so please forgive me. I installed Kaffeine by typing this into the Terminal and it installed just fine...

[INDENT]sudo apt-get install kaffeine[/INDENT]

I also tried this to install the plugin for FIrfox and its not working. I typed...

[INDENT]sudo apt-get install kaffeine-mozilla[/INDENT]

and get this...

[INDENT]Reading Package Lists... Done[/INDENT]
[INDENT]Building Dependency Tree... Done[/INDENT]
[INDENT]E: Couldn't find package kaffeine-mozilla[/INDENT]

Any help would be great. Also I see on some desktops that people have a system monitor for CPU temp etc. Can anyone help me with how to set this up. My dumb Prescott is too hot. Should have went AMD 64.

Thanks[/QUOTE]
 Welcome to the forums

You need to have universe repositories enabled: go to synaptic, settings, repositories, make it show hidden ones, and select universe.

[http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=kaffeine&searchon=names&subword=1&version=hoary&release=all](http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=kaffeine&searchon=names&subword=1&version=hoary&release=all)

For the monitor things you can get gdesklets, wich is very pleasing to the eye while functional [get gdesklets and gdesklets-data].

---

### Post by 93viking on 2005-03-21
Thanks for the post. That did the trick!

Do you know of what i can use to show CPU Temps on the desktop?

---

### Post by bored2k on 2005-03-21
[QUOTE=93viking]Thanks for the post. That did the trick!

Do you know of what i can use to show CPU Temps on the desktop?[/QUOTE]
 gdesklets has something to do this somewhere, but search for gkrellm.

---

### Post by 93viking on 2005-03-22
I have never installed anything on Linux before so please don't trash me... ;) 

I downloaded two files to view my system temps.

"lm_sensors-2.9.0.tar.gz"  and  "lmsensors-gdesklet-0.8.tar.bz2"

How do you go about installing such files in Ubuntu and what directory do you put them in? (I've been a windows guy since 95/NT)

Thanks again for all your help!

---

### Post by bored2k on 2005-03-22
[QUOTE=93viking]I have never installed anything on Linux before so please don't trash me... ;) 

I downloaded two files to view my system temps.

"lm_sensors-2.9.0.tar.gz"  and  "lmsensors-gdesklet-0.8.tar.bz2"

How do you go about installing such files in Ubuntu and what directory do you put them in? (I've been a windows guy since 95/NT)

Thanks again for all your help![/QUOTE]
 Not recommended for you to compile at this moment .

If you installed gdesklets-data you should have all those .

---

### Post by mario8723 on 2005-03-22
I'll 2nd that notion. DON'T install lm-sensors if you are a noob. I know I am, and even followed the How To: Install lm-sensors post somewhere in these hallowed halls. Guess what? It ruined my system and I had to re-install Hoary. Ugh. That'll teach me, lol. :oops:

---

### Post by Jofaba on 2007-03-25
I've got the plugin installed but now when I click on media, it opens Kaffeine but nothing plays. I'm running x86 Kubuntu 7.10 with Nvidia and Beryl.

EDIT: It's quicktime movies from apple.com/trailers that I'm trying to play.

---

