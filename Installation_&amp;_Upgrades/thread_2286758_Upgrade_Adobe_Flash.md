---
title: "Upgrade Adobe Flash"
date: 2015-07-14
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2015-07-14
I have warning that I have an unsafe plugin Adobe Flash. It obviously needs to be upgraded. I don't find the upgrade in the synapse. How do I do upgrade it? 

I have refreshed firefox 2xs. I goes away but when I open a new window it reappears.

---

### Post by coffeecat on 2015-07-14
Hello, Camilia.

I've seen this in one up-to-date installation of Ubuntu 15.04 trying to view a youtube video in Firefox, but not in another 15.04 with Firefox and youtube - at least yet. I wonder if this is not an Ubuntu problem, but rather this:

[https://threatpost.com/mozilla-disables-flash-in-firefox/113763](https://threatpost.com/mozilla-disables-flash-in-firefox/113763)

I have nothing constructive to offer at the moment, but would be interested in anything anyone else can say.

---

### Post by slickymaster on 2015-07-14
You can check whether you have, or not, the the latest supported Flash player just by comparing the one on your browser, going to Tools » Add-ons » Plugins and the version info at [https://www.mozilla.org/plugincheck/](https://www.mozilla.org/plugincheck/)

If you do need to update it, open a terminal window and run```
sudo /sbin/update-flashplugin-nonfree --install
```

---

### Post by Camilia on 2015-07-14
> **slickymaster said:**
> You can check whether you have, or not, the the latest supported Flash player just by comparing the one on your browser, going to Tools » Add-ons » Plugins and the version info at [https://www.mozilla.org/plugincheck/](https://www.mozilla.org/plugincheck/)

If you do need to update it, open a terminal window and run```
sudo /sbin/update-flashplugin-nonfree --install
```
sudo /sbin/update-flashplugin-nonfree --install gives me  sudo: /sbin/update-flashplugin-nonfree: command not found

At link found:
Adobe Flash Player Shockwave Flash 11.2 r202 up to date. 
Shockwave flash is known to be vulnerable

---

### Post by slickymaster on 2015-07-14
> **Camilia said:**
> sudo /sbin/update-flashplugin-nonfree --install gives me  sudo: /sbin/update-flashplugin-nonfree: command not foundThat means that you have the adobe-flashplugin package, not the flashplugin-nonfree package.

[What's the difference between flashplugin-installer and adobe-flashplugin?]("http://askubuntu.com/questions/49298/whats-the-difference-between-flashplugin-installer-and-adobe-flashplugin")
[flashplugin-installer vs. flashplugin-nonfree vs. adobe-flashplugin]("http://askubuntu.com/questions/15408/flashplugin-installer-vs-flashplugin-nonfree-vs-adobe-flashplugin/15410#15410")

> **Camilia said:**
> At link found:
Adobe Flash Player Shockwave Flash 11.2 r202 up to date. 
Shockwave flash is known to be vulnerable
Maybe related to [https://helpx.adobe.com/security/products/flash-player/apsa15-04.html](https://helpx.adobe.com/security/products/flash-player/apsa15-04.html)

---

### Post by grey1beard on 2015-07-14
Re your #3, I have checked my current version to be 11.2.202.481 in Firefox /Addons/ Plugins, where it also says "Use with caution".
The Blocked list site says it's blocking 11.2.202.484 and below.
As I have no idea what to do next in terms of finding a Flash Player or equivalent to allow me to watch the BBC videos, I'd be grateful for some guidance.
Running 12.04 (on an HP g7000, 1.86GHz x2, 32 bit), and have no desire to upgrade.

---

### Post by monkeybrain20122 on 2015-07-14
> **grey1beard said:**
> Re your #3, I have checked my current version to be 11.2.202.481 in Firefox /Addons/ Plugins, where it also says "Use with caution".
The Blocked list site says it's blocking 11.2.202.484 and below.
As I have no idea what to do next in terms of finding a Flash Player or equivalent to allow me to watch the BBC videos, I'd be grateful for some guidance.
Running 12.04 (on an HP g7000, 1.86GHz x2, 32 bit), and have no desire to upgrade.


Chrome would work, it has up to date flash bundled (18.0.0.209) 

You can use flash 18 in Firefox with a wrapper (this works very seamlessly)
[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

If you are in the U.K and watching videos on Iplayer you can also watch them without flash [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/) (someone has tested it on another thread and confirmed that it worked for IPlayer videos though not on the news page)

---

### Post by Camilia on 2015-07-14
> **monkeybrain20122 said:**
> Chrome would work, it has up to date flash bundled (18.0.0.209) 

You can use flash 18 in Firefox with a wrapper (this works very seamlessly)
[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

At that link suggested to use with google chrome so I added google chrome. No problems with google chrome.

---

### Post by Bashing-om on 2015-07-14
people: Hey hey .

As the saga unfolds:
> 
2015 Jul 14: Ubuntu releases adobeflash-plugin and flashplugin-nonfree with updates for PPAPI only

[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/FirefoxAndAdobeFlashNPAPI](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/FirefoxAndAdobeFlashNPAPI)

[INDENT][INDENT]maybe some relieve
[/INDENT][/INDENT]

---

### Post by grey1beard on 2015-07-15
I'm sorry, but for myself, a 76 year old with trouble remembering what day of the week it is, this is far too much information.
It's taken me 24 hours to notice the significance of the difference between adobe-flashplugin from Adobe, and flashplugin-installer from Canonical, and  I haven't enough time in my day, trying to survive, to become conversant with this type of problem solving.
To sum up, could some kind soul post a couple of lines of code that I can paste into Terminal and get it sorted ?
MITA

Poor old John aka grey1beard(not without reason !)

---

### Post by slickymaster on 2015-07-15
After Firefox blocked the browser plugin [Adobe fixes two Flash zero-day flaws]("http://www.computerworld.com/article/2948142/malware-vulnerabilities/adobe-patches-flash-to-quash-last-two-zero-days-unearthed-in-hacking-teams-cache.html") found in Hacking Team cache.

---

