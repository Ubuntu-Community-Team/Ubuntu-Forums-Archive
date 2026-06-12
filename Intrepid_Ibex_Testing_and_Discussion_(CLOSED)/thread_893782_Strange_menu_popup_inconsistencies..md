---
title: "Strange menu popup inconsistencies."
date: 2008-08-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by storm99999 on 2008-08-18
I was going to check with you guys before filing a bug as to not file a bug for something that could just be a PEBKAC.

Whenever I select a menu at the top of the screen, any one with more than eight or so entries take approximately 300-400 ms to load, while all the others load instantly.  It's especially bad in the System menu, as Administration and Preferences both take that long, and the load is not cached away. 

When I click System, and then highlight Administration it loads instantly, but when switched to it has a long delay.

When I click Applications, when System Tools is highlighted after going past any others, it loads instantly (most of the time), but it has only two entries.

If I select a menu, quickly move my mouse down and back up to the current entry then back down, it loads instantly too.

Lastly, if I scroll down Applications with my mouse, medium sized menus load instantly too up until around 2 seconds of mouse movement, in which the medium sized ones quit moving.

It happens whether Compiz is loaded or not.

First of all, anyone else notice this? Secondly, although it still happens when Nvidia is unloaded, could it have a hand in this?  Thirdly, although I thought menus loading within 30 some microseconds were default, I retested with gtk-menu-popup-delay = 0 in my .gtkrc-2.0, same thing (and even then, historically, 250 microseconds was default, and this is taking about 2x-4x depending on menu size than that).  Lastly, is this genuine of a bug report to report it?

Edit: Additionally, when I was rapidly moving my mouse up and down to test, the office menu got stuck open.  It just stayed there floating for about 5 minutes before disappearing.  I can't reproduce this one though.

---

### Post by vade on 2008-08-18
I notice the same thing. It's somewhat irritating. It's probably by design because it has been like that for ages.

---

### Post by ronacc on 2008-08-18
I seem to be getting the same thing here go ahead and file it and I'll confirm , moving the mouse rapidly the delay is very noticeable .

---

### Post by storm99999 on 2008-08-18
It's a terrible thing to be inconsistent by design.  I thought it was new though, because it had only recently affected me, but I may have forgot as I was trying out KDE 4.1 for a while to see what I liked about it.

I need to get something to definitively time it, as a "one one-thousand" count tells me that the Administration menu takes ~.8 seconds to load, which is ridiculous even if it is supposed to be slow by default.

Edit: I'll report it as soon as I find the best package to report it against.

---

### Post by storm99999 on 2008-08-18
Ok, I posted a bug for gnome-panel (which I hope is the right one) as bug [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/259212](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/259212)

---

### Post by ronacc on 2008-08-18
confirmed your bug .

---

### Post by BTMark on 2008-08-18
I just ran an update and upgrade, and this behavior seems to have been fixed.

---

### Post by storm99999 on 2008-08-19
Although it is slightly faster, I'm still experiencing this in 2.23.90.

---

### Post by Nullack on 2008-08-19
I find that once the bits are cached it all happens right away. Gnome does not initially cache the icons so they have to be read into memory. This is ok IMHO.

Are you sure your not having some sort of issue with compiz on it?

Or, some sort of 2d acceleration issue with your video driver?

I have compiz off and its good for me.

---

### Post by storm99999 on 2008-08-19
I've tried it sans compiz and running on the nv driver. Also, it occurs when moving away from menus too, e.g. Administration -> Log out.

The time to show menu is identical to the time to not show the menu in most cases, too.

---

### Post by Nullack on 2008-08-19
Please be more specific. Which Nvidia driver? Im on beta 177 with no problems, compiz off.

---

### Post by storm99999 on 2008-08-19
Well, 177 normally and the vanilla "nv" driver as a backup test.

---

### Post by ronacc on 2008-08-19
I'm running the 177 driver here and compiz on or off makes no difference,what I notice most is running the mouse up and down the menu the highlighting after a couple of passes lags the mouse pointer and becomes very eratic .

---

### Post by Nullack on 2008-08-19
Ok lets try to diagnose this:

1. Im on a USB mouse
2. compiz off
3. Gnome 2.23.90 (beta)
4. Nvidia 177 beta
5. I am using the gnome menu, which is different to the Ubuntu one - the ubuntu one has three different menus for apps, sys etcetc
6. If I go into say system then admin I can move the mouse up and down for minutes no problems

Whats your observation mate?

---

### Post by ronacc on 2008-08-19
my setup here is .
  

1 usb wheel mouse
2 compiz on ( or off no difference) 
3 basic plain install from alpha 4 (amd64)live cd up to date 
4 nvidia 177 
5 definate lag in popup submenus compared to hardy and this is on a fast box with 4gig of ram and  low system load ( 2>5% each core and 10% ram in use 0% swap in use)

---

### Post by Nullack on 2008-08-19
Ok Im going to create a new user to test ubuntu defaults then.

Ronacc or someone who can replicate the problem, can you please try to see if the issue also occurs with the nv driver loaded instead of the nvidia driver. Many thanks

---

### Post by ronacc on 2008-08-19
no change with nv .

---

### Post by Nullack on 2008-08-19
So I did the new user and didnt notice anything strange. Notes:

1. When Im in the last menu item I can scroll very quickly without problems
2. When Im in a parent menu item, I can still scroll very quickly but if the child menu opens that will come up and it then takes a little while for the parent menu to update. But thats expected I think?

How about we get a short video of the issue (you can record your desktop) so we all know the exact issue

---

### Post by ronacc on 2008-08-19
storm99999 should do the video since he opened the thread . What I am talking about is your item 2 , I have intrepid running one one box and hardy runing on another side by side, they are similar boxes , the one running intrepid has a slightly faster cpu and nvidia card ,both running the 177 driver and intrepid has a MUCH more noticeable lag .

---

### Post by storm99999 on 2008-08-19
Well, I got videos.  Sorry, it appears the program I'm using lacked a red channel, so the videos look odd.  I did my best to show the error.

First, there's a major error (the menus getting stuck open, disabling the main menus):
[Major glitch]("http://www.nilocsoft.com/videos/majorglitch.ogv")

Second, there's the normal problem of menus failing to open consistently.
[Minor glitch]("http://www.nilocsoft.com/videos/minorglitch.ogv")

Hope these help (and sorry it's not in a format most players stream, but it got done quickly).

---

### Post by ronacc on 2008-08-19
the recordings look ok to me in both vlc and totem ,mabye its your player thats flaky not the recordings . I didn't realise that the menus getting "stuck open" was part of the same thing . you can close them by left clicking on the desktop anywhere off of the menus .

---

### Post by storm99999 on 2008-08-19
I tried, but gnome-panel completely locked up on that one.  You can see me try to click on things, but after the menus closed, they wouldn't reopen until I restarted. (That's why I opened Yakuake to kill the recorder, the button on the panel wouldn't work).  However, I cannot consistently reproduce the stuck open menus.  

The other video shows the issue I'm mainly annoyed by.

I should put my system information here:
Amd64 build
USB mouse.
Nvidia 177 and "nv" drivers
Compiz on or off
Gnome 2.23.90
Stock Ubuntu menu.
I doubt anything else has much to do with it, but
4GB ram, Core 2 Duo processor.

---

### Post by ronacc on 2008-08-19
my setup is the same as yours except for the  cpu , I'm amd64x2

---

### Post by storm99999 on 2008-08-19
Hmm, all sorts of possibilities here that aren't localized to gnome-panel:

The problem could lie in 64 bit, maybe poor storage with the panel's visual space, changing it lot slower than 32.

The problem could be competing processors, or both processors getting timesliced for the same task of redoing the frame.

Could be poor quality Nvidia 64bit drivers, stock or 177.

Could be the memory randomization algorithm on >= 4gb systems causes the bug inadvertently.

Not all of them are likely, but it may have something to do with the similar hardware.

---

### Post by ronacc on 2008-08-19
what ever it is it was introduced with intrepid , my hardy install on the same box dosent't do it .I'm betting on it being either the pannel or the menus , both show other problems or those problems may be symptoms themselves .

---

### Post by Nullack on 2008-08-20
Gents that some great work you've done there! Storm99999 thanks for the video.

Sebastien clarified its an upstream issue. I have created the upstream gnome bugreport at:

[http://bugzilla.gnome.org/show_bug.cgi?id=548589](http://bugzilla.gnome.org/show_bug.cgi?id=548589)

:)

---

### Post by ronacc on 2008-08-20
added comments to your report . thanks for opening it .

---

### Post by storm99999 on 2008-08-20
> **ronacc said:**
> added comments to your report . thanks for opening it .

Same here, thanks.

---

### Post by storm99999 on 2008-08-23
Well, as of 1:2.23.90.1-0ubuntu1, the problem appears to have resided.  It hiccups every once in a while, but menu response is nearly instantaneous again.  I'll wait a bit before I close the bugs as fixed, so with any luck, one down.

---

