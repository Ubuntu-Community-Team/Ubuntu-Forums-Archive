---
title: "New install - no desktop?"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by agrotto on 2005-10-19
Newbie. I've installed Ubuntu 5.10 a few times now and every time I do I never get a graphical interface (Gnome) and get dumped to the text-system for login and can't get X to run. 

It's an older Gateway machine, but has plenty of RAM and HD space. I was never asked any questions during the install regarding video problems or resolution.

HELP!

---

### Post by pksings on 2005-10-19
If you can login on the text interface you can diagnose this.

sudo bash and then run "startx". That should show your error. Once you know what that is, repost the real error if you don't know how so fix it. Then we can help solve your underlying problem.

---

### Post by agrotto on 2005-10-19
I did "sudo bash"
then "startx"

and got "bash: startx: command not found"

---

### Post by pksings on 2005-10-19
Hmm, sounds like your install didn't finish.

sudo apt-get -f upgrade  

should finish it.

---

### Post by pksings on 2005-10-19
You also might want to read the Upgrade notes.

[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

---

### Post by invalid on 2005-10-19
or if that does not work

sudo apt-get install xserver-xorg

Could it be that you installed the server version of Ubuntu by mistake?

Cheers,
Cb

---

### Post by agrotto on 2005-10-19
I wish.

Got:

"0 upgraded, 0 newly installed, 0 to remove, 0 not upgraded"

---

### Post by muffinresearch on 2005-10-19
I had similar probs. try sudo dpkg --configure -a and if that doesn't throw up anything try installing the package ubuntu-desktop. This fixed my install after it bombed out after the CD was ejected and the install rebooted. I consistently got to between 4-22% before the install errored.

---

### Post by agrotto on 2005-10-19
[QUOTE=invalid]or if that does not work

sudo apt-get install xserver-xorg

Could it be that you installed the server version of Ubuntu by mistake?

Cheers,
Cb[/QUOTE]

Of course this is the answer. I had mis-labeled my CD's and used the Server one by mistake. Thanks for the help and sorry for the wild-goose chase.

---

