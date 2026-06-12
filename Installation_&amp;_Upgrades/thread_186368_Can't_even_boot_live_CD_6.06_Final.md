---
title: "Can't even boot live CD 6.06 Final"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Syirrus on 2006-06-01
I was excited to try out the final cut of dapper 6.06.  I tried both the 64bit version and the 32bit version and I can't even get X to start.  I have a ATI video card x1900xtx.  I tried doing a sudo dpkg-reconfigure xserver-xorg with no success.  It looks like I will be returning back to windows :(

Syirrus

---

### Post by llamakc on 2006-06-01
You're returning to windows before trying out the vesa driver, getting everything setup and then following the instructions for installing the ati drivers?

Ubuntu Dapper works fine with my ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

---

### Post by Syirrus on 2006-06-01
I will try out the vesa driver again.  Perhaps I didn't do something right.  I'm just a little frustrated that's all.  Sorry for being a big baby :).  I will give it another shot and keep you posted.  

Syirrus

---

### Post by daahli on 2006-06-01
hey,

I had a similar problem with a X700 ATI card. I managed to solve it by running the following from the terminal:

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg

Then select driver fglrx (not ATI).

Then start X with startx.

I can't remember whether I really needed line 2 when I installed Dapper, but I definitely needed it for Breezy.

Hope this helps :)

---

### Post by Straker on 2006-06-01
Not meaning to hijack this thread but I am also trying to boot off of the CD, but I have a different error, it appears to be trying to read "hda", but I get a weird error message like:

> huh? Expected NULL return argument

or some such thing. Yes the error message has the word "huh?" in it.  I am really hesitant to upgrade from Breezy, if I can't even boot a live CD (and yes, other Live CD distros work on my PC).

Thanks

---

### Post by llamakc on 2006-06-01
Do you want to upgrade? If so, follow the upgrade instructions and enjoy Dapper.

---

### Post by Straker on 2006-06-02
[QUOTE=llamakc]Do you want to upgrade? If so, follow the upgrade instructions and enjoy Dapper.[/QUOTE]

Sounds kinda dangerous if the Live CD is giving me errors, dontcha think?

I wanna test drive before I buy the car.

---

### Post by Syirrus on 2006-06-02
OKay, I tried vesa again and it didn't work :(.  I'm not sure what to do now. Any suggestions?

---

### Post by BoneyOne on 2006-06-02
I also have the same issue.

When I let it auto detect it crashes X back down to the command line.
If I try to go in and select the vesa driver, it ends up crashing the PC.

And sadly I can't the above with the sudo apt-get as I'm trying to do it off of the LiveCD.

Oh, and it probably has something to do with my X800XL...had same problem with Badger, although I was able to use the vesa driver for it.

---

### Post by Syirrus on 2006-06-02
I appreciate the ubuntu team and the community.  I just wish there was a little bit more quality control when distros are released. I mean we went for RC to final in just a few days.  Surely a bug like this could have been identified if the RC was given enough time to prove itself worthy of becoming a final cut.

---

