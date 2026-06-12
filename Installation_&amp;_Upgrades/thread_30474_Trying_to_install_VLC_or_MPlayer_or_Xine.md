---
title: "Trying to install VLC or MPlayer or Xine"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by STFU Donny on 2005-04-28
I just want to watch these divx/avi files and I'm confused about repositories. How do I install them? I'd like to use VLC becuase I am familiar with it. I followed these instructions from the website: 
 Add the following lines to your /etc/apt/sources.list:

     deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) woody main
     deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) woody main

For a normal install, do:

   # apt-get update
   # apt-get install gnome-vlc libdvdcss2

I get this error message after typing 'apt-get install gnome-vlc libdvdcss2': 

The following packages have unmet dependencies:
  gnome-vlc: Depends: vlc (= 0.7.0-0woody.4) but it is not going to be installedE: Broken packages

I added those lines to the sources.list and executed those commands but it wont install this one package. 

I have Debian GNU/Linux right? 
I tried the sudo command also. 
Or if anyone could recommend another media player, it wouldn't work with Totem movie player. This is my first time using linux! I like it so far. Just used to double clicking on exe's  ;-) 

If there is a good FAQ on installing programs with Ubuntu, I'd like to see it because I don't understand. If I got this installed how would I execute it?

---

### Post by geo on 2005-04-28
VLC is in the universe repository.  To get it on a fresh 5.04 install:

use Synaptic to edit your repositories. Menu Settings/repositories.
edit the binary and source hoary repositories by adding

universe multiverse

to the existing "sections" area, which should already contain main restricted.

Then hit the reload button and your synaptic will go get the indexes for universe and multiverse.

Then use synaptic to search for "vlc".  Installing "gnome-vlc" will get everything you need.

George

---

