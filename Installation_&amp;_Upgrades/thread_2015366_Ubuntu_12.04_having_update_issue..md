---
title: "Ubuntu 12.04 having update issue."
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by kojimasnake on 2012-07-03
My power had been out for 4 days due to severe weather. My laptop had been in suspend when the power went out. When the power came back i let my laptop charge. I turned it on, everything loaded up great I thought. Then u got a weird message saying something about a partial update or upgrade i cant really remember. Also I now have a theme issue as well. Unable to see items in drop down menus when i hover the mouse over them. Anyone have any clue what has happened.

---

### Post by dino99 on 2012-07-03
uninstall then reinstall that theme

---

### Post by raja.genupula on 2012-07-03
> **dino99 said:**
> uninstall then reinstall that theme

+1 and dont go for partial upgrades ever  . That will take your system to unstable state .

---

### Post by prshah on 2012-07-05
> **kojimasnake said:**
> Then u got a weird message saying something about a partial update or upgrade 

If you are getting a message about partial upgrades, it only means that the update manager is not able to resolve a certain update situation.

Using the Terminal (Dash-Terminal) give the command```
sudo apt-get update
``` When it is finished, give the command```
gksudo update-manager
``` Refresh (Check) if required, and install if you get no errors. 

if you get the error about a partial update again, please proceed. Subsequent to the completion of the partial update, please repeat the above steps. The situation should resolve itself, but you may have to "partial upgrade" multiple times.

On the other hand, if you are facing errors with an interrupted update (apt-get update gives an error about dpkg) then please run the command```
sudo dpkg --configure -a
``` to complete the interrupted update.

Please post back with error details if it is not fixed.

---

