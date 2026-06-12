---
title: "Freq out of range"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by lunxer on 2005-07-23
I'm trying to install ubuntu Hoary Hedgehog but when the x server first starts i get freq out of range for my monitors.
Here is my setup 
Nvidia 6800 LE with 2 monitors attached, one viewsonic e92f+ 19" and one older IBM G74 17"
Tried to get in with safe mode and change /etc/X11/xorg.conf and remove all other res then 1280x1024, still the same issue (tried later with only 640x768,same thing)
I have never before installed Ubuntu so i have no idea whats on the screen (x server conf?)
I have not even set the root pass :O

---

### Post by supanova on 2005-07-27
Hi

Get the specs of your montors

I.E. Display size, Horizontal Sync and Vertical Refresh rate

but before you do this you should try

#sudo dpkg-reconfigure xserver-xorg.... answer all the questions... I think that their is a tutorial somewhere on the ubuntu wiki (not sure)

If your monitors are not picked up automatically there will be place to add the details you collected.

Be careful as giving the incorect details can damage your monitors  [-X 

What I have noticed is that sometimes even if you manually enter them they do not appear in your xorg.conf file.

Make sure you have the following in the sections defining your monitors

DisplaySize x y (dimensions... e.g. 360 270)
HorizSync x.y - a.b (e.g. 30.0 - 96.0)
VertRefresh x.y - a.b (e.g 50.0 - 160.0)

Also check out your BIOS.... older ones can be full of #@!$.

The installation will never ask for a root password to be set...

You need to read up on sudo on the wiki

Hope this helps you somewhat

Ciao

---

