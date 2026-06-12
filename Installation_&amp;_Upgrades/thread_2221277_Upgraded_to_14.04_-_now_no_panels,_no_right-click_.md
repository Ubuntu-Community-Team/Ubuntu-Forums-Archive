---
title: "Upgraded to 14.04 - now no panels, no right-click menus, just wallpaper!"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by robbaskerville on 2014-05-01
Hi everyone, and thanks in advance for any help.

I just upgraded Xubuntu 13.10 to 14.04 via the update manager and have struck a problem.

The log-in screen functions perfectly, but when I go to the desktop, I just have the wallpaper and a mouse pointer.  The top panel is missing.  (I think this version doesn't have a bottom panel by default).  I can move the mouse pointer fine, but there is no response to any clicking.

I was able to Ctrl-Alt-F1 into a tty and install icewm.  I re-booted and logged into an icewm session, and it is working perfectly, so it is not an Xorg issue.

Does anyone know how to get my beautiful Xfce back, or should I try a fresh installation from scratch?

Also, this may be unrelated, but I just noticed that a process called tumblered is chewing up 100% of one of my cores.  A quick google says that this can be cause when downloading media files, but I am not doing that.  As I say, that is probably an unrelated issue.

Thanks,

Rob

---

### Post by ajgreeny on 2014-05-01
> Tumbler is a D-Bus service for applications to request thumbnails for various URI schemes and MIME types. It is an implementation of the thumbnail management D-Bus specification described on [http://live.gnome.org/ThumbnailerSpec](http://live.gnome.org/ThumbnailerSpec).That is from the tumbler package description in synaptic, so I suppose it could be something to do with the system attempting to make a thumbnail for some media file that you're downloading, however, I doubt that it is anything to do with your desktop problem.

Try renaming the .config/xfce4/ or .config/xfce4/xfwm4 folder in your home as backups, then login again to xubuntu and see if that gets you back to a proper xfce4 desktop.

---

### Post by foxy123 on 2014-05-01
I had a similar problem with my previous updates. It had something to do with Unity config files (in my case as I use Ubuntu). In any case, the easiest way of solving it without a complete reinstall was to create a new user, then rename the existing user's home into something else and rename the new user's home to the previous user's home. Then you should do

sudo chown -R user:user /home/user

and copy all files (apart from config and other hidden files) to a new home folder. It worked for me.

---

