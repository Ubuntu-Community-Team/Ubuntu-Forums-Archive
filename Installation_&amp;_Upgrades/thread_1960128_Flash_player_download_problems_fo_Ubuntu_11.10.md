---
title: "Flash player download problems fo Ubuntu 11.10"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by Marilyn1 on 2012-04-16
I have Upgraded to Ubuntu 11.10 and I now have no Flash player. How do I Install one that is Compatible for this program? Help

---

### Post by jadtech on 2012-04-16
ok  after upgrading make sure you go to the update manager click the check button and do all the updates once that is done and u have rebooted see if flash is working ..

the thing is once you do the upgrade of ubuntu you need to update all your software  :)
if flash still isnt working ,go to the software center search for flash for mozilla ..

---

### Post by CFury on 2012-04-23
I'm also having problems in 11.10.  I've tried Flash-aid, checked updates via Update Manager, as well as had Firefox check for updated versions of plugins.  No dice.  Any other suggestions?

Thanks.

---

### Post by ronaldbrijo on 2012-04-23
I used to have the same problem... Yesterday it got solved by accident...

I wanted to try a different browser and downloaded Opera. Installed quickly and low and behold no flash problem!!

I also tried flash aid on firefox and all the other "FIXES" to no avail, but Opera has no issues!!

---

### Post by CFury on 2012-04-23
I haven't used Opera in years, how do you like it?

---

### Post by CFury on 2012-04-23
Just tried out Opera and unfortunately the Flash issue remains... However WOW, that's a fast browser!

---

### Post by lovinglinux on 2012-04-23
> **CFury said:**
> Just tried out Opera and unfortunately the Flash issue remains... However WOW, that's a fast browser!

Yes, Opera is really fast. Flash performance is good too. Better than Firefox on my system, although Firefox uses less CPU.

---

### Post by techsupport on 2012-04-23
> **Marilyn1 said:**
> I have Upgraded to Ubuntu 11.10 and I now have no Flash player. How do I Install one that is Compatible for this program? Help

If you install Chrome from the PPA it comes with it's very own flash plugin independently. 

It is down the list:

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by chimuzu on 2012-04-24
I'm not sure what the problem is with your machine. Its rare that one fails to install that plugin on Firefox. I did it several times with several machines.
You could try to download it manually and install the .deb file. It worked for me in the past. If that fails you may have to delete the hidden mozilla profile (under Home folder) for Firefox and try to install it on a frsh profile.

I cant be 100% sure of this procedure but I hope it helps

---

### Post by CFury on 2012-04-24
> **chimuzu said:**
> I'm not sure what the problem is with your machine. Its rare that one fails to install that plugin on Firefox. I did it several times with several machines.
You could try to download it manually and install the .deb file. It worked for me in the past. If that fails you may have to delete the hidden mozilla profile (under Home folder) for Firefox and try to install it on a frsh profile.

I cant be 100% sure of this procedure but I hope it helps


I also tried manually, no dice.  Both Firefox & Opera behave the same when handling Flash, Chrome is working however this is obviously due to it's independent plugin.  Well I"ll keep hacking at it, I'm sure it will end up being something simple I've overlooked.

---

### Post by lovinglinux on 2012-04-24
> **CFury said:**
> I also tried manually, no dice.  Both Firefox & Opera behave the same when handling Flash, Chrome is working however this is obviously due to it's independent plugin.  Well I"ll keep hacking at it, I'm sure it will end up being something simple I've overlooked.

If you are using a 32bit system you can copy Chrome's plugin.

Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/), select Advanced mode from the menu and in the installation options, select Google Chrome. Click "Execute" to run the script. It will copy the plugin from Chrome and make it available to Firefox and Opera.

---

