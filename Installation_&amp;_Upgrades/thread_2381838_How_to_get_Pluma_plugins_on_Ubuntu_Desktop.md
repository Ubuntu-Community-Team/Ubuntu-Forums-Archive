---
title: "How to get Pluma plugins on Ubuntu Desktop?"
date: 2018-01-05
forum: Installation &amp; Upgrades
---

### Post by owlcroft on 2018-01-05
I recently did a fresh install of Ubuntu Desktop on my laptop, as a preliminary to trying it on my workhorse desktop rig.   I quickly discovered that the Gnome 3 version of gedit--a program I use an awful lot on my desktop 14.04 setup--is a total disaster as to convenience of use.  Postponing my rant, I decided to try Pluma, and installed it from the ordinary repositories (v. 1.18).  I love it.  BUT...

As installed it is lacking many plugins, some of which are vital to me (such as bookmarks).  So I went looking for pluma plugins, and so descended into Hell.  There do not seem to be any pluma plugins available as simple Synaptic click-and-install packages analogous to the various gedit plugin packages.  Nor do there seem to be any other repositories that have such things.  I am not experienced in compiling software, but I tried it with the yselkowitz/pluma-plugins package at GitHub.  I will spare you the tale of the seemingly endless tedious hours spent trying to indentify then track down sources for the dependencies, then the dependencies of the dependencies, and so on and so forth.  I finally got to the stage (after adding a PPA, and downloading numerous packages, each of which seemed to entail a dozen or two more items) where it seemed ready to go, but then Lo! it tells me it can't do most of the plugins owing to "no python support", despite my having loaded everything python-related ever mentioned anywhere.  Then when I tried to proceed with the few that seemed they would go ok without python, I hit "fatal error: pluma/pluma-plugin.h: No such file or directory".

I am about ready to pack it in and try to struggle along with the Gnome3 gedit, but the idea sends shivers down my spine.

Can anyone offer any useful advice?  Is there, after all, some secret repository where one can actually get packaged pluma plugins?  Or does anyone have ideas on how i could get past the python and pluma-plugin.h issues?  Did the switch from pluma 1.16 to 1.18 vitiate the 1.16 plugin packages?

<rant>
 Why do the Gnome people seem to feel nowadays that the primary purpose of a piece of software is to get a blown-up 
 screencap of it hung on the walls of the Museum of Modern Art?
</rant>

---

### Post by cruzer001 on 2018-01-05
Hi Eric

I think this is not a gnome3 problem, but the gtk3 version.  Another casualty of our old apps being upgraded or just dropped.  

Can't help you with pluma (i do not use it), but its a popular subject in the UbuntuMate forums as its their text editor of choice.  May want to post there too.

Good luck

---

