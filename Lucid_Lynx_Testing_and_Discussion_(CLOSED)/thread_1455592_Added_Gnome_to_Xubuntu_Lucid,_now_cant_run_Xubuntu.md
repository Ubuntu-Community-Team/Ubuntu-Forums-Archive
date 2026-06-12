---
title: "Added Gnome to Xubuntu Lucid, now cant run Xubuntu WM"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mister_p_1998 on 2010-04-16
Updated my Intrepid install to Lucid, all went well, if rather slow, thought Id see how the system ran under gnome, so installed Ubuntu-desktop, worked ok,but I prefer Xubuntu so logged out, chose Xubuntu logged back in again, still in Gnome! I created a new user and that one goes into gnome ok, but my user is stuck in gnome. Help! let me out!
Steve

---

### Post by mine070 on 2010-04-16
Only thing to do is reinstall. I tried out kde and I was stuck with it.

---

### Post by 3Miro on 2010-04-16
> **mister_p_1998 said:**
> Updated my Intrepid install to Lucid, all went well, if rather slow, thought Id see how the system ran under gnome, so installed Ubuntu-desktop, worked ok,but I prefer Xubuntu so logged out, chose Xubuntu logged back in again, still in Gnome! I created a new user and that one goes into gnome ok, but my user is stuck in gnome. Help! let me out!
Steve

Check this one out:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Note that this is for kubuntu. The command ends with installing kubuntu desktop and you don't want to do that. What you should do is check out the package names after:
```
sudo apt-get remove package1 package2 ....
```
and remove the one at a time.

Hopefully this will uninstall gnome and you will be able to go back to xfce. If this doesn't work, you can uninstall xfce also and then reinstall it.

NOTE: I HAVE NEVER DONE THIS, IT IS POSSIBLE FOR THE ABOVE TO RENDER YOUR MACHINE UNUSABLE. 

You should be able to press Ctr + Alt + F1 at any time, but this is helpful o nly if you know how to use the console well.

Make sure you have a live CD so that you can use it to boot into your system if something goes wrong with the above.

---

