---
title: "unable to install ubuntu  from live cd"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by gumdrop66 on 2008-03-20
Hi all
I'm sure this has been asked a million times, and I have searched this question a million times but am not quite sure what to do.
I am Installing newest ubuntu on SECONDARY blank hard drive..not along with winxp pro:


I cannot install ubuntu from the cd (live) and i downloaded alternate cd-it boots, i get the ubunto logo splash screen..orange line moving etc-then my screen goes blank-I don't understand how to turn off 'apci' or where to type that, or where to type 'no splash' etc
i tried all that to no avail-
i have a fairly new HP computer, 1.5 gb ram..the firstHD has windows xp pro(for games and stuff) the second HD is 40 gb(for linux)
I've read all the answers to this  question and just do not comprehend I apologize.I have used linux in the past..but not this newer version of ubuntu-and not on a secondary HD-I have deleted the windows partition on the 2nd HD,hoping ubuntu would load and install making a partition-I'm thinking of going back to fedora, but want to re ally use ubuntu -I like it and it seems like a nice system..fedora gave me headaches. :(
if someone is to reply to me..please be gentle-I'm not that good with this linux stuff..I cannot figure out how to get it to boot/install with splash off..or with apci off-I tried
I even tried hitting f6-but do not understand which to chooose.thanks all
dee
:confused:

---

### Post by dstew on 2008-03-20
Do you have both the Live CD and the Alternate Install CD, or just the Live CD? I do not think that the Alternate Install CD uses a splash screen. It should work for you.

---

### Post by Pumalite on 2008-03-20
If you can boot a Live CD, post:
sudo fdisk -lu

---

### Post by gumdrop66 on 2008-03-21
nothings working still ive tried live and alt. cd
cannot install at all :(

i dont understand what you mean by 
If you can boot a Live CD, post:
sudo fdisk -lu
Im sorry
please exlain? I'm fairly new
I've used fedora before and all
but that was on one HD not secondary
and I tried ubuntu years ago and liked it
so-this ubuntu is going on 2nd HD...could it be that 2nd HD is a windows partition? I'm confused..thanks again
dee

---

### Post by Touch.Code on 2008-03-21
Sure!

Click Applications --> Accessories --> Terminal and type in: sudo fdisk -lu

---

### Post by jan quark on 2008-03-22
there are some users which encounter issues with the live cd
these are very often graphical issues

so if you still have a cd with the alternate version on it try to run it once again
try to follow this installation guide by herman:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

and tell us to which point it works and when it stops according to the images in the guide

---

