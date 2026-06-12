---
title: "How do I cancel an installation"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by futureman on 2006-11-25
I'm running kubuntu edgy, I was installing flashplugin-nonfree through adept it got stuck on downloading, I have a cable connection and know flash doesn't take more than an hour to download. So I quite adept by force, know I can't use it, I've sudo dpkg --configure -a in the console, but all that does is starts the download again. In adept it says the flashplugin is installed, but it hasn't even downloaded yet, how do I cancel this and what flash plug-ins installation works?

---

### Post by tredegar on 2006-11-26
As I recall, you have to say "Yes" to a flash licence agreement during the install. You are not seeing this prompt, so you cannot answer it, so adept gets "stuck".
If you try again with Adept, when it gets stuck, look for a button called "Show details" or similar. Click it, you'll see the prompt and be able to answer it.

------------

Or, install from the command line:

sudo apt-get install name-of-package

------------

Or, use "easyubuntu" to install it for you:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

(Watch out for the licence agreement prompt!)

HTH

---

### Post by peggyjo on 2006-12-24
I'm having a similar problem with a Flash download being stuck.

It's nice to know "why" it's stuck -- i.e., waiting for a response on the license agreement.

But I'm stuck with it in Terminal, and there is no "show details" function.

Is there a Terminal command I can use to get unstuck?

Thanks much.

(P.S. Absolute newbie here.)

---

### Post by peggyjo on 2006-12-24
OK, I seem to be fixed now. 

Following a clue in another thread ( [http://www.ubuntuforums.org/showthread.php?t=307383&page=3&highlight=cancel+download]("http://www.ubuntuforums.org/showthread.php?t=307383&page=3&highlight=cancel+download") ), I was able to mark Flash for removal in Synaptic. That seemed to get me "unstuck" and I'm no longer getting the error message when I open Synaptic.

---

