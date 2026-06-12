---
title: "LUCID 2 beta: which NBR image should I use?"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eltonw on 2010-04-10
I have previously installed Karmic from the NBR image file. Now I see on the mirrors that there are **two** image files for netbooks (mine is the ASUS EEE 1000 PC):

> Netbook live image
The live image allows you to try Ubuntu Netbook Edition without changing your computer at all, and at your option to install it permanently later. This live image is optimized for netbooks with screens up to 10". You will need at least 256MB of RAM to install from this image.
There are two images available, each for a different type of computer:
Marvell Dove netbook live image
For Dove boards.
Freescale i.MX51 netbook live image
For i.MX51 boards.

#-oHOWTO determine [COLOR="DarkOrange"]which [COLOR="DarkRed"]*live image*[/COLOR] would be suitable for the **[FONT="Trebuchet MS"]Asus[/FONT]**[/COLOR]?

Hunting around, wikipedia, the global Asus site, I can only come up with *this*:
[http://www.asus.com/product.aspx?P_ID=YxnYGjoMzEzmz0Hn]("http://www.asus.com/product.aspx?P_ID=YxnYGjoMzEzmz0Hn")
... which gives me no details of the actual inside hardware:confused:

I am downloading the live CD at the moment

TIA

---

### Post by descendent87 on 2010-04-10
[http://releases.ubuntu.com/releases/10.04/](http://releases.ubuntu.com/releases/10.04/)
You want the ubuntu-10.04-beta2-netbook-i386.iso

---

### Post by eltonw on 2010-04-10
> **descendent87 said:**
> [http://releases.ubuntu.com/releases/10.04/](http://releases.ubuntu.com/releases/10.04/)
You want the ubuntu-10.04-beta2-netbook-i386.iso

I have got the iso image.](*,) As I mentioned, I was in the process of downloading that particular file.

[FONT="Comic Sans MS"][COLOR="Sienna"]HOWEVER, I would like to be able to boot/ install from a USB / SD memory stick.[/COLOR][/FONT]

[COLOR="Red"][CENTER]I have previously installed ubuntu using image files (Karmic, previous releases).[/CENTER][/COLOR] 

My QUESTION, therefore: which of these image files can I use? [B***]OR***[/B] [SIZE="2"]does this mean that the final release will **not** allow me to boot / install LUCID gamma from a USB stick or SD card[/SIZE] (as I have been doing with Karmic)?:confused:

---

### Post by cariboo on 2010-04-10
The Marvell Dove boards use an arm processor, if your netbook uses an arm processor, you will have to determine what version you have. If you don't have an arm cpu, use the i386 image.

If you click the [specifications]("http://http://www.asus.com/product.aspx?P_ID=YxnYGjoMzEzmz0Hn") tab, you will see that your netbook uses an atom n270 cpu. So the Marvell Dove version won't work for you.

---

