---
title: "Installing wine..."
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by Garf on 2006-08-18
Hi...

Before I start I did a search for wine, no obvious threads came up...

I have tonight installed wine to try and get dreamweaver running... I was following some instructions. The firs few were how to isntall wine.

It said (and I had already done this anyway) to type "apt-get install wine". Very Simple. The next step that it said to do though was to just typw "wine" and the purpose of this was "/*To create the wine file structure*/"

The command "wine" just returned the following:

Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit

Anyway after this didn't work, I went ahead with the rest of the installation of dreamweaver... and it didn't work... I can post that information later if desired. But is there a reason why "wine" won't work... is wine completely setup from doing the "apt-get install wine", if so then I guess I have a bigger problem.

I am pretty sure it's a problem with wine because I got an almost identical error from wine when I tried to install sqlyog...

Anyway, any help would be appreciated.

Regards
Gareth

---

### Post by meng on 2006-08-18
The usage of wine is:
wine [name of].exe

---

### Post by zxee on 2006-08-18
> The command "wine" just returned the following:

Usage: wine PROGRAM [ARGUMENTS...] Run the specified program
wine --help Display this help and exit
wine --version Output version information and exit

that output is telling you that wine requires and argument.
e.g (from terminal) > wine dreamweaver

Apt-get wine already set up your wine for use. Although don't expect miricles from wine-sometimes it just makes you dizzy (I couldn't resist)
Check out the wine website [http://www.winehq.com/for](http://www.winehq.com/for) more info on wine (or see crossover office?) [http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by Garf on 2006-08-18
> **meng said:**
> The usage of wine is:
wine [name of].exe

Yeh, I understand that.. but thats not what the guide found here:

[http://blog.publicidadpixelada.com/2006/07/30/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps/](http://blog.publicidadpixelada.com/2006/07/30/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps/)

Was saying...

The part I am referrng to is:

1. $ apt-get update
2. $ apt-get install wine and then type “yes”
3. $ wine /*To create the wine file structure*/

I know it doesn't make sene to me either...

---

### Post by meng on 2006-08-18
Well if I type "wine" by itself I get the same message that you posted. But if I type "wine [name of app]" then it runs the app.

---

