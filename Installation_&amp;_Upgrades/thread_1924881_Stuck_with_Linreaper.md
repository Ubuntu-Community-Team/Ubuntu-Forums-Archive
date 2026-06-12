---
title: "Stuck with Linreaper"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by nicoldutoit on 2012-02-13
I recently installed Ubuntu Studio 11.04 and have been trying to install Linreaper with this script

[http://dl.dropbox.com/u/278272/Linux/LinReaper0.86.2.run](http://dl.dropbox.com/u/278272/Linux/LinReaper0.86.2.run)

I have had no luck with the chmod +x or sh commands in terminal. What commands should I use? Or am I supposed to compile the script to a .run file first?

Please help!

---

### Post by RockMumbles on 2012-02-18
Latest version is here:
[http://dl.dropbox.com/u/278272/Linux/LinReaper0.87.run](http://dl.dropbox.com/u/278272/Linux/LinReaper0.87.run)


you should :

cd to the directory where the linreaper script is saved.  

chmod a+x LinReaper0.87.run

and then execute the script by using this command:

sh ./LinReaper0.87.run

you have to have the ./ to tell sh to look in the current directory for the script or supply the full path to it.

---

