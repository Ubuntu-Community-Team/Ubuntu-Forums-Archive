---
title: "GF2 TI install help for beginner"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by Trier99 on 2013-02-11
Greetings.
I have an Athlon 1800 processor with a GF2 TI nVidia card.
Installation has been completed and I accepted the 230 Mb
of "upgrades".
 
I have no function from the GUI, (no icons, no response to 
the mouse)though I can open up a teminal 
and a toy window (by different key combinations)which seems 
to be a bare-bones effort.(Nautilus)
I can also activate a Mail program which has the same bare look.
I am assuming my ancient graphics card needs some drivers.
Logging out is a problem. I use a couple of CTRL-key combinations 
to get to a tty terminal and shut off the main switch to exit.
 
I don't have enough knowledge to follow some of the posts which 
seem to be going into the area I need.
 
First, is it worth trying to get my graphics card to work?
Second, should I be thinking of another distribution which 
is possibly older and can ope with older stuff?
 
If I had to buy a new graphics card, what would be the cheapest?
 
I of course would welcome some help to complete the installation 
which is my original choice.
 
Trier99

---

### Post by dino99 on 2013-02-11
which ubuntu is used ?
how was made the installation ? (real, wubi, virtualbox)
how are you logged ?  (unity, gnome-shell, ... )

your system either can use:
- nvidia-current
- xserver-xorg-video-nouveau

[http://podzemski.com/2012/10/20/ubuntu-12-10-nvidia-drivers/](http://podzemski.com/2012/10/20/ubuntu-12-10-nvidia-drivers/)

note: for easy change/upgrade/removal, install synaptic

sudo apt-get install synaptic

---

### Post by Trier99 on 2013-02-11
I installed Ubuntu using the official DVD.
I removed the Slideshow after reading some posts,
about my Athlon cip, which enabled the install to complete.
( I was able to use the Terminal for that)
The first install was over an original MSoft Windows.
After my problems with the Athlon chip and Slideshow,
I chose the first option which reinstalled over a previous
install, while keeping as many of the old files as possible.
The computer now autoboots to the purple clouds screen 
which is supposed to be the background of the GUI.
There is nothing showing onscreen and the mouse moves
but nothing happens.
All I can do is try different key combinations.
My keyboard is a MSoft one with a number of keys assigned 
to shortcuts.
"Mail" brings up the mail as described. "Computer" key brings up 
the very simple "desktop" described.
Volume + and - both bring up a coloured dialog.
I think I used CTRL and T for Terminal which is also coloured.
 
"how was made the installation ? (real, wubi, virtualbox)
how are you logged ? (unity, gnome-shell, ... )"
 
I really don't know what the above means.
I suspect I am looking at a broken "unity"
Never having seen a working GUI I can't offer any more.
 
"your system either can use:
- nvidia-current
- xserver-xorg-video-nouveau"
 
Thankyou for your attention, but I don't know how to get from
my Terminal to your options.

How does a terminal user instruct Linux to select one of those 
options?
 
Trier99

---

### Post by Trier99 on 2013-02-15
Just a further comment.
I tried out the uninstall/reinstall method you gave, but 
it failed to alter anything I can see.
By the way, the coloured Terminal I can call by CTRL?ALT/T
calls itself a Gnome terminal.
 
Thanks for your time/help.
 
Trier99 [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by Trier99 on 2013-02-15
I tried installing the Bumblebee package, and as far as I know, 
replacing nvidia drivers with older ones.
Now I have a screen with the proper icons down the left edge.
 
However, things are so slow! The screen actions are about half 
a minute behind the mouse selections!
 
I think I have read somewhere that this has happened to others.
 
Any intervention to guide me to a solution will be most welcome.
 
Trier99:confused:

---

