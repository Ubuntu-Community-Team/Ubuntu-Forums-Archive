---
title: "Xubuntu 10.04 Beta 2"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mesmith on 2010-04-21
This thing is a gem.

I have been stuck at 8.10 forever.  9.04 & 9.10 were disasters for me.  I wasn't sure I even wanted to try Lucid.

Ran it up a few days ago and was astounded.  Moved my data over yesterday and am using it full time.

Great job, everyone.

---

### Post by aviramof on 2010-04-21
Xubuntu is indeed a great edition i really liked it my self the only downsite i found was the lack of compatible
 softwares for instance there is no remote desktop software there and other networks tools can you check and 
see if the problem still exist?
 
and i also have one more downsite to all of this editions and that it that you can't use auto login if you want to be able to 
replace between DM'S because the panel at log off don't appear unless you start typing password and if you use auto login then that never happen.

---

### Post by NightwishFan on 2010-04-21
Anything that follows free desktop standards should work fine with XFCE.

---

### Post by mesmith on 2010-04-21
Remote desktop software comes with Xubuntu Lucid, and I assume plenty of network software will work.  Gigolo also comes with Lucid.

---

### Post by aviramof on 2010-04-21
Well there isn't remoe desktop there by deafult and i tried to install gnome software and it didn't work and i think i have tried a few more things and it didn't worked either 
that is why i formated(i'v installed from xubuntu cd not ubuntu then installed xubuntu) and went back to ubuntu.

---

### Post by 4Orbs on 2010-04-21
Yes, Xubuntu 10.04 is very nice and runs noticeably smoother and quicker than Karmic. Now that I have the nvidia legacy driver installed and running properly (the fix can be found in another thread), there's nothing to complain about. Xubuntu also lends itself quite well to an Openbox session. And the icing on the cake is that I can actually empty the root trash bin in Thunar with no hassle involved.

---

### Post by mesmith on 2010-04-21
I'm not that technical a user, but tell me about your comment on the root trash bin.

Thanks

---

### Post by 4Orbs on 2010-04-21
Unless the standard (Gnome desktop) Ubuntu has changed recently, any files you move to trash while working as the root user cannot be emptied from the root trash bin by just clicking on the "Empty Trash" button (while logged in as root user). Trying to do so just returns a permission denied error. However, if you are using Xubuntu (Xfce desktop, which uses Thunar file manager rather than Nautilus) you can empty the root trash bin (while logged in as root) in the same way you empty your regular user's trash bin.

I guess it's really not a big issue, but it is one of the many reasons I have preferred Xubuntu over Ubuntu for the past three years.

---

### Post by Yellow Pasque on 2010-04-21
> **aviramof said:**
> Well, there is no remote desktop there by default and I tried to install gnome software and it didn't work.
There's an option in xfce to start gnome or kde services, so apps that need that stuff work.

---

### Post by aviramof on 2010-04-22
ok that is nice to know but it would also be nice if this option is turned on by default and all 
the basic software that come with ubuntu would come with xubuntu.

---

### Post by aviramof on 2010-04-22
ok that is nice to know but it would also be nice if this option is turned on by default and all 
the basic software that come with ubuntu would come with xubuntu don't need more then that the rest of the softwares 
i need i can install for my self but i can't start running to start installing things like tsclient and vinagre and etc it's like installing
 gcalctool or gnome-panel this are things that already should be there by default.

---

### Post by XubuRoxMySox on 2010-04-22
> **aviramof said:**
> ...it would also be nice if ... all the basic software that come with ubuntu would come with xubuntu.

If that is what you want, then just use Ubuntu and add Xfce to it:

```
apt-get install xubuntu-desktop
```

One of the oldest and most frequent complaints about Xubuntu is that it was "bloated," meaning that it still had way too much Gnome cruft for an Xfce distro.

Lately, though, it seems that the Xubuntu developers have realized this and corrected it, much to the great delight of most Xubuntu users. We won't want Ubuntu with Xfce tied on, we want Xubuntu *without* all that extra Gnome stuff!

If you want all the Gnome/KDE weight and bloat, then use regular Ubuntu and add Xubuntu-desktop (and kubuntu-desktop, OpenOffice, anchors and anvils and concrete blocks) and weigh it down all you want. It's always easier to add stuff than to trim unwanted stuff off. My poor li'l hand-me-down 'puter can't carry that much extra weight, and LXDE is still buggy as heck on it. 

Light and simple,
Robin

---

### Post by aviramof on 2010-04-22
i don't want all the Gnome/KDE weight and bloat but i do want that xubuntu would have it's own parallel softwares like an 
xfce tsclient and when i tested xubuntu not to long ago it didn't have tsclient or any similer or parallel software.

---

### Post by miegiel on 2010-04-27
Is none of you having this really annoying thunar bug?
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/520118](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/520118)

---

### Post by 4Orbs on 2010-04-27
Thanks for bringing it to my attention. I rarely use the "Detailed" view, so haven't run into this yet. Now that I know about the bug and how to sidestep it, there's one less unpleasant surprise lurking in the shadows.

---

### Post by Slug71 on 2010-04-27
I quite like Xubuntu too. If Gnome Shell doesnt quite work out for me Xubuntu will take its place. 
I wish Xubuntu would use Packagekit and the smartpm backend by default though.

---

### Post by 4Orbs on 2010-04-28
Other good things:
Xfce compositing works very nicely with the stock Nouveau driver, so now I can finally have transparent titlebars and panels without sluggish scrolling in firefox or jerky motion when dragging windows across the desktop. And I can finally get the oddball 1152x864 screen resolution without using the nvidia driver. Nouveau is pretty cool. Now if I could only figure out how to install Diablo 2 in Wine without the nvidia driver I'd be babbling with delight. And another thing; I see they fixed the Gnome System Monitor so there is no more text smearing when scrolling down the running processes window. The more I look, the more I like.

EDIT:
Well, I was wrong about the system monitor, still smears the text. Google Earth needs the nvidia driver in order to run smoothly on my old desktop. Still, Nouveau is pretty cool.

---

### Post by aviramof on 2010-04-28
Why does xubuntu-desktop wants me to remove ubuntu-desktop and libsdl1.2debian-pulseaudion ?

and why does xubuntu ppa not working?
[https://launchpad.net/~xubuntu-team/+archive/ppa]("https://launchpad.net/%7Exubuntu-team/+archive/ppa")

---

