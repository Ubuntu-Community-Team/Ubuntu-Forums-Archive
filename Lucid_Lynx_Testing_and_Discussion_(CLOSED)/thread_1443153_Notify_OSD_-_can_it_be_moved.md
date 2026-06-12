---
title: "Notify OSD - can it be moved?"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-03-30
I was just trying to close a tab on FF when the tune changed on Rhythbox and just covered the tab right up.  This is not the only time it has done this or similar thing to interfere with what I am doing.

If there is a way to reconfigure this so that it is moved back up where it belongs I would really like to know what it is.

Ignoring plymouth and related issues there are only 2 things that are bugging me on 10.04.  That is pretty good for a grumpy geezer.  This is the BIG one.

I kind of hate to bring this up after surviving 9.10-testing.  Seems kind of trivial but it really is getting on my thungas.

---

### Post by 23meg on 2010-03-30
If it's the notification area that you're trying to move, make sure it's unlocked by right clicking its handle (on the left side) and unticking "Lock to Panel", and then move it either by middle clicking anywhere on it, or right clicking the handle and choosing "Move".

The same goes for the indicator applet except that you can right click anywhere on it.

---

### Post by ranch hand on 2010-03-30
Ah, once again I am not clear.  It is the actual notice that I am asking  about.  The one that pops up on top of what your are doing.  I will  provide a screen shot.

In the picture the notice does not look intrusive to excess.  When you get your cursor on or very near it, it gets bigger.  This causes excessive stimulation of the language, at least with me.

---

### Post by chrisccoulson on 2010-03-30
You can't change the position of the notification bubbles. However, you should be able to click through them to perform actions on windows underneath them. This hasn't been possible for a few days though due to a change in GTK. A fix was uploaded for that a little while ago though

---

### Post by 23meg on 2010-03-30
You mean Notify OSD, for future reference. Note that it fades out as you hover over it, revealing the content behind it.

There's no *default* way to configure its position. If you want all notifications in the upper right all the time, like in Ubuntu 9.04, [there's a PPA for that]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/438536/comments/22"). If you want to configure where exactly it appears, there are various branches/packages with modifications that let you do that; a web search for "notify osd position" should bring them up.

---

### Post by ranch hand on 2010-03-30
It does not fade for me but I have not done the upgrades on here for tonight.  I have them ready but need to check my "throw away" installs to see that nothing breaks.

I will load that ppa on one of my other installs too and see how that works out.  I just absolutely hate where that bugger pops up.  It covers things I want to see on my boinc manager screen, FF, nautilus, OOo word processor and OOo spread sheet.  Some times you just have to wonder what the guys that think this stuff up are on or if they just do not use Notify OSD (see I am learning).

EDIT
Gee, not very courteous besides grumpy.  Thanks a whole bunch for the info, education and the link to the PPA.

---

### Post by Mr. Picklesworth on 2010-03-30
Hi Ranch Hand,

Usually you are able to click through Notify-OSD's notification bubbles. There is a temporary regression, though, which makes that impossible. It will be fixed shortly ;)
(In fact, may have just been).

[https://bugs.launchpad.net/bugs/546650](https://bugs.launchpad.net/bugs/546650)

Edit: Yep, fixed with the latest updates.

---

### Post by ubunterooster on 2010-03-30
Slightly to the left of the notification panel is a little dot. Right-click this.

---

### Post by scradock on 2010-03-30
> **ubunterooster said:**
> Slightly to the left of the notification panel is a little dot. Right-click this.
Unfortunately,the little dot is invisible in the pitch-black (so-called Light?) theme currently favored.......

---

### Post by ubunterooster on 2010-03-30
right-click slightly to the left of the left-most notification icon until you get a menu with the following: >  Help
About
-------
Remove from panel
Move
--------
Lock to panel 
Uncheck "lock to panel".
Click move.
Move it; hopefully.

It is like stabbing in the dark, but we know pretty much where it is.
EDIT: on another theme, there is a group of 3 lines to the left of the notification area. Look for the slightest variation

---

### Post by ranch hand on 2010-03-30
> **Mr. Picklesworth said:**
> Hi Ranch Hand,

Usually you are able to click through Notify-OSD's notification bubbles. There is a temporary regression, though, which makes that impossible. It will be fixed shortly ;)
(In fact, may have just been).

[https://bugs.launchpad.net/bugs/546650](https://bugs.launchpad.net/bugs/546650)

Edit: Yep, fixed with the latest updates.
I am not able to click through at all right now and it has always been iffy.  The real point is that it is a stupid place for it to be in the first place.

I have not done the updates for this evening except on my 2 "throw away" installs.  They are, for now, toast.  No booting in normally or recovery.  Nearly total freeze either way (Alt+SysRq+b works).

I think I will wait and see what further updates do before using them on this install or my Lubuntu installs.  I have some other installs that can be used to test further updates for at least another 3 days with out hurting any install that I actually use.

I have also clicked all over the the "bubble" and never found a place that will kill it.  I really do not care either as if it was not positioned perfectly to be as in the way as it can be it would not be a problem.

When the update problem clears so that I can try the ppa stuff on one of my other installs (no real experimenting on this one) I will have it on here so that I can live with it.

---

### Post by 23meg on 2010-03-30
> **ranch hand said:**
> EDIT
Gee, not very courteous besides grumpy.  Thanks a whole bunch for the info, education and the link to the PPA.

Thanks for that edit; it means a lot to me.

---

### Post by ubunterooster on 2010-03-30
Put your mouse so the rightmost pixel of the pointer is on the leftmost pixel of the leftmost icon in the notification area and right-click there. [I have three computers of completely different screensizes, yet these proportions are still correct to get that menu for all of them.]

---

### Post by ranch hand on 2010-03-30
> **ubunterooster said:**
> Put your mouse so the rightmost pixel of the pointer is on the leftmost pixel of the leftmost icon in the notification area and right-click there. [I have three computers of completely different screensizes, yet these proportions are still correct to get that menu for all of them.]
This is interesting but move it where.  The notification will still be there unless I remove the applet completely.  That would be alright as it doesn't work right (yet) but then there would be no way to actually turn off rhythmbox.

---

### Post by Mr. Picklesworth on 2010-03-30
> **ranch hand said:**
> This is interesting but move it where.  The notification will still be there unless I remove the applet completely.  That would be alright as it doesn't work right (yet) but then there would be no way to actually turn off rhythmbox.

Don't let the crazies confuse you :P
There are about 6 posts in this thread from people who think you are talking about a panel applet; that's one of them.

> **ranch hand said:**
> I am not able to click through at all right now and it has always been iffy.  The real point is that it is a stupid place for it to be in the first place.
To the first sentence: Naturally. The fix I talk about was just pushed a few hours ago, so when you update (and restart) you will see notify-osd behaving as it should. When you click on a notification, your click will pass straight through so you can interact with whatever is beneath it. The idea is to be simple, helpful and unobtrusive; like a well-paid butler.
Are you upgrading from Hardy? This functionality has been pretty well the same since 9.04.

The reason for the notification bubble not being flush with the top right of the screen is that there are two kinds of notifications: synchronous confirmations and asynchronous messages. Synchronous notifications appear when you adjust your volume with the keyboard, change screen brightness, press the Eject key, etc. The synchronous notifications are meant to appear immediately no matter what or they won't make sense, so if another notification is showing it could either replace it or be shown alongside it. The decision was taken to show both synchronous and asynchronous notifications side by side. (Note that notification messages are usually queued, shown one by one).

However, it was problematic because the message notifications had unpredictable height, so the confirmations would always appear in different places; top of the stack, bottom of the stack... the bottom of the stack could be any vertical position, too. It was weird and ugly, and behaved poorly.

The solution was to have both asynchronous and synchronous notifications appear in their own exact places, with the synchronous ones at the top right (since their height is always the same!) and the asynchronous ones a bit further down.

There is some interest in having synchronous notifications appear in a totally different part of the screen and asynchronous ones return to the very top right, but hopefully the rationale will help explain that it could be worse :)
(And, personally, I love the consistency it brings. However, I realize the experience there varies, especially depending on how big your screen is).

---

### Post by ubunterooster on 2010-03-30
true, the notification would still be there, but I thought "the real problem is that is a stupid place for it to be" meant you still wanted it moved.

[btw, I've yet to have a problem because of DOING an upgrade]

---

### Post by ranch hand on 2010-03-31
> **ubunterooster said:**
> true, the notification would still be there, but I thought "the real problem is that is a stupid place for it to be" meant you still wanted it moved.

[btw, I've yet to have a problem because of DOING an upgrade]
Well I was kind of relieved that something broke.  9.10-testing was a lot more FUN.  Any update may have left you down for, in one case for me, 10 days.

10.04 has been boring by comparison.  There is, again, some conflict with boxes with ATI graphics (I think).  The two that are inoperable right now are fairly similar to my "main" 10.04 install.  Both are from clean installs, one is a lot older than the other.  I do amm update/upgrade stuff in chroot from my main and then go check.  That way boinc can keep running as much as possible.  Due to that I can continue to easily update them until this is cleared.  I suspect that it will be soon.

This is not the first time that folks have had update problems this cycle and will probably not  be the last.  I am just one of the lucky ones this time.

Thanks for all the help, every one.  I will try the ppa but not today.  I am back on my night time main OS (9.04) with boinc running on it.  I can trust this one not to screw up while I sleep.  I will try the ppa on one of my "backup" installs (I have two for triple redundancy) with the time I am saving not having to update all installs.

---

### Post by ranch hand on 2010-03-31
> **Mr. Picklesworth said:**
> Don't let the crazies confuse you :P
There are about 6 posts in this thread from people who think you are talking about a panel applet; that's one of them.


To the first sentence: Naturally. The fix I talk about was just pushed a few hours ago, so when you update (and restart) you will see notify-osd behaving as it should. When you click on a notification, your click will pass straight through so you can interact with whatever is beneath it. The idea is to be simple, helpful and unobtrusive; like a well-paid butler.
Are you upgrading from Hardy? This functionality has been pretty well the same since 9.04.

The reason for the notification bubble not being flush with the top right of the screen is that there are two kinds of notifications: synchronous confirmations and asynchronous messages. Synchronous notifications appear when you adjust your volume with the keyboard, change screen brightness, press the Eject key, etc. The synchronous notifications are meant to appear immediately no matter what or they won't make sense, so if another notification is showing it could either replace it or be shown alongside it. The decision was taken to show both synchronous and asynchronous notifications side by side. (Note that notification messages are usually queued, shown one by one).

However, it was problematic because the message notifications had unpredictable height, so the confirmations would always appear in different places; top of the stack, bottom of the stack... the bottom of the stack could be any vertical position, too. It was weird and ugly, and behaved poorly.

The solution was to have both asynchronous and synchronous notifications appear in their own exact places, with the synchronous ones at the top right (since their height is always the same!) and the asynchronous ones a bit further down.

There is some interest in having synchronous notifications appear in a totally different part of the screen and asynchronous ones return to the very top right, but hopefully the rationale will help explain that it could be worse :)
(And, personally, I love the consistency it brings. However, I realize the experience there varies, especially depending on how big your screen is).
Thanks for the reason for this.  I do not think it was a problem before but can see how some might.

Personally, I can see no good side to this for how I use my box.  I have plenty of space on my screen.  That the notice ends up that far down the screen is just silly.  It is generated from the upper of two stacked panels as I have both on top.  I have had some new installs where I have not moved the bottom panel and the thing feels like it is half way down the page.

Folks with small screens must love it covering most of their view of the upper right corner of the screen.

I certainly hope that this is not one of the "exciting things we have planned for that part of the screen" (to quote the BIG MAN himself).

Appearantly this can be fixed.  It should be configurable to begin with if they are going to move things like that into your work space.

---

### Post by VMC on 2010-03-31
> **Mr. Picklesworth said:**
> Hi Ranch Hand,

Usually you are able to click through Notify-OSD's notification bubbles. There is a temporary regression, though, which makes that impossible. It will be fixed shortly ;)
(In fact, may have just been).

[https://bugs.launchpad.net/bugs/546650](https://bugs.launchpad.net/bugs/546650)

Edit: Yep, fixed with the latest updates.

This is good news. Since this topic came up, I tried to click through and couldn't, while running Rhythmbox.

---

### Post by cyberkilla on 2010-03-31
Deleted.

---

### Post by ranch hand on 2010-04-11
Well I am glad that the latest updates fixed it as the ppa link packages that I tried did no good, the thing still acts the same as always for me.

The only thig that I have noticed lately is that if you try clicking on the bugger while it is over your boinc screen you can change the settings on boinc, that you can not see, with out effecting the damned pop up notice in the least.

I have found a work around.  Don't listen to music.  I do no like this a bit.  You can't get rid of the thkng or there is no turning  off rhythmbox except with a kill order (force quit applet works).  You can't use rhythbox or the pop ups keep you from using your computer.

This is not an improvement to the desktop.  I love gnome but if they do not find a way that people that actually do things other than entertainment and gossip to be able to use the desktop, I guess there are others.

Lubuntu looks better all the time.

---

### Post by ranch hand on 2010-04-12
I am now back on my main drive in stable OS land for the night.

It sure is nice to have an applet that works.  Nice, short, notices that are tucked up out of the way.  Mouse over the bugger and park the mouse and you have a nice notice of the tune and the time, nicely tucked up out of the way of whatever I am doing.

EDIT

Compare that to the screen shot at the beginning of this thread and explain why that is an improvemant.

---

