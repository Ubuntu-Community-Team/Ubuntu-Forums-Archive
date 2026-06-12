---
title: "Media Player problems"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Bablefish on 2007-05-18
I just want to know if there is a fix for 2 bugs I came aceross in running first of all VLC Media Player. I love this program for years and have it in my Windows PC as it just plays everything. So when I found it in that Add / Remove list I had to install it. Well anyway it plays my MP3s but when it comes to the Quicktime files. It plays the without sound. Any fixes?

The other bug is a real pain in the you know, I recently upgraded that Totem Movie Player with the cinepak version that is also found in the Add / Remove section after discovering that the one that came with my intial install of Ubuntu would not play and VCD or any uncopyrighted DVD. But when I did this I came across something I swear I have NEVER SEEN BEFORE in any software I ever used. When I place some Optical Media in my CD/DVD drive this message pops ups.

There is not plugin to handle the location of this movie.

---

### Post by trippinnik on 2007-05-18
I'm not really sure about totem cinepak, as I don't usually use the Add/Remove function for software.  Do you have the repositories for Restricted formats enabled?  I recommend checking out this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
Also I have had good success using totem-xine, it's fairly lightweight and plays almost all the video I have thrown at it.  Gstreamer framework is the most popular (and default) way to handle media files, however it has many plugins and to have it work you'll need to make sure you have them.

---

### Post by Bablefish on 2007-05-18
I tried this along with a command line trick I found in the Help menu of Totem

IE sudo /user/share/docs/libdvdread3/install-css.sh

and I still have the same problem

By the way it was the Xine Backend edition not the cinepack as I first said

---

