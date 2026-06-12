---
title: "update freeze"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by jesse c on 2008-03-30
my gutsy system shows the icon indicating there are updates available,so i click on it and enter my password.It now says i can only do a 'partial upgrade'  due to something i have running in my system. I click on the partial update option and the download starts and then freezes. this download freeze affects my whole system and i have to shut down and restart.Does anyone know what might be going on and how i can do the updates available?
thanks jesse c

---

### Post by housam on 2008-03-30
try to extend your[[COLOR="Red"]_ repositories _[/COLOR]]("http://www.psychocats.net/ubuntu/sources")and then try again to update.

---

### Post by prcm311 on 2008-03-30
I'm getting this same error.  The two updates it wants to install are Firefox related.  I tried to include pre-release updates which now brings the total to 28, but still none of them install.  What is the code to run if there is a power failure/act of god during updating?  I think that might fix this.

---

### Post by Pumalite on 2008-03-30
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade

---

