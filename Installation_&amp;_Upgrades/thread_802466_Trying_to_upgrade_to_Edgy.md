---
title: "Trying to upgrade to Edgy"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by rebelxt on 2008-05-21
I am trying to upgrade my Dapper system to Edgy (been on Dapper for a couple years).  Can't get it to work.  Went looking for reasons why.  Found this page:
[http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html]("http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html")

Down at the bottom is:
> #  drew Says:
February 5th, 2008 at 10:34 am
Trying to get upgraded to latest version of Ubuntuand cannot get 6.10. My terminal says… gksudo update manager
warnings.warn(”apt API not stable yet”, Future warning)
Then nothing. The Update Manager finds no upgrades Ijust got and installed the 6.06. Were are the install upgrades? Thanks

# Alberto Says:
February 21st, 2008 at 9:00 pm
I have the same problem as Drew (#52). Only difference, I have been working with 6.06 for quite a while. Is this a problem with the repositories, or something else?

# Ben Says:
April 7th, 2008 at 5:20 am
Same problem as #52 and #53
is there an answer to this?
thanks

This is the same problem I'm having.  Anyone have a solution?

---

### Post by wpshooter on 2008-05-21
My "guess" is that the problem lays in the fact that Edgy is not supported anymore.

Why don't you go to either Gutsy or Hardy instead.  My recommendation would be Gutsy for now.

Good luck.

---

### Post by rebelxt on 2008-05-21
There is no place in this sequence to select the upgrade target.  It just doesn't let you do anything.

---

### Post by zvacet on 2008-05-21
There is no need to upgrade from supported release to unsupported one.It can be done but i don´t see any point of doing that.Just make sure that your Dapper is up-to-date with 

```
sudo apt-get update && sudo apt-get upgrade
```

and after that you can directly upgrade to Hardy.Instructions are [here.]("https://help.ubuntu.com/community/HardyUpgrades")

---

### Post by rebelxt on 2008-05-21
> **zvacet said:**
> There is no need to upgrade from supported release to unsupported one.It can be done but i don´t see any point of doing that.Just make sure that your Dapper is up-to-date with 

```
sudo apt-get update && sudo apt-get upgrade
```

and after that you can directly upgrade to Hardy.Instructions are [here.]("https://help.ubuntu.com/community/HardyUpgrades")

I tried this; no-go.

The apt-get worked; then, as described in the instructions pointed to by your link, ran the update-manager. The attachment is a screenshot of what I ended up with, which is a little different from the screenshot shown in the instructions.  I wouldn't say the differences are significant, because the update-manager says the system is up-to-date.  The problem is that the window that says the new release is available does not pop up.

Any thoughts?

---

### Post by Pumalite on 2008-05-21
Try this:

sudo sed -i 's/dapper/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

