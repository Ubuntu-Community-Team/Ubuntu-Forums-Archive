---
title: "JS and flash problems after upgrade"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by needhelppls on 2008-03-11
Hello,

I'm pretty new to ubuntu. I have the 64bit version and had Feisty installed (everything worked fine), but upgraded to Gutsy a few days ago. Since then, I have had two problems. The strange thing is that I have already been able to solve them, but a few hours later, not even having the computer shut down, the problems came back.

The first problem that I had was that flash didn't work anymore after the update to Gutsy. Apparently I wasn't the only one who had problems with it. I tried a few possible solutions that were offered on the internet and had the nsplugthingy reinstalled for a few times. None of the solutions worked, until I tried this:
[https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890)

After installing the flashplugin that way, it worked ... at least for a few hours. I didn't change anything but after a while, I just got a white area where movies should be playing, just like before. I think it's probably still installed in the right way but isn't active or something. How can I get it to work again? How do I get this to work every time I boot the computer and not have to change or start something again?

The second problem is that firefox (2.0.0.12) hangs or freezes for a few seconds on EVERY link I open. So I click the middle mouse to open a new tab, and after about one second, the rotating icon on the new tab (which indicates that the tab is loading) stops rotating, I cannot change to another tab, I cannot open a new link, I can't do nothing. The only thing I can do is move with my mouse (and when I hover any links, they don't even change color). Other applications are not affected: I can still switch to those. I only have the problem when javascript is enabled. I had also solved this problem, with this:
[http://www.ubuntu-nl.org/documentatie/multimedia/multimedia_installeren/](http://www.ubuntu-nl.org/documentatie/multimedia/multimedia_installeren/)

I have also done this: 
[http://kb.mozillazine.org/Standard_diagnostic_%28Firefox%29](http://kb.mozillazine.org/Standard_diagnostic_%28Firefox%29)
But that didn't offer the solution.

I think it was installing the Ubuntu restricted extras thing that solved the problem. Nevertheless, a few hours later, I was back at start and firefox was hanging for a few seconds again on every link I opened when javascript was enabled.

I have literally searched for a solution for more than five hours, now I'm tired of it and that's why I'm asking you guys. There are so many 'solutions' on the internet, but a lot of them only work for not 64bit users or other groups I don't belong to.

Please help me a bit,

Many thanks.

---

### Post by needhelppls on 2008-03-11
Both problems have a common cause I think.

After posting the previous post, I again reinstalled the flashplugin by:
```
sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```.

After that Firefox totally crashed and I had to reboot by holding the powerbutton of my computer for a few seconds. When I rebooted, I repeated the action, then Firefox didn't crash, my both problems were away again.

Then starting watching some youtube movies, when after a while, they didn't work anymore. It was also from then on that I had the problem of the freezing Firefox.

---

### Post by needhelppls on 2008-03-12
I just saw that the problem with the freezing firefox for a few seconds also happens when javascript is disabled, though a lot less.

---

