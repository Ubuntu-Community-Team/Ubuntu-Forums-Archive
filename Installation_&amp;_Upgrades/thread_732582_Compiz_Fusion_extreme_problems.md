---
title: "Compiz Fusion extreme problems"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by Bubbliciousmax on 2008-03-23
I hope I'm not imposing on you guys for typing so much 8-[


I've have Ubuntu for a few months. The first thing I did after I installed it was installed Compiz and it worked beautifully. But for the past few days it hasn't been working. When I say 'hasn't been working' I mean that everything was running horribly. Even all the 2D graphics were lagging, like scrolling, minimizing, etc.

So I thought it was a problem with my graphics card (ATI Radeon x1650 pro). So I uninstalled and then reinstalled the drivers it said it required, but still to no avail. So at that point I thought "well Ubuntu is a pretty nifty fella, so it should have some kind of tool to correct this problem" and then I scoured the system looking for my imagined tool. Finally after what seemed like an eternity I found The Screens and Graphics tool, but that didn't do anything (more on this later though).

It seemed like everything I tried had no effect so I went down to the hardware level, and tried the graphics card on the motherboard. When I'd turn it on it'd (plugged into the MB) go to the loading ubuntu screen and after that would remain black. 

However it would prompt me saying that I was in "low graphics mode" and say that I could continue, configure, or cancel I think. 

   
So I'd go into the configure thing and it'd take me to the Screens and Graphics menu (from the System>Admin> Screens and Graphics). Since I had it plugged into the motherboard graphic card the resolution was 800 by 600 I think, but here's the thing: my screen is 1280 by 1024. I thought this was kind of strange.

So I'd fix it from the drop down menu and then continue to the graphics tab. In that tab there is two Graphics card selection thingys. I say thingys cuz I have no idea what purpose they serve. At first I didn't know what the purpose of them were because I'm not necessarily tech savy, and they both said the exact same thing.
They said:

**Graphics Card (VESA driver (generic))**
Driver:             [[vesa - Generic VESA-compliant video cards]]
Video Memory:  [[[COLOR="Gray"]Automatic[/COLOR]]] 

The [[ ]] represents a drop down menu.
The gray means it's not clickable.

So I'd go to the list and pick my graphic card's general driver and then click the ok button. 

Somewhere in between turning my screen into an over sized freak of nature, making it so all I saw was fuzzy pixil pillars, a glowing black screen (if that makes any sense), and making it so I saw my scream repeat infinitely to either side of my monitor in a space that was about two inches wide, I decided to just take the damn program, and everything that even mentioned compiz off of my computer.

But apparently, this I didn't know, was that in order for me to completely remove it was to remove it from the terminal, synaptic package manager, and manually delete files. And even this failed to completely remove everything.

But at the time I was just like "Whatever, I'm just going to reinstall it and it'll be over written."
But no, no I was wroooong...at first I guess.

I installed compiz probably 40 different times, after restarting my computer as many times, if not more. I tried about 20 different methods that I found online and then I found one that really seemed to do what it promised. (I would insert it here, but I guess that my mouse has lost the ability of cut and paste, but it was the "**How-To: Install Compiz Fusion From GIT**" on the Ubuntu Forums.)

So I tried it once, and I seemed to get results, though certain things required a bit of overzealous persistence.
So about 10 more attempts at installing it, I restart my computer, it loads, I log in, and the desktop begins to load, and then white.

White?

I thought that I had discovered the Ubuntu version of the Window's Blue Screen of Death.
So I begin to frantically click here and there, then all of the sudden, a twitch! 

I move my mouse more, and I decide, what the hell? and press Ctrl+Alt and move my mouse.

THE CUBE! I flip out and just get so excited because I figured I got the multi-desktop cube running. It's a completely albino, blindingly white, cube, but the compiz cube none the less. 
 
So I figure that I'm getting onto something. I restart my computer, hoping that it'll fix it's self. But no such luck.

So after a while of that I try to get my old desktop back to see if I can do something.
So I restart my computer, and try to figure out what I can do from the log in menu.

So I go to the Sessions thing. I was a bit scared that I'd terminally destroy something in my computer because I had never even noticed it before. But I run the session in the terminal and I find I'm able to pull up firefox and so I bring the site that I used to reinstall the Compiz program, because there was also a section included to uninstall it.



Much to my despair I uninstall it, throwing all I had accomplished away. I exit and log in normally, no problems, just no compiz, and it still doesn't see my graphics card.

But then I try to reinstall it again, and I think I typed something incorrect to the terminal because after I hit Enter, all the windows have no borders, no minimize, maximize, or close buttons, and I can't move them because they have no bar at the top. 


And that it was I have been through on my own without knowing a single thing about virtually anything.


However I have determined that My computer is not seeing my graphics card, even though the monitor is plugged directly into it. It seems that none of the drivers I tried to get to work, work. I don't really know what caused it either because it worked perfectly fine until I logged in a few days ago. Before then I hadn't logged in for a few weeks.


I want to get compiz to work because it was really nice having extra desktops.


ANY help is greatly appreciated =D <3

---

### Post by Bubbliciousmax on 2008-03-23
Oh god, did I post this in the right Forum?:confused:

---

### Post by forestpixie on 2008-03-23
Yes it's a good enough start - but you'll need to wait for someone with enough patience to read the thread all the way through to decipher 

a - if there's actually a problem, or it's just a moan
b - whether they can help, not everyone can help with everything
c - what you've done to help yourself

You might be well served by posting actually what you need help with and what information you can give without the storyline.

Edit - and bumping  a thread after 30 mins is not the way to go about it.

---

### Post by forestpixie on 2008-03-23
some things you can try - not had a lot to do with ati cards -
restricted driver manager
or [envy]("http://albertomilone.com/nvidia_scripts1.html")

---

