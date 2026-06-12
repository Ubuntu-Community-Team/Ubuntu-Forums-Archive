---
title: "Browsers don't work after update"
date: 2017-06-01
forum: Installation &amp; Upgrades
---

### Post by igorath on 2017-06-01
The live version worked and the fresh install worked. I then updated and couldn't get the browser to run. Just crash to an error report screen.

Live and fresh install version 16.04

Updated 16.04.3

Gnome flavor

Tried current Chromium and Firefox 54, 53, 45, and 39.
T
I hope this is enough info. If I can't get it working its back to Win XP...


Thanks for any and all help

---

### Post by RobGoss on 2017-06-01
Well it seems to me this machine is really old if you're still running Windows xp, may I suggest providing what your system specs are it will help trouble shoot your problem 

I'm almost certain 16.04 maybe to much for that old machine to handle

---

### Post by igorath on 2017-06-01
Amd athlon xp 2800+
2 gigs pc2700 raM
ECS KM400-M2 mb
Nvida 7600GT 128mb
Wd 80gig x2
LiteOn dvdr

I know its not top of the line but as I mentioned it worked prior to update. And the required specs are met from what I read.

---

### Post by RobGoss on 2017-06-01
Have you tried removing Chromium and reinstalling it again?

You can use the software center or Synaptic package manager

Another alternative is using the terminal 

```
 sudo apt-get purge chromium-browser
```


```
rm ~/.config/chromium/ -rf
```

---

### Post by Impavidus on 2017-06-01
If you run firefox from the terminal, it may give you a useful error message.

---

### Post by ajgreeny on 2017-06-01
Also try closing both browsers then renaming the current configuration folders in your home as backups, ie **~/.mozilla** and **~/.config/chromium** and then try restarting the browsers.

Does that help?

---

### Post by igorath on 2017-06-01
Thanks for the help but no longer needed. Somehow I managed to installed a corrupt copy of Ubuntu onto a hard drive that was
(supposely) disconnected under bios. This drive had all my backups on it. No reason to put anything on it now.

---

### Post by RobGoss on 2017-06-01
>  The live version worked and the fresh install worked. I then updated and couldn't get the browser to run. Just crash to an error report screen.  

From reading this statement everything was working as expected

>  Thanks for the help but no longer needed. Somehow I managed to installed a corrupt copy of Ubuntu onto a hard drive that was  

Is this the same copy of Ubuntu that you said was good?


How do you know the copy of Ubuntu was corrupt?

---

### Post by mörgæs on 2017-06-02
Your hardware does not have SSE2 which the new browsers require. This makes me suspect that your present browser and maybe entire operative system is old and unpatched.

I would recommend that you begin with a fresh install of Lubuntu 16.04 and apply all updates. There is some advice about the browser problem in the thread to which I link below.

---

