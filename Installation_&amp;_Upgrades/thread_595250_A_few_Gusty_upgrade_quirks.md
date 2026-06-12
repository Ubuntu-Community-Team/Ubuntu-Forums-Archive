---
title: "A few Gusty upgrade quirks"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by dsowerby on 2007-10-28
Have been running Feisty for quite a while on desktop PC

The upgrade (using the option from update manager) from Feisty to Gutsy went reasonably well,  though there seemed to be a lot of "do you want to keep the /xxx/.conf file prompts - hopefully I hit "keep" for all of them, but I was tired ..!

Strangely the Thunderbird icon disappeared from the panel.  Simple to fix of course, but my wife beat me to the PC when the upgrade finished ...

A few irritating but not major problems remain:

**Tomcat** doesn't respond to anything except [http://localhost:8180/admin/](http://localhost:8180/admin/) - which works fine.    Any other URL just gives a completely blank page.

**PDF from Firefox**  Clicking a pdf link in Firefox results in a page with the "Loading .."  message, but nothing else.  Downloading and opening directly with eVince works fine

**Totem** Lost the ability to play videos - I haven't been through a re-install yet

**Backuppc** can longer find the server - "Unable to connect to BackupPC server"




Any thoughts/clues welcome, I'm not very far up the expert user scale - bit of a shame though, I was hoping for a completely clean upgrade, but at least nothing major broke.

---

### Post by nozdormu on 2007-10-28
The evince thing seems to be a common problem.  Embedding it with mozplugger worked in Feisty, but not now.

---

### Post by dsowerby on 2007-10-29
Not so bad after all 

Tomcat fixed by re-install
Totem fixed by re-install
Backuppc fixed by fixing Tomcat

just the pdf files left, , but that's not much of a problem.

David

---

### Post by mgmiller on 2007-10-29
> PDF from Firefox Clicking a pdf link in Firefox results in a page with the "Loading .." message, but nothing else. Downloading and opening directly with eVince works fine


I had this exact same problem after upgrading from Feisty to Gutsy.

Make sure you have the medibuntu repos installed.
If not, go here and follow the instructions for adding the repo for Gutsy and adding the gpg key:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Finally, go into synaptic and search for acroread.  You should find 4 packages. I installed all of them.  From a Firefox point of view, the most important is the mozilla-acroread package.

(Note-this is a "non-free" package, so you have to click to accept Adobe's license agreemant the first time you use it.)

Or if you just want a quicky from the command line:
```
sudo apt-get install mozilla-acroread
```

This will install 3 of the 4 packages for you, and after restarting Firefox, pdf's should work great.

After installing them, you need to close and reopen Firefox for it to take effect.

Good Luck.  :popcorn:

---

