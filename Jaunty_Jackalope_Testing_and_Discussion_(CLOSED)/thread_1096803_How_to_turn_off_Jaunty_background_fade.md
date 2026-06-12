---
title: "How to turn off Jaunty background fade?"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sbergman27 on 2009-03-15
Is there some way to turn off the new background fade effect?

---

### Post by ronacc on 2009-03-15
if you are using compiz there are a couple of settings for "fade" in compizconfig-settings-manager . The full version ,I don't know about simple-ccsm , I never use it .

---

### Post by sbergman27 on 2009-03-15
> **ronacc said:**
> if you are using compiz there are a couple of settings for "fade" in compizconfig-settings-manager.
Thanks for the response. Yes, I did find those. But I don't use compiz. And it is my understanding that this effect is completely independent of compiz.

---

### Post by Yashiro on 2009-03-15
If you mean the transition fade when you switch wallpapers it's a Gnome 2.24-6 feature. Possibly you can disable it using the Gconf Editor.

---

### Post by Mr. Picklesworth on 2009-03-15
No, there does not appear to be an option in gconf. I suggest you file a feature request upstream in [Gnome's Bugzilla]("http://bugzilla.gnome.org/"), if there isn't one already.

---

### Post by sbergman27 on 2009-03-15
> **Mr. Picklesworth said:**
> No, there does not appear to be an option in gconf.
Thanks. Yes, gconf-editor was the first place I looked. Hard to believe anyone would add such an effect without providing any way to turn it off.

BTW, I love your sig. I've been a Unix, and later Linux admin and advocate for over 20 years. I've watched, helplessly, as the old guard has smugly shredded newbies in our forums. The pleasant and constructive attitudes found in the Ubuntu Forums is like a breath of fresh air. Something I've hoped for for many years.

-Steve

---

### Post by ronacc on 2009-03-15
I thought you used to be able to select that in system>preferences>screensaver but its not there now . another cute "improvement" .

---

### Post by gjoellee on 2009-03-15
I would say it is quite cool. This feature has been in Enlightment for a while.

---

### Post by ronacc on 2009-03-15
cool or not it should be a CHOICE .

---

### Post by MacUntu on 2009-03-15
But choice leads to confusion! :-\"

---

### Post by zekopeko on 2009-03-15
> **MacUntu said:**
> But choice leads to confusion! :-\"

to much choice leads to confusion. take compiz-config-settings-manager or cairo-dock settings.

those things are eating usability for breakfast.

---

### Post by zekopeko on 2009-03-15
> **ronacc said:**
> cool or not it should be a CHOICE .

no it shouldn't. and why does it bother you so much? rotating wallpapers perhaps?

---

### Post by ronacc on 2009-03-15
You don't like ccsm ? use simple-ccsm or abandon compiz for metacity compositing , you have a choice , you don't like the "confusion" of cairo dock ? use AWN or dockey , you have a choice . My default position is always choice , if something confuses me I have a choice , learn the intricacies or don't use it .

---

### Post by MacUntu on 2009-03-15
> **zekopeko said:**
> to much choice leads to confusion. take compiz-config-settings-manager or cairo-dock settings.

those things are eating usability for breakfast.

Usability is not about the number of knobs but how you present them. CCSM is a good example of how not to present them.

---

### Post by Yashiro on 2009-03-15
If CCSM is bad, that makes KDE a catastrophe, right?

---

### Post by kurros on 2009-03-15
Unfortunately the only way to disable the nautilus wallpaper fade effect is to disable *all* GTK+ animations.

Add 
```
gtk-enable-animations = 0
```to ~/.gtkrc-2.0 (create if it doesn't exist). For all users it would be /etc/gtk-2.0/gtkrc IIRC.

And then logout or pkill nautilus.

I don't like this solution, as I'd still rather have other GTK+ animations. But I had to stop using my wallpaper clock screenlet since the fade every 60 seconds was too distracting.

---

### Post by andrewabc on 2009-03-15
> **MacUntu said:**
> Usability is not about the number of knobs but how you present them. CCSM is a good example of how not to present them.

No, it is a good way. It has options listed for everything. If you want to change something, you can easily do so. If you don't want to change settings, then don't use it. If you only want to change a couple settings, I don't see why everyone else should be punished and use simple ccsm instead.

No option for countdown timer when shutting down, no options for notification popups. Someone had to program that stuff, why not offer options so users can customize? No one is forced to use customizations.

---

### Post by MacUntu on 2009-03-15
> **andrewabc said:**
> No, it is a good way. It has options listed for everything. If you want to change something, you can easily do so. If you don't want to change settings, then don't use it. If you only want to change a couple settings, I don't see why everyone else should be punished and use simple ccsm instead.

You misunderstood me. I'm not saying many optins are bad. I'm saying that presenting many options in a non-optimal way is bad. Some Gnome devs make this into "many options are bad". :(

---

### Post by KrazyPenguin on 2009-03-15
I can see having these things enabled by default for new users.

But too many of them leads to system inefficiency, since many of these toys are system hogs.

For Example: I am more productive using metacity. I find it more quicker and responsive, and my computer as a whole remains that way while I use it.

I would like to see a tool that would make it easier to customize Ubuntu, and I feel Ubuntu Tweak isnt bad.  At least it is categorized with instructions.

---

### Post by rfruth on 2009-03-15
I took care of the fade 'feature' (and others) by using an older version :P

---

### Post by ronacc on 2009-03-15
> **MacUntu said:**
> You misunderstood me. I'm not saying many optins are bad. I'm saying that presenting many options in a non-optimal way is bad. Some Gnome devs make this into "many options are bad". :(

and who decides what is optimal , it is a mater of opinion , I think CCSM is laid out about a logicaly as anything that complex can be , the options are laid out as to the area they affect , you check an option to enable it or click the option to see sub options , to me it is much plainer than gconf .

---

### Post by Darkshade on 2009-03-15
Nothing to do with the topic, but I really don't see what you guys don't like about CCSM. I think everything is pretty well organized and there are options to customize pretty much everything. You have the choice to do it or not. If you want you can set up every single detail, but you don't -have- to do it - you can just check or uncheck plugins and use them with the default configuration which is pleasant enough to most people.

---

### Post by zekopeko on 2009-03-15
> **ronacc said:**
> You don't like ccsm ? use simple-ccsm or abandon compiz for metacity compositing , you have a choice , you don't like the "confusion" of cairo dock ? use AWN or dockey , you have a choice . My default position is always choice , if something confuses me I have a choice , learn the intricacies or don't use it .

> **MacUntu said:**
> Usability is not about the number of knobs but how you present them. CCSM is a good example of how not to present them.
> **MacUntu said:**
> You misunderstood me. I'm not saying many optins are bad. I'm saying that presenting many options in a non-optimal way is bad. Some Gnome devs make this into "many options are bad". :(

many options are bad for 90% of the people. it's the paradox of choice. too many and you will probably choose sub-optimal, too little and you can't achieve what you want. things need to be balanced.
and i do agree that presentation of options is probably the most important part. Sane defaults are the ones that should be changed graphically. The rest should go to some config file or gconf.

> **rfruth said:**
> I took care of the fade 'feature' (and others) by using an older version :P

rfruth could you tell me what exactly bothers you with the fade effect?

if it's apps hogging resources the fade effect is probably just triggered on your action. it's not like it's a daemon in the backgrounds going: "Did somebody change the wallpaper? Should i fade?" every 30 ms.  


> **Yashiro said:**
> If CCSM is bad, that makes KDE a catastrophe, right?

Might explain why i don't like using KDE ;). Just feels (too) busy.

---

### Post by andrewsomething on 2009-03-15
> **ronacc said:**
> and who decides what is optimal , it is a mater of opinion , I think CCSM is laid out about a logicaly as anything that complex can be , the options are laid out as to the area they affect , you check an option to enable it or click the option to see sub options , to me it is much plainer than gconf .

The main problem with CCSM and Compiz plugins in general is that so many have overlapping functionality. 

I know I'm not the only person who, when trying to turn off snapping windows, was quite confused to find that the snapping windows plugin wasn't activated. There is also window snapping controlled by the wobbly windows plugin.

---

### Post by ronacc on 2009-03-15
I haven't run into that one , ofcourse the very first thing I do when I install ccsm is getrid of wobbly windows , I detest that one so much that I wouldn't use compiz if it could not be disabled , like I said above it is a matter of taste :)

---

### Post by markoid8 on 2009-04-14
So I have noticed the same thing. It is a problem because I use wallpapertray to change backgrounds frequently, and the fade uses too much of my CPU. So how exactly did you disable it without turning everything off?

---

