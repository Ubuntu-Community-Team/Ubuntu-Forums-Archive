---
title: "Xorg Discussion"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-07-24
Since I am using Karmic, I posted this thread here. The following are the exact contents of a couple of pm's between myself and RAOF. All opinions are welcome, I'm trying to get a better handle on the state of things.

                                                       Quote:
                                                                      Originally Posted by **Regenweald**                                      
                 [I]Hi RAOF,

I decided to send this privately since the topic may well have been done to death in the forums. Basically i'm wondering if the developers are looking towards a replacement for or cleanup of Xorg. Mind you, I am not a dev or anything, I noticed Xorg using about 84 megs of memory in and up to date karmic and i just went googling. I also have no problems or criticism for xorg, my interest is purely educational. 

It seems like Xorg is to ? as Gecko is to Webkit. I came across DirectFB in my wanderings, do you have any thoughts on it ? 

Thanks.[/I]
                                 
Basically, the answer is "no". There is nothing that could possibly replace Xorg at this stage, although there's an X hacker working on a project called ["Wayland"]("http://cgit.freedesktop.org/%7Ekrh/wayland/") that might, one day, be a replacement.

X does an awful lot of things, much more than just display. Among other things, it handles input, access control, and windowing.

Also, X itself is reasonably light; most of the memory usage you'll see from X is other applications storing cached images in X's cache. xrestop can show this - for example, the top two applications there - Monodevelop & Compiz - are together responsible for 60MB worth of X pixmaps.

There is a certain amount of cruft in Xorg, but unless you want to exclude people with old (or undocumented) hardware *and* don't mind breaking old application, that's cruft that pretty much needs to stay. For example, Wayland requires KMS and DRI2; this means that nVidia cards just won't work at all, until the nouveau drivers get up to speed, and will never be supported by the proprietary nVidia driver.

This would have been better off in a thread; feel free to post the contents in one.


------------------------------------------------------------------------------------------------------
In my case, my concern was for the so-called cruft and performance.

@RAOF , i guess later today means in a few mins in my head.

---

### Post by psyke83 on 2009-07-24
Regenweald,

What you are asking for is a monumental task. I suggest you do some basic research on Xorg and its origins (particularly the split from XFree86) before asking these kind of questions.

See:
[http://en.wikipedia.org/wiki/X.Org_Server](http://en.wikipedia.org/wiki/X.Org_Server)
[http://en.wikipedia.org/wiki/XFree86](http://en.wikipedia.org/wiki/XFree86)
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

P.S. Xorg isn't a memory hog because it's using 84MB of ram. That is shared memory for all graphical applications and/or the graphics memory combined. Again, do some research into what the Xorg server is and does.

---

### Post by Regenweald on 2009-07-24
Actually, i do know what Xorg does in terms on managing all input etc. I guess i got put offtrack by detractors claiming that Xorg is archaic and bloated. The so called 'cruft' is in there to allow older hardware and input devices to work and what i percieved to be high memory is most likely due to my compiz usage. I actually remove all the drivers i don't need after an X install through synaptic and just leave nvidia and the input packages, so i have a little idea of what's going on :)

Again remember, not complaining just asking :) Thanks for the links.

---

### Post by psyke83 on 2009-07-24
> **Regenweald said:**
> Actually, i do know what Xorg does in terms on managing all input etc. I guess i got put offtrack by detractors claiming that Xorg is archaic and bloated. The so called 'cruft' is in there to allow older hardware and input devices to work and what i percieved to be high memory is most likely due to my compiz usage. I actually remove all the drivers i don't need after an X install through synaptic and just leave nvidia and the input packages, so i have a little idea of what's going on :)

Again remember, not complaining just asking :) Thanks for the links.

Who said that Xorg was archaic and bloated? Are you sure they were talking about Xorg, or the X11 implementation itself?

Most users and the majority of developers had such opinions of XFree86 (due to the monolithic and convoluted build system, lack of innovation, license changes and various other issues).

Since the fork, Xorg has improved dramatically in comparison to XFree86. Of course there is always room for improvement, but it seems that Xorg development is more active today than it ever was.

---

### Post by Regenweald on 2009-07-24
> **psyke83 said:**
> Who said that Xorg was archaic and bloated? Are you sure they were talking about Xorg, or the X11 implementation itself?

Most users and the majority of developers had such opinions of XFree86 (due to the monolithic and convoluted build system, lack of innovation, license changes and various other issues).

Since the fork, Xorg has improved dramatically in comparison to XFree86. Of course there is always room for improvement, but it seems that Xorg development is more active today than it ever was.

I see the error in my original question now and wil keep track of Xorg development more closely. Since you mentioned it, what are the limitations of the X11 implementation ? I'll google it also.

Edit: wiki is quite comprehensive.

Thanks.

---

