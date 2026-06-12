---
title: "Ubuntu Software Center Issues"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by Abrucard on 2010-03-16
Okay, so here's what happened, I installed the game Tremulous through the software center, and was messing around with the graphics settings. I set the resolution to one that is not supported by my monitor apparently. I was unable to exit out of the game without hard reseting my system, since the monitor would not show it. Figuring it was just a config file or something that I had to delete, and reinstall, I went and forcibly removed all files with "tremulous" in the name. Now, I cannot reinstall the game via the software center, the icon is missing from the center, where it once was. I tried clearing the packages, and updating them, but to no avail. I hunted down the .deb that installs the game and tried deleting that, that didn't fix it. If it comes right down to it, I CAN get the game to reinstall via the sh run command with the .run file from the website, but this is a nuisance when the package WAS available through the manager. And yes, I realize this is a bit of a gripe, and I probably won't play the game too much, but I'm a bit OCD about this sort of thing, especially when I caused it. >.< So, basically, to condense this, I want to know, is there a way to restore this particular package to it's original state without doing a reinstall or fresh install of the entire system? (Which I don't plan on doing either way)

---

### Post by tommcd on 2010-03-16
> 
Figuring it was just a config file or something that I had to delete, and reinstall, I went and forcibly removed all files with "tremulous" in the name.

What files did you remove? And how did you remove them?
 Did you remove anything outside of your home directory? Like for example, anything in /usr, /usr/games, or /usr/local/games?
 
To try to troubleshoot this, first try uninstalling and reinstalling tremulous via the terminal. To uninstall:
```
sudo apt-get remove --purge tremulous
```
If you get any errors, post them here.
Then rename any .tremulous directory (or directories if there are more than one) to something like .tremulous.bak
Then reinstall tremulous:
```
sudo apt-get install tremulous
```
Again, if you get any errors, post them here. The output from those commands should (hopefully) point to the problem.

For future reference, you could have just uninstalled tremulous from the software center or the terminal.

---

### Post by Abrucard on 2010-03-16
Again, I forcibly removed the files via "sudo rm", I honestly wasn't paying attention to what I was removing, but the purge seemed to help, I also did an autoremove, so now the game will install via the software center again, the only thing left to do is to restore the icon for it within the software center, though it is unnecessary really, lol. Thank you again. :)

---

