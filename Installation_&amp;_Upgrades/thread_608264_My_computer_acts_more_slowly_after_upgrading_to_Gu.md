---
title: "My computer acts more slowly after upgrading to Gutsy"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by runesvend on 2007-11-09
Hello fellow Ubuntonians!

After I upgraded my computer's (Athlon 1900+, 2 GB RAM, ASUSTeK GeForce FX 5200) Ubuntu installation from Feisty Fawn to Gutsy Gibbon it acts very slowly in many applications. Especially Amarok is very slow. When an already open instance of Amarok is changed from minimized to maximized it takes about 20 seconds before it accepts user input and is functional. The left hand side where all the artists are shown in Amarok is drawn on my screen very slowly. I can see the "plus signs" to the left of each artist (which, when clicked, allows me to see the tracks by this artist) are drawn one by one at a rate of circa 5 per second. When this is done drawing my playlist is slowly drawn and I can use the program.

This never happened with Feisty.

[B]If I run the *top* command in a terminal I can see that when Amarok is maximized from a minimized position the process using all remaining CPU power is Xgl. As far as I understand this is the now default method for drawing on my screen, I think it was Xserver in Feisty but I'm not sure.

Is there a way I can get back to the old "Feisty-way" of drawing things on my screen? Because I think my graphics card or something else is simply too slow to function quickly enough.[/B]

Your input is appreciated.

Have a nice evening.

---

### Post by runesvend on 2007-11-16
*bump*

Anyone?

---

### Post by IllegalCharacter on 2007-11-16
To turn off Desktop Effects go System->Preferences->Appearance and click the Visual Effects tab. In there you can turn off the Desktop Effects.

I've also noticed that Gutsy is a lot slower than Feisty, it's unfortunate. I might need to buy another GB of RAM so that I can run the new OS (this rings a bell).

---

### Post by runesvend on 2007-11-17
Thanks for your reply. I did what you suggested but under the *Visual Effects* tab it was already set to "none". So that can't be it unfortunately.

I agree that this is, to put it mildly, unfortunate. A lot of people installing Gutsy on a computer like mine will definitely not accept the low response time and switch to Windows or another OS.

It puzzles me why a bug like this haven't been discovered earlier.

---

### Post by runesvend on 2007-11-17
After searching a bit I found out how to disable XGL.

In [this]("http://ubuntuforums.org/showthread.php?t=581634") thread someone said to issue the following commands:

> mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable

So I did that, restarted Ubuntu and now everything is back to its usual fast Feisty speed. It seems like I'm not the only one having this problem. Someone mentioned that Xgl isn't very good if you're not using Deskop Effects, which I weren't.

In my opinion, enabling Xgl by default and forcing new users (some of whom are probably not as patient as I am) for whom it runs slowly to search the internet to find out which commands to issue to disable Xgl seems like a poor solution. Why not disable it by default and let the people with good graphic cards enable it, or, *at least*, make a GUI for disabling Xgl.

---

