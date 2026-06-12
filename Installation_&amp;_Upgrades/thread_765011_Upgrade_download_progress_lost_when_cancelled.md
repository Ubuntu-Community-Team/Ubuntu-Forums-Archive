---
title: "Upgrade download progress lost when cancelled?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by obidose on 2008-04-24
I am trying to update my version to the new release 8.04. I have started the update from within ubuntu. It says it will take several hours though and I will need to switch to my windows installation before then. If I cancel the update will i lose the download progress so far?

---

### Post by forestpixie on 2008-04-24
No you shouldn't but there are no guarantees - it should pick up from where it left off. As long as it is only downloading packages though - if you turn it off during the actual upgrade you'll likely have some problems. 

You can check by seeing what state the date on packages in /var/cache/apt/archives are.

I though personally wouldn't do it deliberately, but an accidental stop here when the power went during a download of updates when I installed the beta carried on from where it left off.

---

### Post by obidose on 2008-04-24
It says it is only at the stage 'getting new packages' I assume this means it hasn't done any installing yet as that stage is the next one. I can't wait 10hours for it to do all its downloading right now, I need to use some anatomy packages that only run in windows.

I will give it a shot and see what happens, suppose the worst that could happen is my ubuntu install gets messed and I have do do fresh install.

---

### Post by forestpixie on 2008-04-24
I'm sure (fairly) that as long is it's only downloading then it will just resume from where it finished.

When it starts to install the screen changes, if at the moment it's getting new packages it hasn't started to install them yet.

---

### Post by gitpik on 2008-04-24
While I was updateing to hardy a couple of days ago My router had to be reset once or twice during the download part. It picked up each time right where it left off no problems.

---

### Post by ptcbus on 2008-04-24
For a quick download use torrents. I have listed the steps I followed to upgrade from gutsy to hardy here: [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")  .

---

