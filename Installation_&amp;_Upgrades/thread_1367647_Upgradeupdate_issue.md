---
title: "Upgrade/update issue"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by mrbutterscotch on 2009-12-29
I recently did a fresh install on an old Dell I had running XP. I figured since my old laptop with a Celeron mobile runs it so well, my P4 desktop should run pretty well too. Anyway, after installing today, I'm unable to upgrade from 9.04 to 9.10 nor install the updates for 9.04. I click install and the administration function pops up and goes away before I can type in my password. The same thing happens when I try to upgrade. Any suggestions out there?

---

### Post by taurus on 2009-12-29
Can you run any update from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```
Use the same password that you're logged in and when you type it, the cursor won't move so make sure you type it in right and hit Return.

---

### Post by mrbutterscotch on 2009-12-30
That worked for getting the security updates, however it didn't work for upgrading to Karmic. Another problem I've noticed is: I can't play mp3's; when I try to install the proper plug in, it says it can't be done. I know drive space isn't the issue because this is a fresh install on a 100 gb HD. Thanks for your help on the first issue.

---

