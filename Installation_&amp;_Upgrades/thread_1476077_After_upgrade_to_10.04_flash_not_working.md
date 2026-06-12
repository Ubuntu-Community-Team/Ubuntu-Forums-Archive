---
title: "After upgrade to 10.04 flash not working"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Kiwisaft on 2010-05-07
Hey,

Since I upgraded to Ubuntu 10.04. I am not able to watch youtube videos anymore, it says " You need to upgrade your Adobe Flash Player to watch this video". Then there is a link to adobe. But when I download and install it says "Package 'adobe-flashplugin' is already installed". So I tried to remove and reinstall - no change. Then I tried to remove and install flashplayer-nonfree - no change. 
Tried it with firefox and seamonkey.

Hoping for ideas...

---

### Post by Kiwisaft on 2010-05-07
Additional info:

- When I test it on [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) it says "You have version 10,0,45,2 installed"

- I have a 32Bit System

- Tried both flashplugin-nonfree and adobe-flashplugin (APT for Ubuntu 9.04+)

---

### Post by driebel on 2010-05-07
I had some painful flash issues too.  I posted a thread on the absolute beginner's forum yesterday (just search for my user name over there) and a user named 'carlee' provided me with a flash installer she wrote that fixed everything.

---

### Post by Kiwisaft on 2010-05-08
You mean this one: [http://ubuntuforums.org/showthread.php?t=1475441](http://ubuntuforums.org/showthread.php?t=1475441) ? Unfortunately I think we have different problems. It installs correctly but I still have problems with using it.

I read through so many posts but nobody seems to have the same problem :/ please help!

---

### Post by slice16 on 2010-05-08
Hi Kiwisaft,

Have you tried re-installing flash from the 'Ubuntu Software Centre'? 

You can two options, the Adobe Flash Plugin (under search) or the offical flash plugin under Canonical Partners.

Regards,

---

### Post by Kiwisaft on 2010-05-08
ah now sth did the trick: rm ~/.mozilla/plugins/libflashplayer.so 

Before I tried all different kinds of removing and reinstalling packages from different sources. 

thanks

---

### Post by andy16666 on 2010-06-13
Same problem. Stock 10.04 install. Youtube worked this morning, and this afternoon. But suddenly about an hour ago it started telling me that I need to upgrade my flash player.

---

### Post by rabble on 2010-06-14
I also have this problem. Flashplugin-installer does work after I reinstall it; but, if I shut-down Firefox and reopen it, flash again does not work and I have to reinstall Flashpluging-installer. How to fix this?

---

### Post by dfarrell07 on 2010-06-28
My girlfriends laptop was having the exactly the same trouble as the OP. I quit Firefox, uninstalled flashplugin-installer via Synaptic and installed flashplugin-nonfree. Flash seems to be working normally now.

---

### Post by larry on 2010-08-08
Dear All,
I do not know if this other problem is related: my girlfriend has just pointed me out that this page (online shop of a site)

[http://www.freitag.ch/shop/FREITAG/shop.jsf](http://www.freitag.ch/shop/FREITAG/shop.jsf)


correctly shows an animation if visited from windows whereas you see nothing from firefox+ubuntu 10.04.
Does anyone else share her problems when he/she visits that site?
Cheers

larry

---

### Post by lads on 2010-08-16
Hi everyone,

This thread is flagged as solved but there's no solution provided. 

I upgraded to 10.04 last week, removed and re-installed the flash player several times in several ways, but Firefox simply ignores it. Meanwhile, everything working fine with Chrome. Is this a Firefox issue or an Ubuntu issue? Maybe time to leave Firefox behind?...

Thanks.

---

### Post by lads on 2010-08-17
Hello everyone,

I tried the adobe-tools installer suggested in this thread:

[http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)

I removed and re-installed Adobe but the result is the same, Firefox asks to install it every time a web page loads some flash content.

Is there any other flash player one can use with Firefox?

Thanks,

Luís

---

### Post by johnshore on 2010-08-22
Hi
I've had the same problem with Firefox ever since I upgraded to 10.04.  Same with Seamonkey; and Epiphany just crashes.

I've just installed Chrome and it works perfectly.  Must be time to (regretfully) leave Firefox behind.

John

---

### Post by mörgæs on 2010-08-22
> **johnshore said:**
> Hi
I've had the same problem with Firefox ever since I upgraded to 10.04.  Same with Seamonkey; and Epiphany just crashes.

I've just installed Chrome and it works perfectly.  Must be time to (regretfully) leave Firefox behind.

John

A lot of problems on this machine... Does it work with a 10.04 live CD?

---

### Post by mango42 on 2010-08-22
> **johnshore said:**
> Hi
I've had the same problem with Firefox ever since I upgraded to 10.04.  Same with Seamonkey; and Epiphany just crashes.

I've just installed Chrome and it works perfectly.  Must be time to (regretfully) leave Firefox behind.

John

Same problem here but is this a technical or political issue? 

ISTM just about 'everyone' is being herded into the 'g00gle-sphere'. Look how the very word 'g00gle' has become a verb! Yet there are far better, more comprehensive search engines available that do not trample on the rights of humanity (eg: [https://startpage.com/](https://startpage.com/) ).

Is this situation healthy? Certain countries think not and are now pursuing g00gle through their courts. Why?

---

### Post by lads on 2010-08-24
There's a new development now with Firefox, when it loads a page with some flash content it asks to install missing plug-ins, but unlike before, it actually downloads and installs some package. The result is the same though.

Has anyone here tried some Firefox forum? Can a link be provided there?

Thanks,

Luís

---

### Post by mörgæs on 2010-08-24
Here is everything that is worth knowing of Firefox:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by lads on 2010-08-25
Thanks mörgæs that did it.

The solution for me was at this page:

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Scrolling down to the section "Flash doesn't work or I get an error on some web pages asking to install flash, but I have already installed the latest version." it explains that I probably had more than one flash player installed creating a conflict.

This is the recipe:

```
sudo apt-get purge lightspark
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f /home/**/.mozilla/plugins/*flash*so
rm -rf /home/**/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

After that I restarted Firefox and all flash contents started working ok.

Thank you,

Luís

---

### Post by johnshore on 2010-09-11
> **lads said:**
> Thanks mörgæs that did it.

The solution for me was at this page:

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Scrolling down to the section "Flash doesn't work or I get an error on some web pages asking to install flash, but I have already installed the latest version." it explains that I probably had more than one flash player installed creating a conflict.

This is the recipe:

```
sudo apt-get purge lightspark
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f /home/**/.mozilla/plugins/*flash*so
rm -rf /home/**/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

After that I restarted Firefox and all flash contents started working ok.

Thank you,

Luís
Thank you both.  I went through the terminal commands you posted and it worked fine (repaired Epiphany too)

---

### Post by thebigdaddy0 on 2010-10-20
Suddenly my flash stopped working. After a few days pulling my hair out and cursing my computer I uninstalled **GNASH SWF viewer** and now all is well with the world. All working again. Curse you **GNASH**. :mad:

---

### Post by Irina Korova on 2010-11-18
@lads: may God give you long life and good health!! :D I was trying for days to solve this issue and I nearly gave up - you save me ;)

---

### Post by CyborgSmurf on 2010-11-19
Maybe flash is named for what it is. It only works in one flash in youtube and that's it. #14 helped me out, with the Flash-Aid add-on for firefox. Thanks alot! :)

---

### Post by lads on 2011-01-04
To the admins:

This same issue is also occurring after the upgrade to Ubuntu 10.10. There might be something wrong with the upgrade procedures that embroils Firefox. Luckily the recipe I dug out solves it with this new version as well:

```
sudo apt-get purge lightspark
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f /home/**/.mozilla/plugins/*flash*so
rm -rf /home/**/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

You may consider changing the thread's title to include a reference to Ubuntu 10.10.

Best,

Luís

---

### Post by mörgæs on 2011-01-04
Is it also a problem with a clean install of 10.10?

---

### Post by pollixx on 2011-01-31
> **lads said:**
> Thanks mörgæs that did it.

The solution for me was at this page:

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Scrolling down to the section "Flash doesn't work or I get an error on some web pages asking to install flash, but I have already installed the latest version." it explains that I probably had more than one flash player installed creating a conflict.

This is the recipe:

```
sudo apt-get purge lightspark
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f /home/**/.mozilla/plugins/*flash*so
rm -rf /home/**/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```After that I restarted Firefox and all flash contents started working ok.

Thank you,

Luís

Thank-you!  This worked perfectly for me!

---

### Post by boroborolama on 2011-02-23
Thanks Luis (a.k.a. lads).  I must have had some other flashplayer '.so' file installed.  The Ubuntu Software Center claimed otherwise, but the command line solution worked wonderfully.

Thank you.

---

