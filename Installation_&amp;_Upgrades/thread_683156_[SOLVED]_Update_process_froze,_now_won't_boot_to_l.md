---
title: "[SOLVED] Update process froze, now won't boot to log on screen"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by phatdad on 2008-01-30
Hope someone can help. Relative noob.

I was notified I needed to update fairly soon after a fresh Gutsy install. There were a lot of update downloads so I was doing them in chunks. Then, as some of the downloads were installing, everything froze up. No mouse, keyboard or anything. 

I was browsing at the time and the FireFox window was over the Update Manager, so I don't know which update was installing. Nothing would respond, ctrl alt backsace or anything.

Now when I boot it goes as far as the Ubuntu logo and the progress bar, then a few lines flash on and off a few times. Then the monitor goes to sleep as there is no signal.

I assume I can get into recovery mode but what do I type? How can I check what happened last before the crash? And how do I go about fixing the error?

Hope someone can help. Thanks for looking.

---

### Post by Rocket2DMn on 2008-01-30
At the blank screen, see if you can do CTRL+ALT+F1 and see a terminal.  If so it just means your GUI broke, so log in and run
```
sudo dpkg-reconfigure xserver-xorg
```
You will be asked questions about your hardware, but I'm sure you can figure it out.  Let me know if you can't get there or have problems with running that.

---

### Post by phatdad on 2008-01-30
Thanks. Will try tomorrow as off to bed. I'll post what happens.
Thanks again.

---

### Post by phatdad on 2008-01-31
> **Rocket2DMn said:**
> At the blank screen, see if you can do CTRL+ALT+F1 and see a terminal.  If so it just means your GUI broke, so log in and run
```
sudo dpkg-reconfigure xserver-xorg
```
You will be asked questions about your hardware, but I'm sure you can figure it out.  Let me know if you can't get there or have problems with running that.


Tried the above. I could get to the command line, and I think the *sudo dpkg-reconfigure xserver-xorg* went OK, but still won't boot to the log on screen.

These are the final messages, flashed on the screen 3 times before the monitor goes to sleep 

[B]Starting anac(h)ronistic cron anacron
Deferred execution scheduler atd
Periodic command scheduler crond
Enabling additional executable binary formats binfmt-support
Checking battery state…
Running local boot scripts (/etc/rc.local)[/B]

(I took photos as the messages flashed up which is harder than it sounds so there may be a couple of typo/mistakes)

Any help appreciated.....

---

### Post by Rocket2DMn on 2008-01-31
What happens if you do CTRL+ALT+F1, login, then run
```
sudo apt-get update
sudo apt-get upgrade
```
Then load X
```
startx
```
Also, what kind of video card do you have?  Please include make and model.

---

### Post by phatdad on 2008-01-31
Thanks for your help Rocket2DMn- I'm back in now!! I have a geforce fx5200 which I loaded using envy, which seems to be the cause of it all..

I ran, on advice, 

[B]sudo dpkg-reconfigure -phigh xserver-xorg
sudo startx[/B]

which threw up an error saying x was already running. Anyhow, I rebooted and everything was fine until I tried to set the visual effects. I was prompted to enable the driver and reboot. again the problem happened. 

So at the command line I repeated the above steps, which let me log in again. I then ran Envy to uninstall and then install the Nvidia driver. Another reboot and all is well so far!

What is the -phigh bit? Is it default settings for x? I'm asking because I see his all happening again. I remember problems with Nvidia/Envy and upgrades from when I dabbled with earlier versions of Ubuntu. 

So far Gutsy has totally won me over. The community of help and support through these forums is so refreshing.

Thanks again Rocket2DMn

---

### Post by Rocket2DMn on 2008-01-31
I think --phigh might restore default settings, or at least only ask high priority questions only.  I never used phigh myself so I don't tell people to use it, but it apparently works.
What happened when you ran it? Did it ask any questions, and if so, which ones?  I would much like to know.
Glad you're back in business, enjoy!

---

### Post by phatdad on 2008-01-31
I don't think it asked any questions. I entered *startx* after and that threw up an error (as mentioned before). So I entered *sudo reboot* and then ran Envy etc..

-phigh? sounds like priority high..

ps sorry for the delay in answering.....

---

### Post by Rocket2DMn on 2008-01-31
that's cool, delays are quite common on forums.  So no questions then, huh?  That's kinda cool, I might start suggesting that to people who had their xorg.conf working then broke it.
Thanks

---

### Post by phatdad on 2008-02-01
I tried it again (after finishing the updates the same problem happened again...!)

-phign option throws up a warning that it is overwritting existing settings, and is storing a backup version. There are no prompts or requests- it does it automatically.

It worked fine to get me back to desktop, and then I did un/install with Envy gain to get the desktop effects going again.

Any idea how i can see what the problem was?

---

