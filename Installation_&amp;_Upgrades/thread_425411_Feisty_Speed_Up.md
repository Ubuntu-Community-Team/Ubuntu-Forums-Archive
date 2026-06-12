---
title: "Feisty Speed Up"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by GaryH on 2007-04-27
Hi Everybody,
I''m not complaining about Feisty as you can see from my recent, glowing T20 Feisty Great Success Story thread but I would like to speed the GUI up a bit. I'm running a generic kernel and Gnome. Is there another kernel (686 maybe?) which would speed things up enough to noticeably improve the performance of the following:
[LIST]
[*]Window dragging and resizing response time.
[*]Mouse click response time.
[*]keyboard response time in graphic applications.
[/LIST]
I've heard Gnome has a lot of code to chug through due to *excessive * eye candy so wouldn't a faster kernel permit iit respond to events faster? Anyway, that's what my simple minded, qualitative logic begs me to ask.
Thanks for the help everybody!
Peace,
GaryH

---

### Post by LuisGMarine on 2007-04-27
I don't know how much this might help, but you said mouse click response time, you can go ahead and try messing around with some of the settings under System > Preferences > Mouse and there is an option there to set the response time.

For general speeding up of your Ubuntu-Box , as they like to call it, visit this link here [http://ubuntuforums.org/showthread.php?t=189192]("http://ubuntuforums.org/showthread.php?t=189192") it might help you out to get started to making your system faster.

---

### Post by GaryH on 2007-04-28
Thanks for the link LuisGMarine.

---

### Post by GaryH on 2007-04-28
This one is for everybody who wants Feisty to run faster. 

I've spent the better part of day having fun experimenting with the excellent *speedup* suggestions posted on the following two web sites:
[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)
[*][http://www.chinwong.com/index.php/site/comments/ubuntu_speed_up_tips/](http://www.chinwong.com/index.php/site/comments/ubuntu_speed_up_tips/)
[/LIST]
My findings for the suggestions offered on  URL 1 above follow:
[LIST=1]
[*]InitNG - Bootup time, which is what this fix improves,  isn't a concern of mine. The fix isn't worth the risk to my system. 

[*]Speed up Firefox - Easy fix. Slight if any improvement was noticed.

[*]Custom compile a new kernel - Non-trival fix. I will do further investigation to see how much it will speed up Gnome performance before undertaking.

[*]Make sure DMA is on - Easy to check and DMA is on.

[*]Use Prelink... - N/A because prelink isn't necessary with Feisty

[*]Pick the kernel... - It appears that the kernel needed for the T20's PIII, 686, doesn't exist. I will do further investigation to see what's going on.

[*]Disable un-needed services... - Excellent article about reducing bootup time. Since bootup doesn't bother me, this fix wasn't tried.

[*]Use Swiftfox - I keep getting a *try again later message* when trying to install Swiftfox with Automatix. I will pursue this problem.

[*]Tweak your ext3/reisers - Not worth the risk to my system because of, albeit rare, potential disk crash data loss, reboot problems, and compiler problems.

[*]Clean up unnecessary... - This is a very well written article about how to find and delete unnecessary files which I followed to the letter; nothing to do with speed up but a good practice none the less.

[*]XML Opt... The before and after speed measurement improvement is pretty small so I didn't try this one.

[*]Install preload - This is an easy fix. Signs of a speed up aren't yet apparent..
[/LIST]

My findings for the suggestions offered on URL 2 follow:
[LIST=1]
[*]I followed tips 1, 2, 3, 4, and 8 and noticed great startup time improvement on OpenOffice.org Word Processor but the overall performance of Gnome remains unchanged. The speed improvement to OpenOffice.org Word Processor is not without, albeit slight, functional sacrifice. 
[/LIST]
My next steps are to:
[LIST=1]
[*]Install Swiftfox
[*]Research using a 686 Feisty kernel
[*]See if there is a faster graphics driver for the savage chip set
[/LIST]
Hope this helps Feisty users everywhere.
Peace,
GaryH

---

### Post by lenooh on 2007-05-04
do you want to use gnome? why not try other DE or WM?

if you want speed, i think there is nothing faster than PWM1 ([http://modeemi.fi/~tuomov/ion/pwm.html](http://modeemi.fi/~tuomov/ion/pwm.html))

---

### Post by GaryH on 2007-05-04
Hi lenooh,

In your experience how much time is required to get PWM running smoothly. Hours, days, weeks?

Thanks for the advice.

Peace,
GaryH

---

### Post by fede on 2007-05-06
Hello,

[COLOR="Red"][This article has been very useful to me.]("http://www.xsol.se/index.php?content=guide_feisty")[/COLOR]

Especially the part regarding vm.swappiness. (I set it to 5)

A second thing is [COLOR="Red"][changing ext3 to data_writeback as explained here]("http://ubuntuforums.org/showthread.php?t=107856&highlight=tweak+filesystem")[/COLOR]. In my experience it has always worked fine and I've noticed (subjectively) a good speed boost.

The next thing I think is compile a kernel. I haven't done it yet since I'm on feisty, but on previous versions it helped a lot.

A third thing that helped me a lot is installing my system as described in "a faster kde" by aysiu, at [COLOR="Red"][http://www.psychocats.net/ubuntu/kde-core]("http://www.psychocats.net/ubuntu/kde-core")[/COLOR]
I think it runs quite faster than kubuntu, after installing everything I need.

The only thing I like more about GNOME is that it looks very pretty; kde can be (in my experience) a great lot faster than gnome. In my machine, nautilus takes a couple of seconds to display a directory; it's almost instant in kde, and it IS instant in windows. Metacity seems to really bog down my system, just moving a window around (frantically) sends cpu usage to 100%. Also, I like kde because some apps are a must to me, especially kontact over evolution and k3b over any other recording program. 

I don't mean this as a KDE vs Gnome rant, it's just my personal experience regarding system speed.

---

### Post by GaryH on 2007-05-06
Thanks for the tips fede. You're right about Nautilus, it's a real tortoise. I'll check out your recommendations and publish my findings.

1. Concurrency bootup speed up fix. Before/After  80/65 Sec. Bootup measured from Grub countdown down done to appearence of Gnome cursor. Duplications of a few bootup log messages were observed with CONCURRENCY=shell.

Peace,
GaryH

---

### Post by galileon on 2007-05-22
hi, from your three symptoms, i think of missing graphics acceleration...

do you have an nvidia or ati card? are u using the opensource or the official binary driver?

i always have these problems with mu nvidia geforce6500, when i dont use the proprietary driver...but i know, its maddening that i have to taint my system with such filth!

just a thought...

---

