---
title: "[SOLVED] Gutsy Upgrade Repositories not working!"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by plr4ever on 2007-10-18
I just installed a pre-release Gutsy last night, although i cannot figure out which release it is. However, when i try to use update manager, change my software source repositories, or do anything that involves repositories period, i get a consistent error:  

[B]Could not download all repository indexes

then it says the the repository is old or because of network problems.


[http://archive.canonical.com/ubuntu/dists/gutsy/Release:](http://archive.canonical.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  commercial/binary-i386/Packages in Meta-index file (malformed Release file?)[/B]


I partially updated some things last night, but canceled during the install before shutting down. I have changed my software source mirror a few times tonight, and i still get the error that canonicals mirror is defunct. 

Any clues?:confused:

---

### Post by Kalrog on 2007-10-20
You say this is solved?  I'm still getting the same thing (but for the AMD64 version)

---

### Post by plr4ever on 2007-10-21
Well i did not exactly solve it, i just clean reinstalled it. I could not figure out for the life of me what it took to get that repository working, although i did notice the problem:

When connecting, the server looks for the directory gutsy-commercial. This makes sense, as all the previous versions are xxxxx-commercial. However, if you visit the archive.canonical.com website, you find that the gutsy directory does not have the -commercial tag on the end of it, meaning gutsy is looking for a folder that doesnt exist and canonical needs to update.

Hope this helps, or gives someone a possibility to fix it.

---

### Post by dushkal on 2007-10-24
try partner instead commercial

try this in the sources.list

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

---

