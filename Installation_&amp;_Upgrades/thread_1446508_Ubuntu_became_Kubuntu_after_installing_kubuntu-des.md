---
title: "Ubuntu became Kubuntu after installing kubuntu-desktop"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Paulzy on 2010-04-04
Ubuntu became Kubuntu after installing kubuntu-desktop. I just wanted to install the KDE 4 Desktop manager. OK I used 
> 
sudo apt-get install kubuntu-desktop


And it said it was going to download over 400MB of data, so I answered Yes. When it got to the DM config screen i still set gdm as default. Later after the installation was done, I typed
> 
sudo dpkg-reconfigure gdm


I set kdm as default. Rebooted. I saw the blue kubuntu boot screen, then I was REALLY expecting to see a COMPLETELY different desktop, but ...no. Just my old one, complete with the GNOME panels, except the UserSwitcher didn't work. Everything else was the same (or so it appeared), except I had all these KDE apps in my menus.

So I did
> 
sudo dpkg --configure kdm


That didn;t work as I recall so I retyped
> 
sudo dpkg-reconfigure gdm


And rebooted.

Well, I still see the blue kubuntu boot screen screen. How can I get it back to ubuntu's default boot screen?

Thanks.

BTW: When I DO switch DMs, how can I be sure it actually worked??

---

### Post by ajgreeny on 2010-04-04
You can change from gdm to kdm with the command you show, and then choosing which one you want, but to actually change from gnome to kde, you must wait for the login screen and then go to the options menu, from where you will get the choice.

If you want to get back to ubuntu's splash screen, the reconfigure gdm, with the choice of gdm there should do it, but I know from experience it does not always seem to work, so you could always just uninstall the kubuntu-artwork-usplash if you wish.  That may also take kubuntu-desktop, but don't worry about that as it is only a meta-package and does not really do anything, except make sure all thekubuntu packages are installed if you do a distro version upgrade.

PS
kdm and gdm are not the desktops themselves but just the display managers, used at login, rather than any other time, as far as a user will notice. It is at the login screen only that you will know which is being used.

---

### Post by Paulzy on 2010-04-04
Thanks, that helps a lot. Hm, I just wanted to be able to use KDE4. But here the thing. When I do select KDE from the Sessions menu during login, but I didn';t notice any diffrence, aside from the UserSwitcher not being added to the GNOME panel. hmm?

thanks again

---

### Post by ajgreeny on 2010-04-05
It sounds from that as if you are not actually geting the KDE desktop environment when you choose it from the session menu.  You would certainly notice the difference between gnome and KDE, they don't look similar, or certainly not so similar as to be mistaken for one another.

I think something must have gone wrong in the installation in some way.

---

### Post by Paulzy on 2010-04-17
> **ajgreeny said:**
> It sounds from that as if you are not actually geting the KDE desktop environment when you choose it from the session menu.  You would certainly notice the difference between gnome and KDE, they don't look similar, or certainly not so similar as to be mistaken for one another.

I think something must have gone wrong in the installation in some way.

Somethign did indeed. For now when i upgraded from 8.04 LTS to 8.10 things went wrong. For one I cannot select certain menus without being forced off and being dropped back to the login screen :(

---

