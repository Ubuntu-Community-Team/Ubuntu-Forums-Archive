---
title: "Creating a modified installation disc"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by redvenomweb on 2010-08-10
Hi.  I have recently been doing more and more Ubuntu installations for friends and family, and I'd like to streamline my process a bit.  My goal is to create a 10.04 installation CD that does the following:

installs 10.04 with all current security updates
installs ~15 repository packages
installs one package from a .deb file I provide
installs sun-java6 (and related packages) and configures it as default java
runs /usr/share/doc/libdvdread4/install-css.sh
add ~30 images that I provide to the default desktop background directory
configures default media applications (for media filetypes) to the applications I designate
turns off sound file preview
adds desktop links to home folder and trash (I normally do this through gconf-editor)
adds links for selected programs to desktop
changes theme to clearlooks (with customization)
sets number of desktops to 1

These are all things I do on every installation, and I'd like to automate this going forward.  I'd like these changes to be applied to every new user that's created (not unlike modifying the Default User folder in Windows XP).  I'd also like to know how to add updates to my installation disc in the future.

Finally, if possible, I'd like to create this install on both a DVD disc and a USB stick, if possible.

Thanks for any help.

edit: To clarify, I'd like to have the installation media do all of these things without accessing the network (I may have been vague on that point).  I can access the network to grab necessary packages to create the media, of course.

---

### Post by robert shearer on 2010-08-10
remastersys ?
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

---

### Post by linux18 on 2010-08-10
ubuntu customization kit will get you a few of those, but you'll have to work on the live cd directly for the other ones. I can help, but I'm already overloaded with work.

---

### Post by redvenomweb on 2010-08-12
I was able to install and configure remastersys, and I think I've gotten it to do about 95% of what I want.  The only problem I've run into is the creation of new folders for new users.

The remastersys guide that I saw advised to install and configure Ubuntu with a single user, then (after your configuration is complete) copy the files from /home/$user to /etc/skel and chown them to root.  I did that, but I didn't copy the folders that Ubuntu generates by default (Documents, Pictures, Music, Downloads, etc).  After creating the custom Live CD and installing it, I don't have any of those standard folders; notably, I don't even have a Desktop folder, so my desktop displays whatever is in my home folder.

At this point, I need to figure out how to do two things:

1) I'd like all the standard Ubuntu folders created in /home/$user (and have them properly tagged so that they are listed in the Places menu) when a new user is created

2) There are 3-4 desktop icons that I would like on the desktop of each new user

Any suggestions?  My first thought would be to dump all the standard folders in /etc/skel, but I'm uncertain that they will be flagged properly (e.g. music programs opening the Music folder by default) if I do so.

---

### Post by linux18 on 2010-08-12
sudo apt-get install xnest
sudo Xnest -ac :1

then carefully follow this guide:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

once you make it to the section that starts with:
**Custom Background for GNOME**

type these into the chroot terminal:
export DISPLAY=:1
metacity &
gnome-panel

then you can make all the customizations you want!
just follow the rest of the guide to finish

---

### Post by redvenomweb on 2010-08-12
Well, I tried copying all the extra folders to */etc/skel* and it seems to properly flag them.  However, they didn't show up in Places (which was not unexpected), so I had to add them manually through the Bookmarks menu.

I'd like to avoid having to do this on each install.  In which file is individual configuration data for Nautilus bookmarks stored?


edit: Nevermind, found it... *~/.gtk-bookmarks*

The problem I'm having is that *.gtk-bookmarks* (the one I copied to */etc/skel*) refers back to the folders in the original imager's home directory.  Why is *.gtk-bookmarks* propagating from */etc/skel* as */home/imager/* instead of inserting the appropriate path for new users?  I tried modifying it to /~/ but nautilus doesn't seem to like that.

---

### Post by redvenomweb on 2010-08-14
The solution was to delete .gtk-bookmarks from /etc/skel.  All working and happy now.

---

