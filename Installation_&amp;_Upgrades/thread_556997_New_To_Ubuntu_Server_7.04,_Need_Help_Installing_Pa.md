---
title: "New To Ubuntu Server 7.04, Need Help Installing Package Off A CD!!!"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Juggz on 2007-09-22
Recently I received an old Compaq Presario 5BW175 from a buddy of mine & I decided to set it up as a home file/print server. I downloaded Ubuntu Server Edition (I have dial-up, so it took quite awhile… ;)).

I am completely new to Linux, this was my 1st installation of Linux, went flawless, yay! Bye, bye Win98!!!

I decide that I would like to install gnome-core to have a simple GUI to get the feel for things visually. From what I noticed, the gnome-core package is not included in the server installation, like I said in the beginning I have dialup & the Linux box is only connected to my local network through my router, so I decided to download a copy of the gnome-core package & burnt it on one of the countless blank cd’s I have lying around with my main workstation & tried to install it on the server via cd.

The thing is I can’t figure out how to access the package, I’ve tried countless methods on this forum.

Sudo aptitude, then searching for the package

Sudo apt-get install & “the package”

Sudo aptitude install & “the package”

Sudo Dpkg -I & “the package”

& some others, I think, been a couple ;). 

Anyone know how I might get gnome-core installed from the disk that I burned?

Also, any tips or recommended applications that would help this old box perform it’s duty better as a file/print server would be much appreciated! 

Thanks very much in advanced!!! :)

---

### Post by kerry_s on 2007-09-22
that won't work, gnome-core is a meta package it installs several things.
anyways the command is> **sudo dpkg -i name-of-deb**

but you need to install X first, as in xorg(**sudo apt-get install xorg**) which is a meta package to and just installs other packages.

with out internet it's going to be pretty hard to getting anything, and your best bet would be something smaller than gnome-core, all you need is a simple wm, something like jwm or fluxbox.

if you can attach it to your modem to install it would be easier.

**sudo apt-get install xorg jwm mc**
then
**startx**

you might want to try puppy or dsl, i think the both have servers, but i think only puppy has cups. there both small and both have gui.

---

