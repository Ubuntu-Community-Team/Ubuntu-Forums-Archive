---
title: "[SOLVED] reinstall wine"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by Darkade on 2007-11-17
Hello, I had wine a couple weeks ago and I uninstalled it. Now I want to install it again, now here is the thing: I go to Synaptic and select wine, it installs it and everything seems fine, but The Wine Menu no longer appears in my menubar. :(:( I know it's silly 'cause Wine is installed (I can run my Wine applications from terminal, run winecfg and everything) but it's annoying to create the menu myself and create a menu for everything I install on wine. Also having the menu makes it easier to manage the applications.
I've tried to uninstall it several times with the same results

this is the terminal lines I've been using

sudo apt-get --purge remove wine
sudo apt-get autoremove
sudo apt-get clean

Also, I've deleted .Wine folder in my home folder

Finally I though It could be that menu wasn't creating fine so I checked /etc/xdg/menus/applications.menu file and no wine menu appears.

Anyone have any ideas why on reinstall the wine menu does not appear?
Thanks and peace:):)


Hey I got it solved and decided to post how because lots of people seem to have the same problem.

0)You should have wine installed even though you can't see the menu
1) open your ~/.config/menus/applications.menu file
2) do a search for "wine" 
3) you'll notice that every entry that has to do with wine has a </deleted> tag, erase that tag
4) now save the file
You should now have wine menu back in your menu bar, I also changed the location of the applications-merged (It had wine related entries in it) folder but I'm not sure that has anything to do.

I got the Idea from here [http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/4de2f6c56102be46/c99a81771b0fb164?lnk=gst&q=wine+menu#c99a81771b0fb164](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/4de2f6c56102be46/c99a81771b0fb164?lnk=gst&q=wine+menu#c99a81771b0fb164)
thanks to the wine community and I hope this works for all of you

---

