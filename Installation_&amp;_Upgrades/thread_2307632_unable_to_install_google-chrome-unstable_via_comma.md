---
title: "unable to install google-chrome-unstable via commandline"
date: 2015-12-26
forum: Installation &amp; Upgrades
---

### Post by bill23 on 2015-12-26
Hey,

Lately Google Chrome stable has been having iss

---

### Post by Vladlenin5000 on 2015-12-27
Chrome (stable) is fine in all my installs.
What is the problem with your exactly? And what made you think that the development branch would be better? It most certainly won't be if the problem is profile and/or addons/extensions/apps related.

---

### Post by MAFoElffen on 2015-12-27
> **Vladlenin5000 said:**
> Chrome (stable) is fine in all my installs.
What is the problem with your exactly? And what made you think that the development branch would be better? It most certainly won't be if the problem is profile and/or addons/extensions/apps related.
Agreed. Normal install under Ubuntu, is usually via visiting the Google Chrome download page > select link > Popup asks if you want to open with Ubuntu Software Center > Yes... then it opens in Software center > Install...

In the past 2 years since this now goes to Software Center, instead of what was the default "deb package manager" ... Every onvce in a blue-moon, I've noticed that sometimes (very rarely, but still does sometime happen) will hang in the Software Center. But if I cancel it and try again, it will then work successfully.

If you select save, then You would have to open a terminal and manuever to the downloaded directory, then install as a .deb package from the commandline... so what difficulty or error are you having? Because your post states a descriptive challenge to, not a problem that can be resolved(?) Is there an issue that we can help you with?  We are trying to guess what assistance you need from your post... Maybe a little more information from you, may help you get the assistance you need.

---

### Post by ptn107 on 2015-12-28
```
wget -c -t0 https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
dpkg -i google-chrome-stable_current_amd64.deb; apt-get -fy install
```

---

### Post by Vladlenin5000 on 2015-12-28
OK, that installs it. Downloading the *.deb, double-clicking it and using whatever GUI packet manager you have (Ubuntu Software Center is currently the default) would do the same.
But your problem with the Google Chrome (stable) is...?? The most important information is still missing.

---

### Post by MAFoElffen on 2015-12-28
> **ptn107 said:**
> ```

dpkg -i google-chrome-stable_current_amd64.deb[COLOR=#ff0000]; apt-get -fy install[/COLOR]
```
First, why the second half of that? 
- Without that, does it say there is broken packages? And possibly in that error message why it is broken?

Because you need to display what ever error messages in this thread, so we can see what is going on. We are not there, so are depending on your description of, to be able to help you...

Guess would be either from a depends problem, or a conflicting package, where installing would break another package you installed.

First, try with prefacing your command with sudo... if you tried using the above command
```

sudo dpkg -i google-chrome-stable_current_amd64.deb[COLOR=#ff0000]
[/COLOR]
```
 without being in a root prompt or without using sudo, (the first line will work, but...) that second line would fail because of inadequate "permissions" errors. That is a guess based on trying to read your mind and all the likely possibilities.

---

### Post by ptn107 on 2015-12-30
```
apt-get -fy install
```
dpkg doesn't resolve dependencies when installing debs so we call apt-get afterward to install anything that google-chrome needed.  Using the software center or gdebi (dpkg gui) automatically does this.

---

### Post by chathamdavid1970 on 2015-12-30
maybe he couldn't figure out what he wanted to say and stopped mid sentence and accidentally posted it....

---

