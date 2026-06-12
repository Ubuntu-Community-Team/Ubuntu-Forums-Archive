---
title: "Minor/Random display problems"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by gvblake22 on 2007-05-01
Ok, I first want to make it clear that I know virtually nothing about Linux.  I've been using Windows XP for years and am fluent in computer hardware, but Linux is out of my league.  With Vista currently being a terrible upgrade path I decided to go the way of the Penguins and try Ubuntu.  I installed the x86 32-bit Feisty Fawn 7.04 and it all went pretty well for the most part.  However, my problems started when I tried to get video drivers set up for my onboard nvidia GeForce 6100 IGP (Gigabyte GA-M61PM-S2 motherboard and AMD Athlon 64 X2 3600 Brisbane processor).  The System/Preferences/Screen Resolution window only allowed me to change the resolution up to 1024x768 at either 50hz or 53hz refresh rate.  I'm running a [Gateway FPD2485W 24" LCD]("http://www.gateway.com/accessories/product/1541000R.php?seg=hm"), so I obviously wasn't too excited about a 1024x768 maximum resolution.  With the help of a friend from another computer forum, I was able to edit some xorg.conf thing and add 1920x1200 as a resolution (just replaced 1024x768 with 1920x1200 in all of the lists).  

That fix seemed to work, as I now have a full screen resolution, but ever since that little edit I am having different issues.  Now when I am using Firefox and I click a link that opens in a new window, that window is all black (but the title bar and stuff show up correctly).  Even the contents of the page that is supposed to be displayed are loaded (I can blindly click links if I know where they are located on the page).  Sometimes if I just minimize the window and restore it, everything shows up correctly, but other times I can't seem to get it to show up at all.

The other problem I'm having is that when I maximize a window (say Firefox for example) it sortof gets "stuck" and when I click on the title bar or a mimize, maximize, or close button.  The title bar just turns to the white inactive color, but I can still use the contents of the window, so it's not frozen or anything.  I have to right click the task bar and select "unminimize" for that window and then it works again.

Any ideas on any of that?  Did I do something wrong with the nVidia driver?  I don't think I actually even installed any driver, it was just already there.

---

### Post by Belyel on 2007-05-01
I'm not sure if the open source driver will support a resolution that high very well.  I know you won't be able to get any 3D effects going (in games/applications) with just the nv driver that is included with Ubuntu by default.  I would recommend checking out a package called envy that you can find at [this website.]("http://www.albertomilone.com/nvidia_scripts1.html")  Follow the directions and look around ubuntuforums (this board) for more information about your xorg.conf file and how it can be your friend.  The envy script will install the full drivers for your nvidia chipset so you can use all of its features.  This will probably fix the problems you are having.

---

### Post by gvblake22 on 2007-05-01
Well, I'm really not concerned with 3D performance, just that the 2D capabilities of system are up to par and will play nice with my monitor.  I'll give Envy a shot, that looks like it might be the ticket, thanks Belyel!!:)

EDIT:
Looks like there are no stable versions of Envy available for Feisty 7.04, will it be ok to use the latest stable version that looks like it is for edgy 6.10?

---

### Post by Belyel on 2007-05-01
Stability is a relative term :).  I've used the supposedly "unstable" on both my comps and it works fine.  I think that it would work better than the one for edgy, at any rate.

---

