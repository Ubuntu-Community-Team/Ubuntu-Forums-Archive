---
title: "Installing Kismet"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by Fitzwilliam_Darcy on 2011-07-19
Hi guys, I'm new to Ubuntu and Linux and would like help on a problem with installing kismet.

I'm following the instructions on [wirelessdefence.org]("http://wirelessdefence.org/Contents/Installingkismet.htm") to install it.

(I'm using Oracle VM Virtualbox with Windows 7 as host and Ubuntu 11.04 as guest)

When I type in **./configure** into the terminal it works fine, but when I type in **make** it comes with an error saying:

ls: cannot access ./doc/*.xml: No such file or directory.

Does anyone know what this means or how I can fix it?

---

### Post by drpjkurian on 2011-07-19
go to Applications-->Ubuntu software centre and search for'Kismet' in search bar and install it

---

### Post by Fitzwilliam_Darcy on 2011-07-19
> **drpjkurian said:**
> go to Applications-->Ubuntu software centre and search for'Kismet' in search bar and install it

It comes up with **0 matching items** so I had to manually doenload the .tar file and install it using the terminal.

---

### Post by Fitzwilliam_Darcy on 2011-07-19
Does anyone know what type of file it is or if it's a directory or not? I do not get the file extensions in Linux that much.

---

### Post by haqking on 2011-07-19
> **Fitzwilliam_Darcy said:**
> Does anyone know what type of file it is or if it's a directory or not? I do not get the file extensions in Linux that much.


a .tar file is a compressed file which has its contents zipped up.

you need to extract the files.

piece of advice though, if you dont know what a .tar is or how to deal with or how to search to find out then Kismet might be a bit overwhelming for you ;-)

what exactly are you wanting to do with Kismet ?

and it is in the repos so you can conolse apt-get to it or go to synaptic package manager or the software centre, depends what you are comfortable with or what version you are using and/or want of kismet

---

### Post by Fitzwilliam_Darcy on 2011-07-19
Kismet version: gpsd-2.96bis

I meant what type of file is a **./doc/*.xml** that's been giving me the error.

I can extract the .tar file perfectly fine and **./configure** it but the **make** doesn't work.

> it is in the repos so you can conolse apt-get to it or go to synaptic package manager or the software centre

How do I do it using the console and apt-get?
When I type it into the synaptic package manager search bar it says 0 matches found.

---

### Post by haqking on 2011-07-19
> **Fitzwilliam_Darcy said:**
> Kismet version: gpsd-2.96bis

I meant what type of file is a **./doc/*.xml** that's been giving me the error.

I can extract the .tar file perfectly fine and **./configure** it but the **make** doesn't work.



How do I do it using the console and apt-get?
When I type it into the synaptic package manager search bar it says 0 matches found.

ok gotcha.

what version of ubuntu you using then ?

i have checked in 10.04 and 10.10 and it is in their, i typed kismet in synaptic and in software centre

from console type sudo apt-get install kismet

---

### Post by Fitzwilliam_Darcy on 2011-07-19
Ubuntu Version 11.04.

I go into the synaptic package manager --> Settings --> Repositories --> Download from: Main server
Then I close it and click on **Reload** is says
"Could not download all repository indexes"

And another dialog box appears saying:
"E: could not get lock /var/lib/apt/lists/lock - open (11:resource temporarily unavailable)
E: unable to lock the list directory"

When I type kismet into the quick filter, no results show up.



Using the console method with **apt-get**, I get this:
"E: Unable to locate package kismet"



And I still don't know what **./doc/*.xml** is. Is it a specific file that I'm missing?

---

### Post by drpjkurian on 2011-07-20
Hi
Please do the following,
System-->Administration-->Synaptic package manager-->Settings-->Ubuntu software centre and check everything. See the screenshot 1
Also select 'other Software' and check the following. See Screenshot 2

After this steps install Kismet from Software centre..

---

### Post by Fitzwilliam_Darcy on 2011-07-20
Aah thank-you. I have it installed now, but how do I start it? Or maybe a better question is where is it?

The only new program installed is wireshark, but where's kismet?
Applications -> Internet -> Wireshark
I think wireshark was installed because it's a good tool to use while using kismet, but I can only find wireshark.

I can't find kismet anywhere...

---

### Post by haqking on 2011-07-20
> **Fitzwilliam_Darcy said:**
> Aah thank-you. I have it installed now, but how do I start it? Or maybe a better question is where is it?

The only new program installed is wireshark, but where's kismet?
Applications -> Internet -> Wireshark
I think wireshark was installed because it's a good tool to use while using kismet, but I can only find wireshark.

I can't find kismet anywhere...

type kismet from console

---

### Post by &#1048;&#1075;&#1086;&#1088; on 2011-07-20
Wireshark+Kismet?!:confused:
That not sounds good to me:(....
What will say your neighbourhood?:popcorn:
Do not be a evil man...

---

