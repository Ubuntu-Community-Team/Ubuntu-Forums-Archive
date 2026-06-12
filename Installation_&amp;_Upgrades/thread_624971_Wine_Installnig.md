---
title: "Wine Installnig"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Richard Proctor on 2007-11-27
I have absolutly no clue as to how to get or install wine as all the versions ive downloaded all come up as having "dependancies" and wont install

can someone give me clear cut step by step instructions on how to get wine up and running on my computer?

---

### Post by rolodoom on 2007-11-27
Well I use Wine from the Wine HQ repository.

Usually you add the repository line to your sources.list, then reload your software lists, install and then configure. The next are the steps for Ubuntu Gutsy.

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
winecfg

```For more information you can go to Ubuntu WineHQ Page:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Well that's pretty much it.

---

