---
title: "Lost volume icon"
date: 2010-02-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Michaelg14 on 2010-02-12
One of the last updates took away my volume control icon that is usually in the top panel.  It is not in the add to panel selection. Anyone know where it went or how to get it back?

Mike

---

### Post by VMC on 2010-02-12
Your right. I didn't notice that until you mentioned it. I've been busy tracking down Plymouth errors.

Not only volume but network also.

---

### Post by x33a on 2010-02-12
It should be available under add to panel. it is usually listed as volume control. if that doesn't work, then take a look here:

[http://ubuntuforums.org/showthread.php?t=1292789](http://ubuntuforums.org/showthread.php?t=1292789)

---

### Post by lrcaballero on 2010-02-12
Click on the top panel, select add to panel, scroll down and select  Notification Area and/or Indicator Applet one of these two should bring it back up for you!!!!!

Good Luck

Luis

---

### Post by VMC on 2010-02-12
> **lrcaballero said:**
> Click on the top panel, select add to panel, scroll down and select  Notification Area and/or Indicator Applet one of these two should bring it back up for you!!!!!

Good Luck

Luis

The Notification Area brought back the network icon, but not the volume control. Also no volume listed under add to panel.

---

### Post by tad1073 on 2010-02-12
[http://ubuntuforums.org/showthread.php?t=1402227](http://ubuntuforums.org/showthread.php?t=1402227)

wrong volume icon, though you meant volume as in drives.

---

### Post by Michaelg14 on 2010-02-13
So far nothing has restored the volume control applet.  Indicator applet brings up a volume icon but it does not respond to my mouse wheel like the original one did.

---

### Post by phillw on 2010-02-13
Yup, gone here, also.

I've added the volume control to panel until it reappears. For the vanishing network one - a little 'work-around' I was told was to log off and then back on again - that always seems to bring it back, but not the volume.

Phill.

---

### Post by SevenMachines on 2010-02-13
yep, volume only gone here, is there a bug open?

---

### Post by SevenMachines on 2010-02-13
there was an update to indicator-sound yesterday for me, i guess thats the one

---

### Post by LKjell on 2010-02-13
It is really bad since I use trayer to show my volume. Already reported.

---

### Post by SevenMachines on 2010-02-13
i'm using system->preferences->sound to fiddle with the volume at the moment. thanks for reporting LKjell!

---

### Post by tad1073 on 2010-02-13
no volume icon for me also...

---

### Post by wilee-nilee on 2010-02-13
alt-f2   gnome-volume-control-applet
Will start it I just put it in the startup applications, because it doesn't restart on reboot.

I just also added the indicator applet from panel add and it has the volume control in it. 

I turned off the autostart and now the volume is in this add on.

---

### Post by code850 on 2010-02-13
Here too, no volume control icon since updates this morning. Volume control is not present in 'add to panel' items.

---

### Post by castrojo on 2010-02-13
Ensure indicator-sound is installed, then log out and back in.

---

### Post by robert shearer on 2010-02-14
> **whiprush said:**
> Ensure indicator-sound is installed, then log out and back in.

nope, no volume icon, tried logging out and back in, tried rebooting, and looked in 'add to panel' no dice.

What was the install of "indicator-sound" meant to do ?.

---

### Post by kklimonda on 2010-02-14
It adds a volume indicator to the indicator applet. So you have to have indicator applet already added to the gnome panel to see it.

---

### Post by zika on 2010-02-14
I have indicator-sound installed. But, if I want to see volume icon in indicator I have to put (manually) gnome-volume-indicator-applet in StartupApp...

---

### Post by phillw on 2010-02-14
> **LKjell said:**
> It is really bad since I use trayer to show my volume. Already reported.

Can you post the bug # I'll pop on an 'affects me', rather than run the risk of raising a duplicate bug.

Thanks,

Phill.

---

### Post by robert shearer on 2010-02-14
> **kklimonda said:**
> It adds a volume indicator to the indicator applet. So you have to have indicator applet already added to the gnome panel to see it.

Ok, got it now!. Thanks for that.:)

As a workaround it is usable. 
Would prefer to not have the indicator applet just to get the volume icon (why have 2 icons for the use of one. Just takes up space.)
The volume no longer works with the mouse wheel so I will wait and see if a future update returns the previous icon and functionality.

---

### Post by phillw on 2010-02-14
> **robert shearer said:**
> Ok, got it now!. Thanks for that.:)

As a workaround it is usable. 
Would prefer to not have the indicator applet just to get the volume icon (why have 2 icons for the use of one. Just takes up space.)
The volume no longer works with the mouse wheel so I will wait and see if a future update returns the previous icon and functionality.

And to think, a couple of months ago, we were chuffed that 10.04 just booted - Something which it still has 'bad' days at  ;)

Phill.

---

### Post by mdurham on 2010-02-14
?

---

### Post by ubername on 2010-02-14
I think Phillw is referring to the fact that a lot of us are having odd problems booting! (There are at least three threads on it)

---

### Post by VMC on 2010-02-14
I just re-installed using the latest current. Volume was there. Since I don't use Empathy/Evolution I removed from panel the "letter" applet. That also removed volume indicator?!

At any rate I added Indicator applet and got back volume.

Why is volume and the Evolution tied at the hip?! Makes no sense.

I guess this is a bug report item. Anyone add a bug report for the missing volume? If not I will add one.

---

### Post by robert shearer on 2010-02-14
> **phillw said:**
> And to think, a couple of months ago, we were chuffed that 10.04 just booted - Something which it still has 'bad' days at  ;)

Phill.

Probably has something to do with snow and coal dust as booting has not been a problem **here** (summer, clean,green New Zealand) ;)


> 
Why is volume and the Evolution tied at the hip?! Makes no sense.

Agreed, I don't use Evolution/empathy either.

---

### Post by castrojo on 2010-02-14
> **VMC said:**
> Why is volume and the Evolution tied at the hip?! Makes no sense.

I guess this is a bug report item. Anyone add a bug report for the missing volume? If not I will add one.

It's like that by design. Instead of applets in a tray you'll have applets in the indicator area.

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

EDIT: It's not tied to the evolution indicator, it just so happens that evolution happens to be the only indicator you're running right now. Try running rhythmbox for another example. Power, bluetooth, and some others will probably land next week so it will make more sense.

---

### Post by Merk42 on 2010-02-14
Well if it's intentional, why no mousewheel support and why is the icon partially blue?

---

### Post by castrojo on 2010-02-14
> **Merk42 said:**
> Well if it's intentional, why no mousewheel support and why is the icon partially blue?

Because you're running Lucid and it's not finished. :)

---

### Post by VMC on 2010-02-14
> **whiprush said:**
> It's like that by design. Instead of applets in a tray you'll have applets in the indicator area.

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

EDIT: It's not tied to the evolution indicator, it just so happens that evolution happens to be the only indicator you're running right now. Try running rhythmbox for another example. Power, bluetooth, and some others will probably land next week so it will make more sense.

Your partially correct. Regarding rhythmbox, it to is part of the indicator applet, but I can quite rhythmbox and it goes away.

 If I remove Evolution/Empathy that "letter" is still there. I say that's a bug, regardless.

---

### Post by castrojo on 2010-02-14
> **VMC said:**
>  If I remove Evolution/Empathy that "letter" is still there. I say that's a bug, regardless.

The messaging indicator is there for any application that needs to leave you a message in some manner, xchat, etc., not just empathy and evolution.

The letter icon is pretty bad, there's a bug about that somewhere; it's not just for mail applications.

---

### Post by tekkidd on 2010-02-14
on the panel right click and select add to panel then choose the volume slider and click add it

---

### Post by mdurham on 2010-02-14
> **tekkidd said:**
> on the panel right click and select add to panel then choose the volume slider and click add it
I don't see any 'volume slider'

---

### Post by VMC on 2010-02-14
> **whiprush said:**
> The messaging indicator is there for any application that needs to leave you a message in some manner, xchat, etc., not just empathy and evolution.

The letter icon is pretty bad, there's a bug about that somewhere; it's not just for mail applications.Aaah. that now makes since. Right now with both Evolution/Empathy removed, or as much as possible, the "letter" shows brown box when pushed.

BTW- I found out the hard way. You can only remove just so much Evolution stuff. Go to far you to also remove gnome, all indicators and are left with just X when you reboot.

> **mdurham said:**
> I don't see any 'volume slider'
There is none, but he's using kubuntu. Maybe they have one.

---

### Post by Mr. Picklesworth on 2010-02-14
> **robert shearer said:**
> Ok, got it now!. Thanks for that.:)

As a workaround it is usable. 
Would prefer to not have the indicator applet just to get the volume icon (why have 2 icons for the use of one. Just takes up space.)
The volume no longer works with the mouse wheel so I will wait and see if a future update returns the previous icon and functionality.

You'll want to hold on to that applet. Applications are gradually being moved to support it; it replaces the old XEmbed-based notification area.

Don't worry, KDE 4 is using the same technology. We aren't alone here ;)

(I do wonder why the same applet doesn't host the old fashioned notification area, though. It would be awesome if that could happen, although I guess it might add some weird complexity to the source code).

Personally, I'm thinking the unified message indicator may be rendered obsolete by all this stuff, since different categories of indicators can be treated differently. (And it's an ugly delta from all the upstreams).
While we're all here, has anyone close to the project tinkered with NOT having that unified message indicator menu but still using the status indicator spec? So, instead of that unified mail icon lighting up Empathy, Evolution and Gwibber produce their own status indicators and do their own things?

---

### Post by castrojo on 2010-02-14
> **VMC said:**
> There is none, but he's using kubuntu. Maybe they have one.

Actually I am glad you brought this up! The indicators are actually an implementation of the KDE KStatusNotifierIcon framework: 

[http://ubuntudevelopers.blip.tv/file/3182018/](http://ubuntudevelopers.blip.tv/file/3182018/)
[http://www.jonobacon.org/2010/02/10/kde-application-indicators-in-gnome/](http://www.jonobacon.org/2010/02/10/kde-application-indicators-in-gnome/)

It also works the other way around, running a GNOME app in KDE does the right thing; so people can mix and match all their apps and the "tray" will work the same.

---

### Post by robert shearer on 2010-02-15
[QUOTE
Don't worry, KDE 4 is using the same technology. We aren't alone here ;)[/QUOTE]

> Actually I am glad you brought this up! The indicators are actually an implementation of the KDE KStatusNotifierIcon framework:
 
Oh:sad::sad:  you mean we will have 'French-fried Fruit-salad with that ?' Happy bouncy icons to let us know we have clicked on something and two clicks for the effect of one ??.

I liked it when Gnome was Gnome and simple..

...No Kangaroos,  no 'two thin ones to balance out the fat one'  and just a Volume control that is just a volume control.

end rant :)

---

### Post by Merk42 on 2010-02-15
> **robert shearer said:**
>  
Oh:sad::sad:  you mean we will have 'French-fried Fruit-salad with that ?' Happy bouncy icons to let us know we have clicked on something and two clicks for the effect of one ??.

I liked it when Gnome was Gnome and simple..

...No Kangaroos,  no 'two thin ones to balance out the fat one'  and just a Volume control that is just a volume control.

end rant :)

No just the notification aspect.

Also, two clicks instead of one? Dolphin does things in one click that takes Nautilus two

---

### Post by robert shearer on 2010-02-15
> **Merk42 said:**
>  Dolphin does things in one click that takes Nautilus two

Yes, I have heard sonographs of dolphins and there is a lot of clicking, though I like Nautilus for their pretty shells :D

I will wait for the final release and anything I post before is mere ramblings and comment - so it would be nice to have the volume applet back with mousewheel control,
 that rare Norwegian Blue Volume applet....sigh:)

---

### Post by uBeer on 2010-02-15
> **robert shearer said:**
> Yes, I have heard sonographs of dolphins and there is a lot of clicking, though I like Nautilus for their pretty shells :D

I will wait for the final release and anything I post before is mere ramblings and comment - so it would be nice to have the volume applet back with mousewheel control,
 that rare Norwegian Blue Volume applet....sigh:)

The icon now is horrible indeed. Why don't they use the old icon without color? That was way better!

---

### Post by VMC on 2010-02-15
Todays latest updates has new indicator applets:
indicator-applet, indicator-applet-session, indicator-sound

Maybe this will help with the missing volume indicator, or at least improve it.

---

### Post by mdurham on 2010-02-15
> **VMC said:**
> Todays latest updates has new indicator applets:
indicator-applet, indicator-applet-session, indicator-sound

Maybe this will help with the missing volume indicator, or at least improve it.
Doesn't seem to have made any improvement for me.

---

### Post by svc985 on 2010-03-12
> **lrcaballero said:**
> Click on the top panel, select add to panel, scroll down and select  Notification Area and/or Indicator Applet one of these two should bring it back up for you!!!!!

Good Luck

Luis

thx... 
this tip(or trick) saved me a lot of time

---

### Post by ybytyruzu on 2010-03-12
Hi, to remove "letter" remove indicator-message.

---

