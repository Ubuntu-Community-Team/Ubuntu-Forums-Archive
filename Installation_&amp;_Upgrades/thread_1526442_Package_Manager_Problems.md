---
title: "Package Manager Problems"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by akumasaint on 2010-07-08
HI anyone who reads this. I've gad ubuntu for about 2 months and I have a bit of a problem. It's nothing really big but I would like to know how to fix it before major problems start.

As the title says, I'm having trouble with the Package Manager. It's not allowing me to update Ubuntu and I can't even access Ubuntu Tweak now. I get the error

E:Type 'sudo' is not known on line 61 in source list /etc/apt/sources.list, E:The list of sources could not be read.

Any help would be nice, thank you!

---

### Post by Gregorybekkers on 2010-07-08
hi,

You can open that sourcefile and see what is there on line 61.
Is it a ubuntu source that is listed there?

Otherwise just delete that one.

KR,

Greg

---

### Post by akumasaint on 2010-07-08
> **Gregorybekkers said:**
> hi,

You can open that sourcefile and see what is there on line 61.
Is it a ubuntu source that is listed there?

Otherwise just delete that one.

KR,

Greg

Quick Question, how do I open the sourcefile?

---

### Post by Gregorybekkers on 2010-07-08
sudo gedit /etc/apt/sources.list

> **akumasaint said:**
> Quick Question, how do I open the sourcefile?

---

### Post by fballem on 2010-07-08
> **Gregorybekkers said:**
> sudo gedit /etc/apt/sources.list

actually, I have read on other postings that you should use gksudo when you are using gedit.

Open a terminal (Applications > Accessories > Terminal). This will open a terminal.

When the terminal is open, type: gksudo gedit /etc/apt/sources.list then press the enter key. You will be asked for your password. Once you have provided it, then the editor will open.

On the editor (similar to the screenshot I have attached), scroll down to line 61. Rather than deleting the line, you should put two hash marks ## as the first characters. This will change the line to a comment.

Save the file and close the editor and the terminal.

Try the update again. If this doesn't work, then reboot your system and try again. Hopefully, this will work.

---

### Post by akumasaint on 2010-07-08
> **Gregorybekkers said:**
> sudo gedit /etc/apt/sources.list

Okay, that seem to work, thank you:p

---

