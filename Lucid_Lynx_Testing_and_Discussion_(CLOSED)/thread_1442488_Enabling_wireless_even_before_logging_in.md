---
title: "Enabling wireless even before logging in?"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tsk1979 on 2010-03-30
Hi,
I am running kubuntu 10 beta. Its going on fine, and I am able to connect to wireless network and all.
the problem is that I connect to wireless only after I login.
Is there a way to enable wireless even without starting kde desktop.
I find entering password every time I login to Plasma desktop for kwallet annoying.
Only after I enter password. the network manager for kde connects to wireless.

Sometimes, I just do alt+ctrl+F1 to login to terminal and then from there I do ssh to my server etc.,
I do not want this wireless dependency on KDE desktop.

I know there is a way with wicd, but then I have to uninstall knetworkmanager or something?
Is there any native way where I can edit a conf file, put my wpa-psk key there, and simply have wireless enabled on bootup.
Then I can login to KDE, and not bother about entering passwords, as wireless is already enabled!

---

### Post by gradinaruvasile on 2010-03-30
I dont know how exactly knetworkmanager works, but in the gnome version you have an option to make a connection available to all users. But i dont know if it works before actually logging in the gui.

The simplest solution is wicd. I use it and it works better than network manager. Network-manager will be removed automatically in Ubuntu IIRC (now i use Debian and the 2 can be installed side by side here).

One precaution - before installing wicd reinstall the network manager - this way you will have the .debs cached locally in case something goes wrong and you want to reinstall it.
This is done in a terminal:

sudo apt-get install --reinstall network-manager

---

### Post by tsk1979 on 2010-03-30
Okay, I will get wicd, and wicd-curses(command line stuff).
Then I will see how it goes!
Thanks!

---

