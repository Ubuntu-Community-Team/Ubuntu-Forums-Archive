---
title: "CTRL +c on Lubuntu 22"
date: 2023-04-01
forum: Installation &amp; Upgrades
---

### Post by wiredcharlie on 2023-04-01
I've just installed Lubuntu 22. In the past CTRL +c in terminal would terminate the current process. Now it does not. 

Please could someone explain?

Tony

---

### Post by sudodus on 2023-04-01
Please give an example of a program/process that is not terminated by ctrl+c in the terminal window where it was launched.

---

### Post by guiverc on 2023-04-02
Please also be specific with release details. 

Lubuntu 22.04 LTS and Lubuntu 22.10 use different versions of packages thus are not the same (*though backports is available for 22.04 LTS that brings them closer*). Ubuntu has reserved the *year* format (ie. 22) for *snap* only products, however Lubuntu being a desktop system (*with the desktop packaged only in deb format*) does not support 22, only 22.04 & 22.10.

Otherwise I agree with @sudodus; being able to get ^C to work when I expect it to in *jammy* (22.04) & *kinetic* (22.10).

---

### Post by wiredcharlie on 2023-04-02
lubuntu-22.04.2-desktop-amd64
**[SIZE=4][COLOR=#000000]Lubuntu 22.04.2 LTS (Jammy Jellyfish)[/COLOR][/SIZE]**

sudo nano [file]

shift-ctrl-x to exit results in failure to return to command prompt

terminal is QTerminal 0.17.0

---

### Post by guiverc on 2023-04-02
Nano uses ^C as an editor function (*Location*)... thus ^C inside of nano is **not** dealt with via `qterminal`.

---

### Post by tea for one on 2023-04-02
Ctrl x closes the nano text editor and returns to command prompt.

---

### Post by MAFoElffen on 2023-04-02
On mine in 'nano', (and only in nano) just on my laptop, it respects the right <Cntrl> but ignores the left <Cntrl>... Strange.

---

### Post by ActionParsnip on 2023-04-03
isn't it CTRL + SHIFT + C to copy?

---

