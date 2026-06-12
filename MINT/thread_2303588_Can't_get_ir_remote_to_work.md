---
title: "Can't get ir remote to work"
date: 2015-11-20
forum: MINT
---

### Post by jarminator on 2015-11-20
[SIZE=2][FONT=arial]I've got a [Logitech Harmony Companion]("http://support.myharmony.com/en-ca/download?utm_source=www.myharmony.com&utm_medium=homepage&utm_campaign=download&_ga=1.104372160.1153940077.1447825818#control-series") remote and I'm not sure if it will work under Linux. 
A quick background: [/FONT][/SIZE]
[LIST=1]
[*][SIZE=2][FONT=arial]This is my **first ever** install of Linux and I love it! Specifically it is [Linux Mint 17.2 “Rafaela” Cinnamon]("http://blog.linuxmint.com/?p=2863") so I hope it ok to talk about it here. I figure this is more of a generic ubuntu question than a specific Mint question so I hope I don't offend anyone.[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]I've only had it up and running for about a week so far and this has been my only stumble in attempt to create the perfect Linux Kodi htpc. Kodi opens at boot and everything runs quite smooth and fast![/FONT][/SIZE]
[*][SIZE=2][FONT=arial]This is my second ever forum post and I'm obviously a total noob so go easy on me ;)[/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=arial]My hardware is:[/FONT][/SIZE]
[LIST=1]
[*][SIZE=2][FONT=arial]The pesky remote mentioned above[/FONT][/SIZE]
[*][SIZE=2][FONT=arial][COLOR=#545454]A super fast (but sadly too noisy(I'll just have to crank the volume)) [/COLOR][COLOR=#545454][NUC5i7RY]("http://www.intel.com/content/www/us/en/nuc/nuc-kit-nuc5i7ryh.html")[/COLOR]
[/FONT][/SIZE]
[*][SIZE=2][FONT=arial][COLOR=#545454]keyboard, mouse, tv, stereo etc.[/COLOR][/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=arial][COLOR=#545454]&#8203;[/COLOR][COLOR=#545454]I'm can get the tv and stereo setup using the android phone app but have been banging my head against the wall trying to get any kind of input to the NUC. I don't want to resort to windows since I'm really enjoying linux but this stupid remote might be the deal breaker. I've tried various things so far like: [/COLOR][COLOR=#000000]sudo apt-get install lirc [/COLOR]but I get an error when it tries to Setting up setserial (2.17-48) plus from what I have read people are hating lirc and so I tried: [COLOR=#000000]ir-keytable
[/COLOR]which I believe I have installed correctly but I get this error Couldn't find any node at /sys/class/rc/rc*.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
I did this [tutorial]("https://gist.github.com/mcneil-hack/89965125556b219f84fd?signup=true") on concordance and struggled right through to the end only to find that Logitech no longer has a web based setup.
I tried out [this]("http://blog.serindu.com/2014/05/12/ubuntu-14-04-xbmc-13-intel-nuc-i3/") but when it got to the ir-keytable part I got stuck.

I've read a bunch of other stuff but in all honesty I'm too green and can't even figure out how to tell if the NUC IR is even alive.
I ran a command at one point a couple of days ago (can't remember what it was now though ) and it gave me hope - A list of devices including a Logitech Universal something something... 
I really need some kind of step by step as I can't seem to put all the pieces together.
After three days of my joy of Linux keeping me going I'm finally starting to get frustrated. 
Thanks!

[/FONT][/SIZE]

---

### Post by mastablasta on 2015-11-20
i just use the TV's remote for Kodi. is that not an option here?

I also use one of those mini keyboards I bought form China for 12 EUR or so.

---

### Post by jarminator on 2015-11-20
Thanks for the reply! The whole idea is to use this particular remote. It is a universal remote with great range so i could control my stereo from the other room or just plop down in front of the tv for a movie etc. Plus if i'm feeling lazy i may try controling lighs and other things with it eventually. Plus, plus, it is the best feeling, slickest looking remote... Oh, and I've already bought the damn thing &#128521;
I may give your idea a try this weekend just for kicks, though I feel I'd run into all the same issues anyway.
Has anyone got this (or another Harmony remote) working... Or a nuc with built in ir... Or both ideally &#128515;
Thanks!

---

### Post by oldos2er on 2015-11-20
Moved to MINT.

---

