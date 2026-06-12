---
title: "netpbm problem no pnmtopnm"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by losttest on 2012-03-06
Hi. I'm having a problem with part of the **netpbm** program called **pnmtopnm**. I'm getting error:

No command 'pnmtopnm' found, did you mean:
 Command 'pnmtopng' from package 'netpbm' (main)
 Command 'pngtopnm' from package 'netpbm' (main)
 Command 'pnmtopgm' from package 'ivtools-bin' (universe)
pnmtopnm: command not found

I'm using Ubuntu 11.04 - the Natty Narwhal and installed netpbm package with Synaptic package manager without any error messages. The program itself is the first on the list [http://netpbm.sourceforge.net/doc/directory.html](http://netpbm.sourceforge.net/doc/directory.html) so it should exist. And according to manual program **pamtopnm** is the same thing as **pnmtopnm**, unfortunately including the error :(

No command 'pamtopnm' found, did you mean:
 Command 'palmtopnm' from package 'netpbm' (main)
pamtopnm: command not found

other stuff like jpgtopnm works.

Due to lack information in google about No command 'pnmtopnm' found, having pnmtopnm on the list and fact that pnmtopnm is included in win32 netpbm package i assume that problem is with installation.

Reinstalled - still not found
Tried to make the netpbm-10.35.84 version downloaded from sourceforge.net says "fatal error: jpeglib.h: No such file or directory"

Actually I need to convert .jpg to text .pgm, so if there is another way please tell.

---

### Post by losttest on 2012-03-06
So to be sure: can anybody install netpbm using package manager and try to convert any image?

jpegtopnm foo.jpg | ppmtopgm | pnmtopnm -plain > foo.pgm

---

### Post by tigger63 on 2012-03-07
I just installed netpbm and everything seems to be working BUT when I run the command pngtopbm it runs and returns to the prompt with no errors problem is I can't locate the output file???

Looking at your issue it seems like its installed  but I don't think pnmtopnm is a valid option..

I'm new to this aswell and ubuntu too..
I used 
sudo apt-get install netpbm

to install it..

Anyone help us out here....please

---

### Post by losttest on 2012-03-08
> **tigger63 said:**
> I just installed netpbm and everything seems to be working BUT when I run the command pngtopbm it runs and returns to the prompt with no errors problem is I can't locate the output file???
Looking at your issue it seems like its installed  but I don't think pnmtopnm is a valid option..
I'm new to this aswell and ubuntu too..
I used 
sudo apt-get install netpbm
to install it..
Anyone help us out here....please

are you sure it's **pngtopbm**? couldnt find it here [http://netpbm.sourceforge.net/doc/directory.html](http://netpbm.sourceforge.net/doc/directory.html)
try *pngtopnm example.png > example.pbm* intstead

still can't solve pnmtopnm problem :(

---

### Post by losttest on 2012-03-09
solved. use **pnmtoplainpnm** instead
jpegtopnm 1.jpg | ppmtopgm | pnmtoplainpnm > 1.pgm

---

