---
title: "Problem in installing gnuplot in Ubuntu"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by uabhi12 on 2012-02-12
[SIZE=3][FONT=Times New Roman]I am having problems in installing the package gnuplot in Ubuntu 11.10. The methods described in the websites are not working or maybe I am making some mistake.Help required.
[/FONT][/SIZE]

---

### Post by 2F4U on 2012-02-12
A bit more information on what exactly your problem is (error message etc.) would probably get you better responses.

---

### Post by Topsiho on 2012-02-12
Did you try installing gnuplot from the repositories (using synaptic or on the command line)? That is the most easy way, without having to visit websites other yhan to get some information on what sort of application gnuplot is.

Topsiho

---

### Post by uabhi12 on 2012-02-12
[SIZE=3][FONT=Times New Roman]Did you mean Ubuntu software centre by repositeries?I cannot find the package gnuplot over there. Please help.[/FONT][/SIZE]

---

### Post by Topsiho on 2012-02-13
Yes, it is in the software centre, but a bit disguised. It is called "a command-line driven interactive plotting program".

I never use this software centre, too difficult for me, and also too slow. I use synaptic, which you can also find in the software centre, or much more easy you install this with the command (in a terminal):

sudo apt-get install synaptic

and enter your password when requested to do so.

In synaptic you search for gnuplot, and install what you want. There are several gnuplot files, such as gnuplot, gnuplot-doc, and so on. If you know the names you could also install them in the same way as I described for synaptic, which is the easiest way of course.

OT: it's considered rude to use a large font in a forum. A bit like shouting into one's ears :)

Success,

Topsiho

---

### Post by uabhi12 on 2012-02-13
[FONT=Times New Roman][SIZE=2]Halo Topsiho,

I  have installed synaptic in your prescribed way. In fact it was already installed due to some previous work. But the only place I am finding "synaptic package manager" is "Dash". Is it the same as synaptic? But I am finding no files under synaptic let alone gnuplot. Please make some more help.
[/SIZE][/FONT]

---

### Post by Topsiho on 2012-02-14
> **uabhi12 said:**
> [FONT=Times New Roman][SIZE=2]Halo Topsiho,

I  have installed synaptic in your prescribed way. In fact it was already installed due to some previous work. But the only place I am finding "synaptic package manager" is "Dash". Is it the same as synaptic? But I am finding no files under synaptic let alone gnuplot. Please make some more help.
[/SIZE][/FONT]

Synaptic is installed during the install of Ubuntu. So I am not amazed it was already there.
I have started Ubuntu 11.10 on my experimental computer, started synaptic in the dash (it's the correct one, synaptic is synaptic), ==>searched<== (by name) for gnuplot, and there they are: 6 files whose names start with gnuplot, and some more with gnuplot embedded in them. Of which some are installed already (by default, as I did not install them myself: gnuplot, gnuplot-nox, gnuplot-x11). There is also a gnuplot-doc, which is not installed, but contains the documentation, if you want it you can install it in my "prescribed way".

OT: you are still shouting :(

Topsiho

---

### Post by haresear on 2012-02-14
> **uabhi12 said:**
> Halo Topsiho,

I  have installed synaptic in your prescribed way. In fact it was already installed due to some previous work. But the only place I am finding "synaptic package manager" is "Dash". Is it the same as synaptic? But I am finding no files under synaptic let alone gnuplot. Please make some more help.

If you are not seeing any packages listed in synaptic, try clicking the "reload" button (or in the "edit" menu select "reload package information").

---

