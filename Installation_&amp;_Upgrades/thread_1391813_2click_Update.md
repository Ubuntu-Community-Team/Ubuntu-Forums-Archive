---
title: "2click Update"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Cerebrux on 2010-01-27
Its been almost 5 months since I released the v5.7 of 2Click Update and never thought that it really needs something new to add. It works like as it should be. It is better than your classic Update Manager. You run it and it deals with the rest of its job (update package list, install upgrades, remove obsolete dependencies, free disk space etc.) without bothering user with confirmation dialogs that he would already answer yes. Over all 2Click Update counts 2700 downloads and just the 1023 times are only from the 5.7 version. Since its first release it has been translated to 20 Languages. (thanks Simos, for the initial internationalization!). So why should I release a new version of something that just works ?

I pretty much assume that you know the saying "if it ain't broke, don't fix it". Well for some odd reason Canonical, decided to remove the "aptitude" package from a default Ubuntu installation. This is where 2Click Update stops working. The code internally, used to have some "aptitude" commands so in a default installation of the latest Ubuntu (version 10.10) won't work.

The easy thing would be just to replace "aptitude" with the default "apt-get". But you may know that if a programmer starts working again on an old code 3 things can happen:

[INDENT]Fix some issues
Totally break it
Add some, late night new features[/INDENT]

In my occasion, I couldn't stop trying to implement some new ideas, features and user interface improvements ! Let me remind some of the key features that 2Click Update has and makes it the all-in-one system updates and maintenance app for inexperienced users.

When you launch 2Click Update it will automatically do the following things for you:

[LIST]Refresh your package list.[/LIST]
[LIST]Install the latest updates for your applications and system libraries.[/LIST]
[LIST]Remove packages that were automatically installed to satisfy dependencies for some packages that are no more needed.[/LIST]
[LIST]Remove packages and configuration files which are not required by any other software upon your system.[/LIST]
[LIST]Remove all stored archives in your cache for packages that are no longer in the repositories or that have a newer version in the repositories.[/LIST]
[LIST]Delete from cache the downloaded packages to free up some space.[/LIST]
[LIST]Optimize RAM memory.[/LIST]

Just watch the following video to see it in action.

[http://www.youtube.com/watch?v=CwwpkBgZvvo&amp;hd=1](http://www.youtube.com/watch?v=CwwpkBgZvvo&amp;hd=1)

**Cool ha ??? Go grab it** :

2Click Update is available in **.deb** package for easy install/uninstall. To download it you can either go to the the download section here: [http://cerebrux.net/2clickupdate/](http://cerebrux.net/2clickupdate/) 

Whats next ???

If you like it ... then spread the word ! Re-tweet it, share it with your friends...

---

