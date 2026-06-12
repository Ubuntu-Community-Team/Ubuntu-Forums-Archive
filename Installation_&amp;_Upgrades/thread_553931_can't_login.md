---
title: "can't login"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by dkrussian on 2007-09-18
This is partially addressed in another thread, but I have the same trouble as this guy
[http://ubuntuforums.org/showthread.php?t=533680&highlight=language](http://ubuntuforums.org/showthread.php?t=533680&highlight=language)
After installing with wubi,  my login screen types in arabic, and only arabic, no matter what flavor of english I try to chose with change language.

SO, being a good netizen I tried to follow those instructions to solve my problem before starting another thread. Absolutely no go. When typeing in 
edit /var/lib/locales/supported.d/local
as per [http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html](http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html) instructions, I get an error that says something about not having a rule for application/* and no access to the thingy (despite the command line clearly stating root@mycompy)

I wish I could copy paste the errors, but can't really do that accross OS's now can I? If it is absolutely necessary, then I'll go handwrite em and type em in, but I'm hoping someone here has an idea how to fix this without.

---

### Post by dkrussian on 2007-09-19
the exact text of the errors is as follows
Warning: unknown mime-type for /var/lib/locales/supported.d/local
Error: no edit mailcap rules for type application/*

---

### Post by dkrussian on 2007-09-20
Since no one seems to be tossing me a bone here I am continuing to scrounge the forums for anything useful. I note that a couple of other users have the problem of unkown mime-type and are being told to use gedit, that's all fine and good except for the little problem that you can't launch gedit from command line only, says can't open a window. 
The only place I can get a coherent input is by launching ubuntu (original kernel) and hitting ctrl+alt+f2. Everywhere else is either arabic only or complete jibberish in the command line (wierd arrow symbols and whatnot...from god knows what number of the unicode)
I am completely new to ubuntu (and linux for that matter) and could really use some help with this.

---

