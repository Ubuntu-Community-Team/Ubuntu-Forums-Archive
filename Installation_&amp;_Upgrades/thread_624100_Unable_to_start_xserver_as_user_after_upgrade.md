---
title: "Unable to start xserver as user after upgrade"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by jdogzilla on 2007-11-26
Hello, I just upgraded from feisty to gutsy.  I can no longer start the xserver as a normal user.  I can start it fine by logging in as root.  The xorg.conf has no real error to indicate the problem.  

I am running kubuntu with an nvidia gt7600 graphics card. 

Is this a permissions problem?  Why can a regular user not start the xserver?

Thanks

---

### Post by jdogzilla on 2007-11-26
Anybody have any suggestions?  I tried reconfiguring the xorg.conf with dpkg-reconfigure. 

The log says the following:

Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, shoudl be 1; fixing.

And that's it.  I created a new account, and could start x with that account.  But even after I move my .kde to .kde-old, I could not start an x session.

---

### Post by ZipoTe on 2007-11-26
Hi jdogzilla!

Let's see... first, start the xserver via "startx" and report any message you see when starting with the "normal" user. Look for some error talking about .xinit or xauth.

---

### Post by jdogzilla on 2007-11-26
Looks like kdm is not starting, or failing at boot.  If I start kdm with 
sudo /etc/init.d/kdm restart, it all works.  What can I do to make sure kdm starts up at bootup?

---

### Post by ZipoTe on 2007-11-27
Try "startx" and report any errors.

Maybe it is a permission error, but I need what your terminal says :popcorn:

---

