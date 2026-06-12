---
title: "Update causes blank screen/can't log in"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by aleddilwynfisher on 2016-04-26
Hi,

I got a message asking to update Ubuntu and started the update. 

Things were going fine but suddenly I got a blank screen and, after a long wait and the laptop going quiet besides the fan, I had to switch it off.

I switched it back on and just get the console, which I have little/no experience of. I tried sudo apt-get update as suggested elsewhere but it doesn't seem to work (just says it couldn't download most things). Also tried other suggestions elsewhere, like sudo init 3 and sudo init 5. Just says 'PolicyKit daemon disconnected from the bus. We are no longer a registered authentication agent.'

What can I do? I am very new to Ubuntu and the laptop came with it preinstalled. Very worried about losing work on there.

Thanks,
Aled

---

### Post by pickarooney on 2016-04-26
does typing **startx** when you have logged in to the console do anything?

---

### Post by aleddilwynfisher on 2016-04-26
Just tried that - seemed like things were happening as the console disappeared for a bit, but now I'm back there. Lots of code... Last thing it says is "waiting for X server to shut dow. (II) Server terminated successfully (O). Closing log file"

---

### Post by aleddilwynfisher on 2016-04-26
I should've said - when I turn it on, I get the Dell logo as normal, then the Ubuntu logo as normal, but before the usual log-in screen, it goes into text with my computer name and 'tty1', and asks for my login and password. After typing them in, I can do commands.

---

### Post by Bashing-om on 2016-04-26
aleddilwynfisher; Hello;

As you can log in via the terminal, the situation is salvageable .

We need to know what release and what (D)esktop (E)nvironment you are running. ( unity, gnome kde, xfce ??)
Then we can examine what is not taking place in the GUI .

[INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by aleddilwynfisher on 2016-04-27
Thanks for helping!

Not sure what any of that means to be honest (I bought a new laptop with Ubuntu Linux 14.04 pre-installed) but, after a quick Googling, it looks most like Unity. 

Is there any way I can find out for sure? And, if it is Unity, what should I do?

---

### Post by Bashing-om on 2016-04-27
aleddilwynfisher; Hey ...

The situation could arise from a number of different causes.
We begin the process of discovery:
To know what the DE is ( I bet as pre-installed ubuntu it is in fact 'unity'):
Post back the outputs - Between code tags - of terminal commands:
```

lsb_release -a
uname -a
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP

```
These tell us what release you are running, the booting kernel info, and the Desktop employed in this install.

Next we want to insure that the package manager is in a consistent state:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```

And as a 1st approximation of where the problem may lie we will want to know what is taking place in the X layer :
```

cat /var/log/Xorg.0.log

```

All this ->
[INDENT][INDENT][INDENT]just clearing the deck for action
[/INDENT][/INDENT][/INDENT]

---

