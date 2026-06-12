---
title: "[SOLVED] Upgrade to Firefox 3 GTK Problem"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by Craftycorner on 2008-09-23
I have Linux Dapper Drake 6.6 and downloaded the tarball for Firefox 3, unzipped it and tried to run it.  It came up with this error:

> 
We're sorry, this application requires a version of the GTK+ library that is not installed on your computer.

You have GTK+ 2.8.
This application requires GTK+ 2.10 or newer.

Please upgrade your GTK+ library if you wish to use this application. 

How do I make the required upgrade?:confused:

The download came from:
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)
The program came from:
[http://download.mozilla.org/?product=firefox-3.0.1&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-3.0.1&os=linux&lang=en-US)

---

### Post by Partyboi2 on 2008-09-23
You can download GTK 2.10 from [[COLOR=Blue]here[/COLOR]]("http://www.gtk.org/download-linux.html") and compile it. This also might help
[http://www.captain.at/howto-run-firefox-3-debian-etch.php](http://www.captain.at/howto-run-firefox-3-debian-etch.php)

---

### Post by Craftycorner on 2008-09-23
How do you 'compile'?

---

### Post by lmno745 on 2008-09-23
What is World of Warcraft?Players from across the globe can leave the real world behind and undertake grand quests and heroic exploits in a land of fantastic adventure and [yoga mats]("http://www.yoga-mats.cn/") . Do you want to [China Travel guide]("http://www.china-travel-guide.cn/") yourself?So please let us do this task for you, one of our World Of Warcraft powerlevelers work for you as a full- time job other than part-time.s a massively multiplayer online game, World of Warcraft enables thousands of players to come together online and battle against the world and each other. As we know, When you first start a game of World of Warcraft, you will be taken to your race's starting area. All the races except trolls and gnomes begin in a unique location.So it takes a long time to powerlevel a powerful character for many players, for the player's energy and time are limited. [http://www.yogawww.com](http://www.yogawww.com), [http://www.chinatravelvip.com](http://www.chinatravelvip.com), WOW Power Leveling is our primary service, we offer [wow gold]("http://www.wowchina.us/") & [wow gold]("http://www.wowgoldsell.com/") service,and is on sale now for a limited time! You can purchase our power leveling service at a much lower price than any of our competitors. We don't use any Bots or Macros to power level your character.All of our employees are skilled World of Warcraft players, who personally powerleveling your character, to provide even more safety to your account.  We will complete the wow power leveling in a very short time, and you can play the character at your desired level. During the progress of World of Warcraft powerleveling, you can get all information about your World of Warcraft powerleveling status anytime.We use real players (WOW Power Leveler) to level your character, ALL HAND MADE. Your account will be safe and secure,GUARANTEED.Our goal is to make sure all our customers are satisfied with their wow powerleveling & [cheap wow gold]("http://www.howtogold.com/") orders. We upgrade your characters levels, skills and more.safety to your account.[http://www.yogawww.com](http://www.yogawww.com), [http://www.chinatravelvip.com](http://www.chinatravelvip.com), [www.wowchina.usOur](www.wowchina.usOur) team consists of veteran players with over 1 years of playing experience, they offer quality and professional service to all our customers. No risk is ever involved during this process.Our staff will not chat to anyone during this progress, so don't afraid about your character.Our service is standing by 24/7 to serve you.

---

### Post by Partyboi2 on 2008-09-24
Open a terminal and install build-essential package if you have not already got it install
```
sudo apt-get install build-essential
```
Then download to your Desktop  gtk+-2.10.14.tar.bz2 from the link I provided above. 
Then move it into the /opt directory
```
sudo mv ~/Desktop/hello-2.1.1.tar.gz /opt
```
then change into /opt
```
cd /opt
```
extract it
```
tar xjf gtk+-2.10.14.tar.bz2
```
then make a directory called gtk210
```
mkdir gtk210
```
then change into the new extracted directory
```
cd gtk+-2.10.14
```
then run ./configure using the gtk210 directory that you made as the prefix
```
./configure --prefix=/opt/gtk210
```
If no errors then type
```
make
```
If no errors then
```
sudo make install
```

---

