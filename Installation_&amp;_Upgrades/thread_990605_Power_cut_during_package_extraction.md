---
title: "Power cut during package extraction"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by roopakv on 2008-11-22
Hi... i am total newbie to ubuntu, for that matter of fact Linux.
I was recently installing ubuntu server 8.04.1 Hardy Heron on a machine... After installing the basic components i required from the cd i rebooted and was into ubuntu...
Here after setting up the network connections... 
i then wanted to install desktop GUI over the server to make it easy for handling... (saw the guide given on codejacked.com)
the command i gave was

sudo aptitude update
sudo aptitude install ubuntu-server

First it wanted to download 536MB of installation packages.. it took about 2 and a half hours, after which it started extracting the package. For some reason when the power was disrupted my UPS failed and the computer was turned off.

I turned it on again and now the errors i receive during 

sudo aptitude install ubuntu-desktop

dpkg was interupted ,manually run dpkg --configure-a
at least something similar

when i do that it fails and the error is too many errors to be shown...
i tried booting into the gdm it works... but after i enter username and password nothing come up....its stuck there

ive hunted around the net a bit ... and guess my problem is partial extraction of dpkg package...
is it possible to re extract the entire package and re-install..
if it is not possible how do i reset so that i may re-download and install the desktop package... personally i would like to just re-extract as downloading takes forever for me...

Sorry for the loong question
Can someone help this newbie please????

---

### Post by Sef on 2008-11-22
Could you please copy and paste the error messages when from the terminal, you type or paste this command:

> sudo dpkg --configure -a

---

### Post by roopakv on 2008-11-24
i triend this ... but unfortunately cant copy the error as it is on the other system.. dont know how to access the net while on ubuntu server so using net from a another computer...

the basic set of errors it gives are whole list of components it hasn't extracted yet.
then it stops and says !queueln ... too many errors..
if u could just tell me how to re-extract the package if possible..

---

