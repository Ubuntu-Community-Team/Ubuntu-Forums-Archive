---
title: "Pidgin 2.5.0 Released :)"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2008-08-19
Hello,

I'm so glad 2.5.0 has been released, when will it make its way into Intrepid's Repositories?

Lee

---

### Post by eldragon on 2008-08-19
considering there hasnt been a feature freeze, and ive been able to compile and run it with no tweaking at all (in hardy), i guess it will make it into the repos.

---

### Post by aamukahvi on 2008-08-19
Nice, there's lots of improvements on the MSN side.

---

### Post by gladstone on 2008-08-24
Would it be better to install it from [GetDeb](http://www.getdeb.net/release/3099) or somehow in the [Intrepid](http://packages.ubuntu.com/intrepid/pidgin) package lists? Could I update via apt-get?

---

### Post by klange on 2008-08-24
> **gladstone said:**
> Would it be better to install it from [GetDeb](http://www.getdeb.net/release/3099) or somehow in the [Intrepid](http://packages.ubuntu.com/intrepid/pidgin) package lists? Could I update via apt-get?

? If you're on Intrepid (and assuming your package source isn't a week old), you can just update + upgrade and you should get Pidgin 2.5.0.

---

### Post by gladstone on 2008-08-25
> **WindowsSucks said:**
> ? If you're on Intrepid (and assuming your package source isn't a week old), you can just update + upgrade and you should get Pidgin 2.5.0.

Sorry, should have mentioned that I'm using Hardy ;)

---

### Post by Manosdoc on 2008-08-25
It's already in Intrepid !:)

---

### Post by volanin on 2008-08-25
A little offtopic, but both pidgin 2.4.X and now 2.5.0 have problems saving my IM window position. Does anybody has this as well?

I have my buddy list at the left side of the desktop, and my IM window at the right side of the desktop. But if I close the IM window and reopen it by double-clicking any buddy, it appears adjacent to the buddy list, and not in the previous position in the right side.

This started happening since in hardy.
:(

---

### Post by durand on 2008-08-25
> **volanin said:**
> A little offtopic, but both pidgin 2.4.X and now 2.5.0 have problems saving my IM window position. Does anybody has this as well?

I have my buddy list at the left side of the desktop, and my IM window at the right side of the desktop. But if I close the IM window and reopen it by double-clicking any buddy, it appears adjacent to the buddy list, and not in the previous position in the right side.

This started happening since in hardy.
:(

Happens here as well but I don't really notice..

Yay for custom smileys! Now people can see our awesome pidgin smileys :) Though we still don't have full speed transfers :( I think that will come soonish with the msn-pecan project.

---

### Post by gladstone on 2008-08-25
> **Manosdoc said:**
> It's already in Intrepid !:)

So... guys :) I'm sticking with Hardy, but what is the best way to install Pidgin 2.5.0?

---

### Post by Zlatan on 2008-08-25
> **gladstone said:**
> So... guys :) I'm sticking with Hardy, but what is the best way to install Pidgin 2.5.0?

i think it should be to ge .deb file and then install

---

### Post by gladstone on 2008-08-25
Cool, I've just installed from [GetDeb](http://www.getdeb.net/release/3099) and all seems well (thank-god for MSNP15!!).

Would be nicer if I could install via apt-get using the [Intrepid](http://packages.ubuntu.com/intrepid/pidgin) package lists, but bring on October!

---

### Post by khc on 2008-08-25
> **volanin said:**
> A little offtopic, but both pidgin 2.4.X and now 2.5.0 have problems saving my IM window position. Does anybody has this as well?

I have my buddy list at the left side of the desktop, and my IM window at the right side of the desktop. But if I close the IM window and reopen it by double-clicking any buddy, it appears adjacent to the buddy list, and not in the previous position in the right side.

This started happening since in hardy.
:(

This is intentional. It's done that way so your window manager can actually, eh, manage your windows.

---

### Post by BwackNinja on 2008-08-25
> **khc said:**
> This is intentional. It's done that way so your window manager can actually, eh, manage your windows.

It is actually pretty useful, if someone sends you a message, the window will appear in the least obtrusive place possible.

---

### Post by psic on 2008-08-25
Nice to see. I've just recently installed the latest Ubuntu on an older-ish desktop, its prime function is web surfing and IM. Imagine my surprise when the installed version of Pidgin is buggy and crash-prone.

After some reading around on this forum, it seems that version 2.4.1 (I think - the one included in Hardy) has memory leak problems, which both top and free seem to agree with.

I'll try out this version now, plan on getting the .debs from getdeb.net. Any comments are welcome, and I'll update here in any case :)

ps. oh, my first post on these forums :)

---

### Post by volanin on 2008-08-25
> **BwackNinja said:**
> It is actually pretty useful, if someone sends you a message, the window will appear in the least obtrusive place possible.

Ok, I don't like the behaviour, but that's quite a good point.
The last problem that I have (in 2.4.X and 2.5.0) is:

I have the habit of sending the IM and closing the window with ESC.
This makes the history logs totally fragmented.
But there is an option to fix that:

Untick **CLOSE IMs IMMEDIATELLY WHEN TAB IS CLOSED**.

The IM window is closed, but the whole conversation stays "on" in the background. This has the added benefit that the conversation does not clear from the IM window until I close Pidgin. But... whenever I am talking to my buddies, after some minutes (variable), the IM window ALWAYS crashes and closes the conversation. It is annoying as hell.
:(

---

### Post by psic on 2008-08-25
> **volanin said:**
> 
The last problem that I have (in 2.4.X and 2.5.0) is:

I have the habit of sending the IM and closing the window with ESC.
This makes the history logs totally fragmented.
But there is an option to fix that:

Untick **CLOSE IMs IMMEDIATELLY WHEN TAB IS CLOSED**.

The IM window is closed, but the whole conversation stays "on" in the background. This has the added benefit that the conversation does not clear from the IM window until I close Pidgin. But... whenever I am talking to my buddies, after some minutes (variable), the IM window ALWAYS crashes and closes the conversation. It is annoying as hell.
:(

Just wondering, do you have this problem because of the 'Close IMs Immediatelly when tab closed' setting? Or general Pidgin crashing?

---

### Post by volanin on 2008-08-26
> **psic said:**
> Just wondering, do you have this problem because of the 'Close IMs Immediatelly when tab closed' setting? Or general Pidgin crashing?

Pidgin buddy list never crashes.
Just its IM window, that suddenly closes mid-conversation and loses all history, so it REALLY seems like a crash... but I can reopen it by double clicking the contact in the buddy list (and then asking to my buddy: "what was your last message again?")

It just happens when I have 'Close IMs Immediatelly when tab closed' unchecked.

As I said, I close the IM window all the time. And if the options is checked, Pidgin also closes the conversation and flushes the history to disk, so it might reset something, and never trigger the bug at all...

But with the option unchecked, even when I close the IM window, the conversation is still "on" in the background, and is fully restored when the IM window is opened again... so... even when closing the IM window all the time as I do, the conversation goes on unclosed for a long time... triggering something that might crash it.

Sometimes it takes 5 minutes, sometimes 30... but it ALWAYS crashes.
And Pidgin buddy list keeps running as normal.

Was I clear?
:)

---

### Post by durand on 2008-08-26
Strange, I've never had this problem. For me, when pidgin crashes, it's because of pulseaudio messing up.

volanin, couldn't you put pidgin on a separate desktop and leave the windows open all the time?

---

### Post by zerwas on 2008-08-26
Users of Ubuntu 8.04 should use the PPA of the Pidgin developers: [https://launchpad.net/~pidgin-developers/+archive](https://launchpad.net/~pidgin-developers/+archive)

Have fun.

---

### Post by merlyn on 2008-08-27
> **gladstone said:**
> So... guys :) I'm sticking with Hardy, but what is the best way to install Pidgin 2.5.0?

Grab the .debs from [here]("http://www.getdeb.net/search.php?keywords=pidgin").

Cheers.

**Edit:** Whoops, I ought to have read the entire thread. Aren't I an Idiot?

---

### Post by gladstone on 2008-08-27
> **zerwas said:**
> Users of Ubuntu 8.04 should use the PPA of the Pidgin developers: [https://launchpad.net/~pidgin-developers/+archive](https://launchpad.net/~pidgin-developers/+archive)

Have fun.

Cheers for that!!

---

