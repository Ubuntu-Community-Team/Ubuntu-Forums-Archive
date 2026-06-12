---
title: "Upgrading Blender"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by Jem Masters on 2009-11-19
Hi all!

   I have a question, is there a way to upgrade Blender 2.48a for Ubuntu 9.04?  I was searching in the synaptic and I couldn't find it, there was the 2.48a version.  The thing is that I don't want to download 2.49 directly from the web because I don't have any idea of where to put all the content of the folder ( I don't know if something shall go to /bin or etc ...), any help guy's?


Thx in advance.

---

### Post by squaregoldfish on 2009-11-19
I upgraded Blender by uninstalling the supplied version and installing from the Web. This is how I set up all the files:


Extract the folder, and put it in /usr/local
Make a symbolic link to the folder named as /usr/local/blender
Make a symbolic link in /usr/local/bin pointing to /usr/local/blender/blender

And you're done!

When a new version is released, perform the first two steps above - the symbolic link in /usr/local/bin ensures that you'll always execute the new version.

Steve.

---

