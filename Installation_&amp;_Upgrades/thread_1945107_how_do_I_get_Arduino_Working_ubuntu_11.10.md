---
title: "how do I get Arduino Working ubuntu 11.10"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by ve3tru on 2012-03-22
If I open the IDE these are no saved sketches, and the serial ports are grayed out.
If I open it as super user the saved sketches and serial ports are there.
But it cant find the port no mater what I do
Tried everything I could online with out any luck wasted a week so far, I hate to go back to windows that worked, right from get go, but I need this to work. I spend more time fixing things looking for some obscure patch fix that may or may not work, then actually using this computer, it gives linux a bad name.

---

### Post by Bucky Ball on 2012-03-22
What software do you use in Windows to communicate with your Arduino device? I haven't used mine in awhile but when I did, the software I was using in Windows was open-source anyway and in the Ubuntu repos so I just installed and all as it was, problem free. I can't remember what I was using, though.

UPDATE: Pretty sure it was [Pure Data]("http://puredata.info/Pure"). You might also be interested in [Pure Dyne]("http://puredyne.org/Pure").

PS: Are you sure there's nothing amiss on the Aruduino setup? Are you just attempting a 'hello world' or something more elaborate?

---

### Post by ve3tru on 2012-03-22
Not sure what your trying to say, Arduino is open soure, but wont work under linux.
I suspect that the problem lies with the programers them-self as they seem  to be more windows type guys. I'm working on a project that's been on going for 3 years, so linux is useless to me if this program won't work properly; and its not hello world lol.

---

### Post by Bucky Ball on 2012-03-22
Ok, and what I'm asking is what software are u using to communicate (program) the Arduino device? Pure Data?

You haven't really addressed much of what I asked in my post and if Linux is useless to you then perhaps stop digging for a fix and go back to Windows ... as I mentioned, had no issues myself but my Arduino is one of the first and was doing basic stuff.

Good luck with the project, BTW ...

---

### Post by ve3tru on 2012-03-24
Well I have an arduino uno using the arduino alfa version, the one I got off package manager.
I have Ubuntu 11.10 and Arduino has never worked as far back as 9.04 Ubuntu. Im glad this progam worked for you, but I can show you lots of web pages with people like myself that it has never worked for, or is not working right. With even more pages of fixes and patches.
This laptop is my backup as my windows one is in the shop and your right I plan on going back to windows as this and other programs I need will not work. I was hoping for something constructive like try  *lsusb *or check for a missing package so I can use it.

---

### Post by rag2 on 2012-04-06
I've also been having problems with the Ubuntu provided Arduino package, trying to talk to an Arduino Uno. There are different sets of serial devices depending on what Arduino hardware one is talking to.

There is a further set of problems depending on a **patched communications library** (which may, of course, be the source of my own issues). A colleague reports that even with Windows, there are issues with 64 bit drivers.

Did you ever get any further?

Cheers,

R.

---

### Post by rag2 on 2012-04-06
A further report. The problems one was having with the **arduino** package in Ubuntu 11.10 have totally gone away on a machine running **Ubuntu 12.04&#946;**. The **avrdude** package is updated from 5.10 to 5.11.1, and **arduino** from version 22 to version 1.0 (which **is** later).

Between the two updates, sanity, at least for an **Arduino Uno**, is manifest.

YMMV

R.

---

