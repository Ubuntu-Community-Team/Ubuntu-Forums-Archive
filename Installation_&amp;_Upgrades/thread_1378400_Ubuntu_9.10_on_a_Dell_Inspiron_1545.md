---
title: "Ubuntu 9.10 on a Dell Inspiron 1545"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by CeilingCrash on 2010-01-11
Tried to install the 9.10 distro on a new (to me) Dell 1545 this weekend, very disappointing experience.  Wireless broken, video broken.  Hope this stuff gets fixed in the next LTR.  Until then, let me share what I did to make it work : 

Start with a CD of the 8.04 Long Term Release 

([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)).   It's a good idea to plug an ethernet cable directly into your laptop rather than using wireless, if possible.   This should be much faster and more reliable (since your wireless may flake out.)

Now go into Update Manager and select Upgrade to 9.10.   
If you get an error which complains that the flash-nonfree package is in a badly broken state, do this : 
  
   sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
   sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
   sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree

Then restart the upgrade to 9.10.

To get flash going, use Symantic to install adobe-flash .

Finally, set up your multimedia (to play DVD's, etc) by following these instructions : 

[http://shibuvarkala.blogspot.com/2009/10/how-to-make-ubnutu-910-karmic-koala.html](http://shibuvarkala.blogspot.com/2009/10/how-to-make-ubnutu-910-karmic-koala.html)

Reboot.   Video and DVD playback should work now.

That's it !   I must say, once I got everything working, 9.10 has 
great stuff like automatic dual-monitor support (plug and play!).

Hope this post helps somebody out there ...

---

