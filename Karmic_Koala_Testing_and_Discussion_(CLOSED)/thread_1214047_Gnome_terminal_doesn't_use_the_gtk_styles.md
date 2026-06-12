---
title: "Gnome terminal doesn't use the gtk styles"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by durand on 2009-07-15
As in the title, gnome-terminal doesn't use the gtk styles (widgets,fonts) that the rest of the desktop uses. Does anyone else have this problem?

---

### Post by wayne_cat on 2009-07-15
no problems here ... can you make a screenshot?

[[IMG]http://ubuntu-pics.de/thumb/18773/bildschirmfoto_iCBP9U.png[/IMG]]("http://ubuntu-pics.de/bild/18773/bildschirmfoto_iCBP9U.png")

---

### Post by taavikko on 2009-07-15
No problem here also, had to add menubar and open a tab in terminal for better view...

---

### Post by durand on 2009-07-15
Attached. I also just noticed that my mouse pointer has reset to the ubuntu default. I'm not sure if thats related.

EDIT: I didn't add my tab bar but its still obvious.

---

### Post by taavikko on 2009-07-15
Does this happen with all the themes?

---

### Post by durand on 2009-07-15
> **taavikko said:**
> Does this happen with all the themes?

Just tried, and yeah :(

---

### Post by durand on 2009-07-15
[http://changelogs.ubuntu.com/changelogs/pool/main/g/gnome-terminal/gnome-terminal_2.26.3.1-0ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/gnome-terminal/gnome-terminal_2.26.3.1-0ubuntu1/changelog)

I can't see any relevant changes :S

---

### Post by taavikko on 2009-07-15
At first hand I would continue by resetting gnome-terminals conf
by renaming .gconf/apps/gnome-terminal
within virtual console gdm shut, so gnome session would in any way try to just overwrite the file.

Is also easy to see if problem persist by creating a new user and starting gnome-terminal in that session, if it really is b0rked.

---

### Post by durand on 2009-07-15
> **taavikko said:**
> At first hand I would continue by resetting gnome-terminals conf
by renaming .gconf/apps/gnome-terminal
within virtual console gdm shut, so gnome session would in any way try to just overwrite the file.

Is also easy to see if problem persist by creating a new user and starting gnome-terminal in that session, if it really is b0rked.

Actually, when I tried switching user, gdm crashed and brought me back to my own account at which point the terminal was magically fixed :o

Thanks everyone for the help! I hope it doesn't come back though.

---

### Post by psyke83 on 2009-07-16
From an open terminal, open a new terminal:
```
$ gnome-terminal
```

It should print any GTK warnings/errors in the first terminal - paste them here.

---

### Post by durand on 2009-07-16
> **psyke83 said:**
> From an open terminal, open a new terminal:
```
$ gnome-terminal
```

It should print any GTK warnings/errors in the first terminal - paste them here.

psyke83, as I said above, it somehow fixed itself however when it was still broken, I did try running gnome-terminal in a terminal but it only gave the usual theme deprication warnings.

---

### Post by durand on 2009-07-17
Argh! Something really strange is going on because this problem is back (along with the mouse cursor being reset)... :(

---

### Post by deathsshadow77 on 2009-07-17
are you sure its an issue with terminal and not the theme? I use dust sand from time to time and I notice that the appearance window is slightly different from other normal windows. Can you take a screenshot with terminal and some other application? I think it may have something to do with appearance preferences not being a normal window.

---

### Post by durand on 2009-07-17
> **deathsshadow77 said:**
> are you sure its an issue with terminal and not the theme? I use dust sand from time to time and I notice that the appearance window is slightly different from other normal windows. Can you take a screenshot with terminal and some other application? I think it may have something to do with appearance preferences not being a normal window.

I am completely sure that its not the theme. I've been using this theme for about a month and I've not had any problems with the terminal (which I use daily) until recently.

EDIT: Screenshot attached.

---

### Post by durand on 2009-07-18
Ok, its gone again. I don't really mind it so much anymore now that I know that it will go at some point but I really want to know whats actually causing it, and why it's only affecting gnome-terminal and my mouse cursor...

---

