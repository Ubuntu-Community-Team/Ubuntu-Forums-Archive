---
title: "Problem with snaps on new install"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2020-04-26
I recently installed ubuntu 20.04.
I installed emacs, and it won't run (except as root).
When I try to run it, I get the error
>emacs
cannot create user data directory: /mnt/hd1/home/asb/snap/emacs/296: Permission denied

My home directory is /mnt/hd1/home/asb

Permissions for directories
/mnt/hd1/home/asb/snap
/mnt/hd1/home/asb/snap/emacs,
and
/mnt/hd1/home/asb/snap/emacs/296 
are all 755.

How do I fix the permisions error?

Failing that, can I install packages without snap?

---

### Post by TheFu on 2020-04-26
**sudo apt install emacs** doesn't work? Some snap packages are embedded inside .deb packages, unfortunately.

There is a command to allow some snaps, if configured by the snap packaging team, to have access output /home ... I would hope that snaps aren't hard coded to /home and allow access to whatever directory the getent passwd $USER returns, but I have doubts.  Anyway, the command is:
```
snap connect {insert snap package name}:removable-media
```
so
```
snap connect chromium:removable-media
```
would be for the Chromium-browser.  The snap package creator decided NOT to use the .deb package name for Chromium.
Guessing that emacs snap package name is emacs, 
```
snap connect emacs:removable-media
```
would allow access to /mnt/ and /media/ in addition to $HOME. That's the theory.

[https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022](https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022)

I'm with you concerning snap packages.  Looked at using AppImage packages, but they have some funky runtime stuff to, so we can't just create a symbolic link to the package-name.appimage file to run it without the pesky constraints the snaps force.

IMHO, snaps are broken by design until the local admin has a way to control the constrained file access locations.

---

### Post by asb3 on 2020-04-26
Your suggestion failed:
 > snap connect emacs:removable-media
error: snap "emacs" has no plug named "removable-media"

emacs has no defined interfaces

> snap interfaces emacs
error: no interfaces found

I don't remember how I downloaded emacs.  Whatever I did, it installed it in /snap/bin.
I installed it again using
sudo apt-get install emacs.
It installed it in /usr/bin, and it runs correctly.

How do I remove the previous installation?

---

### Post by deadflowr on 2020-04-26
> How do I remove the previous installation?
Anything in /snap/bin is a snap package, so use 
```
snap list
```
to see installed snaps.
And then
```
snap remove <snap-package -name>
```
replacing snap-package-name with whatever the name of the snap is that shows for it.

The remove command should prompt for a password, but if it doesn't just run it with sudo.

---

### Post by asb3 on 2020-04-26
All fixed. Non-snap emacs installed, snap emacs removed.

---

### Post by TheFu on 2020-04-26
The "snap connect" only works if the snap package creator allows it, as mentioned above.  
You and I don't have any say beyond - install or remove of the snap package. That is our choice.

---

### Post by chrisonbuntu on 2020-06-17
> **TheFu said:**
> The "snap connect" only works if the snap package creator allows it, as mentioned above.  
You and I don't have any say beyond - install or remove of the snap package. That is our choice.

I'm on Ubuntu MATE 18.04 and Vidcutter installed by SNAP couldnt open video files on my SD card, or anywhere outside of the ~/snap/ folder!  I had the same issue with not being able to 'connect' it either!  A quick 'snap remove vidcutter' got rid of it and "flatpak install flathub com.ozmartians.VidCutter" got a working version :)

I know snap is getting a lot of hate in the linux news at present, which I actually think is mostly overblown, but these complications are very frustrating to have to deal with.

Flatpak isnt perfect either, but so far I have had more success with *using* the installed apps.  The snap sandbox is far too restrictive by default and there isn't a clear way to choose its settings on install.  A quick set of Y/N questions for the common 'connections' at install time would be a great improvement.

---

### Post by CatKiller on 2020-06-17
> **chrisonbuntu said:**
> A quick set of Y/N questions for the common 'connections' at install time would be a great improvement.

You mean like this one? 
[img]https://149366088.v2.pressablecdn.com/wp-content/uploads/2018/07/spotify-snap-app-in-the-ubuntu-software-store.jpg[/img]

---

