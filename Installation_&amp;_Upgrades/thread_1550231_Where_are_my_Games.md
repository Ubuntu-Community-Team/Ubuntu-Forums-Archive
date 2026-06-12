---
title: "Where are my Games?"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by scater on 2010-08-10
When I download a game from the Ubuntu Software manager, it doesn't show up in the applications. Is there another place where the files are located? And how can I execute them? I am trying to run Mednafen

---

### Post by lyall on 2010-08-10
have you install the Menu Editor?
if not install it from Synaptic Package Manager

then under Applications > Other > Menu Editor

in the Menu Editor under Games look for the game you are looking for and place check in the box in front of it, it will be in your Games listing

good luck and have fun learning

---

### Post by oldos2er on 2010-08-10
Mednafen is a CLI program, so open a terminal (Applications, Accessories, Terminal), and enter **mednafen**

---

### Post by scater on 2010-08-11
> **oldos2er said:**
> Mednafen is a CLI program, so open a terminal (Applications, Accessories, Terminal), and enter **mednafen**

I did that. Then it gave me this

```
menkin@menkin-desktop:~$ mednafen
Starting Mednafen 0.8.C
 Loading settings from "/home/menkin/.mednafen/mednafen.cfg"...
 Compiled against SDL 1.2.14, running with SDL 1.2.14

No command-line arguments specified.

Usage: mednafen [OPTION]... [FILE]
    Please refer to the documentation for option parameters and usage.
```

---

### Post by scater on 2010-08-11
> **lyall said:**
> have you install the Menu Editor?
if not install it from Synaptic Package Manager

then under Applications > Other > Menu Editor

in the Menu Editor under Games look for the game you are looking for and place check in the box in front of it, it will be in your Games listing

good luck and have fun learning

I did what you said. I came in contact with the program not opening. It is in the games menu on applications. But when I click to open it, it doesn't load...

---

### Post by linux18 on 2010-08-11
[B]mednafen --help
[/B]

---

### Post by sydbat on 2010-08-11
> **scater said:**
> I did what you said. I came in contact with the program not opening. It is in the games menu on applications. But when I click to open it, it doesn't load...Try doing a reinstall via Synaptic. There might be some dependencies that did not get installed from the Software Centre.

---

