---
title: "Reinstall without reformat"
date: 2014-10-10
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2014-10-10
The reinstall reported that I may need to re-install some packages manually because not all the packages could be installed as part of the reinstall. Is there a list somewhere of the packages that were not reinstalled?

I have just opened the terminal. There is now where to enter a command line. It is black with sidebars but no place to enter a command. The directory location is not showing. How do I bring it back so that I can run some  bash commands?

R

---

### Post by deadflowr on 2014-10-11
gnome terminal?
If black, is it possible that the background and the text are both black?
Ifr yes to gnome terminal, can you open Edit >> Profile Preferences >> Colors, and fiddle with the color scheme?
Does that do anything.

And for what it's worth, when you reinstall without formatting, only the packages that are on the installation medium(usb/cd/dvd) will be installed.
The good news about it though, is that your home directory should still be intact.

---

### Post by ecophobia on 2014-10-11
Use Xterm to run

dconf reset -f /org/compiz/

Then restart Unity:

setsid unity

---

### Post by Robbyx on 2014-10-11
I decided to do a reinstall and then found the same thing again. I have changed the colour scheme and that solved the disappeared text, but gave me a load of other problems that are mentioned in other querries. Thanks for helping.

---

### Post by ecophobia on 2014-10-11
With Linux, I has always been like that. The OS can do much more then other operating systems, but you would have to spend much more time on it to make it work. I remember my experience with RedHat Linux BEFORE it became commercial and Fedora or Ubuntu did not exist. Today, Linux has many things polished up, and added many features. The later tend to case many problems, making Linux experience consistent though out these years :KS

---

### Post by deadflowr on 2014-10-12
> **ecophobia said:**
> Use Xterm to run

dconf reset -f /org/compiz/

Then restart Unity:

setsid unity

Since this is tagged as UbuntuGnome, I would doubt that would be of any help.
Unless that's a misused tag...

To the OP, perhaps point us to some other queries that show/state similar problems.
Or at least post whatever those other problems are.
(I only knew of the black on black terminal...)

---

### Post by Robbyx on 2014-10-13
I cleared up the other points by reinstalling Ubuntu, this time by reformatting the system partition. However there is a daily problem of the order of my two monitors. Each time I start the computer the previous settings are lost and so the mouse has to go to the right to get to the left monitor. When I change the monitor order that corrects it only for that session.

---

