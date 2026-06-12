---
title: "problem installing a program"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Peterfc on 2008-04-28
Hi All

[COLOR="Blue"]Sorry but i am a having trouble installing Realplayer.

I went to the link below for help. At the Ubuntux.org it said open in terminal did tha[/COLOR]t.

[http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player](http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player)

Open a terminal window and type in:
sudo apt-get install realplayer
killall gnome-panel

[COLOR="Blue"]Copied that in the terminal [/COLOR]

The second command refreshes the GNOME panel.

After that you can find RealPlayer 10 in the Gnome menu under Applications -> Sound & Video.

[COLOR="Blue"]I then got the message below.[/COLOR]

tried it and I get this reply "Package realplayer is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source E: Package realplayer has no installation candidate ?

I listen to a radio through Real player. Tried Rhythmbox but the radio is a local station and i can't find a tuner . Using Gutsy Iplayer on the BBc.co.uk/liverpool site played now after upgrading nothing plays. 

Any easy solution for us newbies to install programs without a degree in computer studies???

---

### Post by russ18uk on 2008-04-28
Realplayer isn't free so you won't get it from the (Ubuntu official) repos, so you need to specify where to obtain it from in the sources.list, or download the file direct from Real.com: [http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin](http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin)
Make sure you make the file executable - cd into the directory with Realplayer, chmod a+x RealPlayer11GOLD.bin, or right click > properties > Check Executable. "./RealPlayer11GOLD.bin" to run it in a terminal.

---

### Post by PmDematagoda on 2008-04-28
Can you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by Peterfc on 2008-04-28
Sorry but where do i find.

[COLOR="Blue"]cat /etc/apt/sources.list[/COLOR]

sorry but very new to all this only just escaped from the W*****S jail.

---

### Post by PmDematagoda on 2008-04-28
Just enter the command into a terminal, you can bring up a terminal by going to Applications>Accessories>Terminal.

---

