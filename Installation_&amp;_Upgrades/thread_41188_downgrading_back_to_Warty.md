---
title: "downgrading back to Warty"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by Stefan Koopmanschap on 2005-06-12
I've recently upgraded my wife's PC from Warty to Hoary, and since then have been having trouble with too many things. Most important problem for which I can't seem to find a solution: Crossover Office won't start anymore, giving a Wine error.

So, I want to move back to Warty, as everything seemed to work fine under Warty. How should I approach this? Is there even a way to do this, to mass-downgrade all packages? Or should I do a clean Warty install?

---

### Post by Xian on 2005-06-12
If it were my box I'd backup or split off the /home directory to save the user prefs and then do a clean install.

---

### Post by Gtaylor on 2005-06-12
I had some problems with upgrading also, it is probably best to just back your things up and install Hoary with a clean install. It runs much better than Warty once installed, the upgrade can be a little rough, especially now since more time has progressed since the first upgrades were rolled out.

---

### Post by Stefan Koopmanschap on 2005-06-12
[QUOTE=Gtaylor]I had some problems with upgrading also, it is probably best to just back your things up and install Hoary with a clean install. It runs much better than Warty once installed, the upgrade can be a little rough, especially now since more time has progressed since the first upgrades were rolled out.[/QUOTE]

but do you have crossover office? that is one piece of software my wife can't live without, since she needs her photoshop.

---

### Post by nocturn on 2005-06-13
[QUOTE=Stefan Koopmanschap]but do you have crossover office? that is one piece of software my wife can't live without, since she needs her photoshop.[/QUOTE]

Is Crossover the only app that is failing?  If so, it may be better to try to fix it then to downgrade (because you will loose out a lot of stuff).

What version of crossover do you have?
What you can try is:

1# uninstall crossover and reinstall it
2# install a newer version if possible
3# try crossover under a different user (maybe config files got messed up).

I know a friend of mine is running it on Hoary, it seems to work.  I don't know if it was installed before or after upgrading from Warty...

---

### Post by kvidell on 2005-06-13
[QUOTE=Stefan Koopmanschap]but do you have crossover office? that is one piece of software my wife can't live without, since she needs her photoshop.[/QUOTE]
 My fiance has CrossOver Office Pro running on his Hoary box no questions asked.
It's nice, too.
- Kevin

---

### Post by Stefan Koopmanschap on 2005-06-13
[QUOTE=nocturn]Is Crossover the only app that is failing?  If so, it may be better to try to fix it then to downgrade (because you will loose out a lot of stuff).

What version of crossover do you have?
What you can try is:

1# uninstall crossover and reinstall it
2# install a newer version if possible
3# try crossover under a different user (maybe config files got messed up).

I know a friend of mine is running it on Hoary, it seems to work.  I don't know if it was installed before or after upgrading from Warty...[/QUOTE]
 nocturn: nope, there's more apps that are having trouble, but cxoffice is the most important one to my wife.

kvidell: that is a very comforting thought. I think I'll try to install a fresh Hoary then.

---

### Post by Stefan Koopmanschap on 2005-06-18
for future reference, I did a fresh install and now crossover office works fine out of the box. I can run everything again. thanks a lot!

---

