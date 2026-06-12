---
title: "edgy - blue background image while starting gnome after adding xfce to ubuntu"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by xdevnull on 2006-11-04
I am sick and tired of blue!  People may complain about ubuntu brown, but it is nice after all the blue I've been staring at for years!

I am new to ubuntu, after several years of using Suse.  So far so good, but I like having another window manager in case there is a problem with the one I'm using.  That way if gnome won't start I can use a light weight environment (say, xfce) to login and trouble shoot using both a command line as well as the tools provided with a window manager.  

So I installed the xubuntu desktop according to the recommendation on the xubuntu.org website:

sudo apt-get install xubuntu-desktop

No problems.  It seemed to work except that I now have the xubuntu login screen, which is blue, which I hate.  So no problem - I go into the login-screen applet under System and change it back to the one I want.  

BUT

Now when I login to my default session (gnome) there is this blue screen that comes up in the background - that I just know is the xubuntu background.  It goes away after the session comes up (I think after the panel is populated), but I know that behind my nice brown ubuntu background there is lurking the blue xubuntu background eating memory.

I had a similar problem with Suse before.  If you installed both gnome and KDE, and then went into either/both of them, you would get these background artifacts that never went away.  You would see them every time you logged in and every time you logged off (especially if you installed compiz with KDE).  Not the way I want to be using my precious memory resources.

So - why and where does this happen and how can I fix it?  Does this have something to do with X or the xdm/gdm/kdm thing?

Thanks

---

### Post by boban on 2006-11-04
I think you could try (in Gnome): System->Administration->Login Window. There you have background color under theme selection...

---

### Post by xdevnull on 2006-11-04
Thanks!  Dude, that was so easy it actually pisses me off!

---

