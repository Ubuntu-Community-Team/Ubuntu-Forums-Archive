---
title: "Gnome - No borders"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by Onimae on 2007-03-25
I'm having a bit of problem. I just did a clean install of the Feisty beta. By that, I mean I deleted the paritition containing my Edgy install. I have a seperate one for my /home folder. After the update everything worked great with one incredibly vital exception. Window borders were *gone*. They just disappeared off the face of the earth, it seems.

At first, I thought it would be a problem with some old config files or some such, so I went through the usual process of deleting those from my home folder.

No luck.

I even got rid of .recently-used.xbel, to no avail.

So, my question is, what could have caused this strange behavior to start occuring, and how can I fix it?

It's probably worth noting that I had Beryl installed before installing Feisty. That might have changed something so as to make Metacity not start by default, but that would be awful destructive, don't you think?

Any help would be greatly appreciated.

**Onimae**

---

### Post by bulldog on 2007-03-25
No problem.
I think Beryl will be executed by your session menu,System-->Preferences-->sessions.
Look for it and remove all the beryl and emerald items from the start-up tab.
Log out and in again and it should be metacity again.

You can reinstall Beryl/Emerald after that,take a look here,
[http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367)

---

### Post by Onimae on 2007-03-25
Well, I managed to sort out that problem, but along the way I noticed a much larger one. After booting the computer the splash screen stays there for a very long time, seemingly hanging on the "nautilus" icon. It takes about 5 minutes, at which point it will go away, and load all the stuff in my session thing. Why would that happen?

---

### Post by aksdb on 2007-03-27
> **Onimae said:**
> Well, I managed to sort out that problem, but along the way I noticed a much larger one. After booting the computer the splash screen stays there for a very long time, seemingly hanging on the "nautilus" icon. It takes about 5 minutes, at which point it will go away, and load all the stuff in my session thing. Why would that happen?

I currently encounter the same problem (after upgrading from Edgy). So if someone finds a solution or has an idea, I would be curious to know about it :)

---

### Post by aksdb on 2007-03-27
I finally fixed both problems. I found out, that $WINDOW_MANAGER contained ~/.gnome-compiz-manager/openbox which was non existant and I never even used one of both. That was the reason why gnome-wm didn't launch metacity (or any other window manager) and that was also the reason why the splashscreen hung. I then found, that the wrong export entry was in the .gnomerc file (at the bottom after several empty lines ... that took a while for me to realize that ;)) so I simply deleted that file and now Feisty loads everything just fine :)

---

### Post by warjowuch on 2007-03-28
what do you mean with $WINDOW_MANAGER ??

I have these problems, I can't even alt-tab to other applications, so I am doomed to single task now, because I have NO window borders and they don't even appear in my gnome-panel...

Someone help?

---

### Post by aksdb on 2007-03-28
As I said: simply delete "~/.gnomerc" or correct its content.

---

### Post by warjowuch on 2007-03-28
Your path suggests this file should be in my users homedir. But I cannot find it there... I don't have a .gnomerc-file there.
Thanks though!

---

### Post by aksdb on 2007-03-28
In that case you could still create this file and put this line in it:
export $WINDOW_MANAGER=/usr/bin/metacity

If that still doesn't work, open up a console and enter "gnome-wm --replace" and look what happens. Maybe that points you in the right direction where to look for the error.

---

### Post by warjowuch on 2007-03-28
The last thing helped!
THank you so much :-) This makes my desktop usable :-)

---

### Post by MacUntu on 2007-04-13
Helped me a lot, thanks!

---

### Post by papercuts on 2007-04-20
What if we don't use metacity?

I use xfwm4 (I installed it) and for me the line reads:

[HTML]export WINDOW_MANAGER=/usr/bin/xfwm4[/HTML]

if I change that I won't have xfwm4...

---

### Post by jaumedejuan on 2007-04-20
It worked for me as well :D

My config was:
- official upgrade from edgy to feisty
- compiz being used
- ati open driver being used

that was pretty good, thanks mate!

---

### Post by danskmacabre on 2007-04-20
Hmm, I can't find that file and when I start terminal, it is just a white screen...
Help please :)

---

### Post by mrojas73 on 2007-05-04
Thank you so much, it fixed my problem.  Below is the code for the noobs ;).

sudo rm ~/.gnomerc

---

### Post by moeFinley on 2007-05-27
cool, worked for me too.  Although originally I would just load Beryl Manager and select metacity.  But that was becoming a bit of a pain :)

---

### Post by RegularSlinky on 2008-01-12
Newer versions (7.10) of Ubuntu/Gnome don't seem to have ~/.gnomerc. So deleting it is not an option.

I've just turned off the Appearance -> Visual Effects. This seems to restore the borders. I wish I knew why. The problem started when I turned the Visual effects onto full and then back to medium. When they went back to medium the borders disappeared, and terminal windows are just blank.

Well at least I have a temporary solution: turn off Visual Effects :(

---

