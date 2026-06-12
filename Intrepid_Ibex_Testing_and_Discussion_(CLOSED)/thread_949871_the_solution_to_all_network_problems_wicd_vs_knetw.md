---
title: "the solution to all network problems: wicd vs knetworkmanager"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by linomac on 2008-10-16
to install wicd 
1. we add the following line at the file /etc/apt/sources.list
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras
2. wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -
3. sudo aptitude update
4. sudo aptitude install wicd
it will automatically uninstall networkmanager, knetworkmanager.

it has tray icon.
it works perfectly and flawlessly.
it has great settings.
no need to edit /etc/network/interfaces 

Please give it a try

And then consider

Does it worth all the pain and misery with knetworkmanager with all it's problems and lack of features? 
Why should we use a 0.7 svn program and not a complete and mature program as default at kubuntu?

I propose wicd to be the default networking program.
It works perfectly.

I suppose there are no technical reasons to avoid using wicd as default networking programs.
I hope there are no political reasons to stay away from it from the official distribution.

Thanks. Please vote which you would like to be the default networking application at intreipd

---

### Post by imdano on 2008-10-16
See this post about why wicd isn't going to replace NM: [http://ubuntuforums.org/showpost.php?p=4438094&postcount=66](http://ubuntuforums.org/showpost.php?p=4438094&postcount=66)
You might also want to read the thread that post comes from, since its on the exact same topic.

---

### Post by linomac on 2008-10-16
"
But for now it's probably better for a distro like Ubuntu to stick with an app like NM as the default, which has features like VPN plugins, dialup support, etc., that we don't have yet. Features like that might not be important at all for a lot of users but they are important for Ubuntu to have included by default. Until these things get integrated into wicd I don't think the Ubuntu team will make the switch."

yes the matter though that knetworkmanager is not final version yet, it has a lot of problems, and there are a lot of complaints heard that there are not so many developers on kubuntu, or that ubuntu focuses more on gnome.
i think networkmanager right now works better in gnome than kde.
maybe i have wrong impression

---

