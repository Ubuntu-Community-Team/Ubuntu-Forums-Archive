---
title: "Where is my System Menu? 11-10 Gnome3"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by StGeorge on 2011-10-15
I made the mistake of upgrading my Ubuntu 11.04 distro to the latest Ubuntu 11.10 distribution.

 The problem I have is that the upgrade has not kept all of my previous settings.  If I sound furious, it is because I am. Ubuntu should upgrade keeping the preferences of the previous installation.
 I answered "Yes" to keeping old Configs, why has it still messed up my computer?

It took me days to get 11.04 the way I wanted it, after the 11.10 upgrade I had a completely useless Linux Distro. 

 I had the ridiculous Unity desktop where I could not find anything. I did have 11.04 setup with the Gnome desktop but this dreadful Unity has been installed by default with 11.10.

 I need a proper desktop, not this idiotic "I want to be a mobile phone on a desktop" type interface.

I had to re-install Gnome with:
```
sudo apt-get install gnome-panel
```

The problem is that all I am offered with the Gnome Desktop now is Applications and Places as menu items, no System menu.
I dont want a scroll lists of 100's of apps displayed as big icons, I want a hierarchical menu system

Now I would like to know how I can get my System Menu back.

Has anyone any ideas.

I really am sick of spending hours trying to fix Ubuntu after System Upgrades.

Wish I had stuck with 10.04

---

### Post by Grumbel on 2011-10-15
Don't know of any way to get the system menu itself back, but the stuff in the system menu has been moved to the "User menu", which is in the top-right by default. If it's not there, it can be added by Alt-rightlicking the panel, selecting "Add to Panel" and then searching for "user menu".

There is also:

[http://ubuntugenius.wordpress.com/2011/06/25/ubuntu-11-04-fix-add-the-classic-gnome-menu-applicationssystemwine-to-the-unity-panel-system-tray/](http://ubuntugenius.wordpress.com/2011/06/25/ubuntu-11-04-fix-add-the-classic-gnome-menu-applicationssystemwine-to-the-unity-panel-system-tray/)

Which I haven't tried.

---

### Post by MAFoElffen on 2011-10-16
> **Grumbel said:**
> Don't know of any way to get the system menu itself back, but the stuff in the system menu has been moved to the "User menu", which is in the top-right by default. If it's not there, it can be added by Alt-rightlicking the panel, selecting "Add to Panel" and then searching for "user menu".

There is also:

[http://ubuntugenius.wordpress.com/2011/06/25/ubuntu-11-04-fix-add-the-classic-gnome-menu-applicationssystemwine-to-the-unity-panel-system-tray/](http://ubuntugenius.wordpress.com/2011/06/25/ubuntu-11-04-fix-add-the-classic-gnome-menu-applicationssystemwine-to-the-unity-panel-system-tray/)

Which I haven't tried.
Like he tried to describe... Upper Bar > Look right-most item (username) > System settings.  

It is also under Application as "System Tools."

---

### Post by RileyLynx on 2011-10-16
Ubuntu 10.10 has switched to the Gnome3 backend. So expect a LOT of things to be changed or dumbed down. :/

I'm going to give XFCE/Xubuntu a try myself, add in compiz for some extra tweakablity.

---

### Post by StGeorge on 2011-10-16
I appreciate your answers but the 'System Settings' which appears to be mimicking System/Preferences and System/Administration in the old style System Menu in the right User menu is not a complete list of what I had in 11.04.

For example I am missing:
Synaptic Package Manager
Or are we now faced with using only that exceptionally slow and inefficient 'Ubuntu Software Centre'?
I cannot find Main Menu.
Ubuntu has always been difficult enough when it comes to creating menu items. Now I do not even have that option.
I could go on but the 'System Settings' link is just nowhere need complete enough.

It looks like we are now facing learning Ubuntu all over again?

How does anyone get anything done with this Distro?

Still at least I have got 98se and XP which I can use when I need to actually get some work done.

Will have to use the laptops with 10.04 for serious Ubuntu Linux Computing.

Grumbel-Thanks for the Link. I have followed the Guide in the link.
I now have a menu I can use.

Thanks again for taking the time with answers.

---

### Post by nerderello on 2011-10-16
I found Synaptic under "Other" .

When I shot myself in the foot and upgraded to 11.10, and after installing Gnome Classic (which is no longer Gnome 2, unlike in 11.04), I found most of what used to be in the old system menu had ended up under "other" in the Application menu.

I also found that I had to install gnome-tweak-tool to be able to change, install, themes.

And when you add the WiFi performance issues, they need to rename 11.10 - Shoot Yourself in the foot.

Oh, and if you haven't found out already, you need to Alt-Right click to add stuff to the top panel.

---

### Post by StGeorge on 2011-10-16
It has been another Ubuntu nightmare. I don't know about 'shooting myself in the foot' nerderello, I feel like I shot myself in the head and was unfortunate to survive!

What I have done for other unfortunates who have not switched their out of date desktop style of computing to a Tablet or better still binned the desktop to use a Mobile for all computing needs, is to:

(I kept my original install of Gnome Panel), then I:

Installed Classic Menu Indicator.
Terminal: 
```
sudo add-apt-repository ppa:diesch/testing
```
```
sudo apt-get update
```
```
sudo apt-get install classicmenu-indicator
```

Once installed, hit Alt+F2 and enter:```
classicmenu-indicator
```as the command to run.

Your old System menu and Preferences and Administration sub-menus are now in an applet on the right side of the menu bar.

Open Preferences/Main Menu from your new Applet and add:```
classicmenu-indicator
```as a new Menu Item, so that if this Menu does not run on the next boot, you can start the Menu and add 'classicmenu-indicator' to your Startup Applications so it will load on future boot.
It should already be in there, so check to see it is not disabled.

So if you are unfortunate enough to upgrade to 11.10 from 11.04 the above should help with a hierarchical menu.

You will probably spend hours fixing other previous preferences though.

EDIT:
After all that I have just found:
> nerdello:
I found Synaptic under "Other" .Applications/Other that is.

I now have enough hierarchical menus to open a chain of Distros.
Still better 10 Menus than 1 Unity

---

### Post by StGeorge on 2011-11-23
Wiped 11.10 off the face of my Hard Drive and Re-Installed 10.04.

Started looking for an good XFCE or LXDE.

These look interesting:
[http://www.pclinuxos.com/?page_id=188](http://www.pclinuxos.com/?page_id=188)
[http://www.pclinuxos.com/?page_id=213](http://www.pclinuxos.com/?page_id=213)

Would appreciate any ideas.

---

