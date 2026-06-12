---
title: "Newsplash + NewWave"
date: 2008-05-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by analystscouch on 2008-05-15
Hi people,

I've made [a few rough mockups for the Intrepid usplash]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Newsplash"), and I'd be interest in hearing what the wider community think. Please leave your comments here, and/or  at the wiki page.

Also, I want to highlight the great work being done by the [NewWave theme team]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave") (I'm a tester, but don't have the skills for developing) who are designing a great new theme which hopefully will be packaged with Intrepid. Personally, I'd like it to be default. I think we need a really great usplash to integrate with what these people are doing.

Cheers,
Nick

---

### Post by quickshade on 2008-05-16
I like #2 but the loading bar color doesn't match the theme. I suggest chaing it to orange. Other than that it's pretty sweet.

---

### Post by caryb on 2008-05-16
What is it with you guys & your oranges & browns:lolflag:



Cary (Blue KDE user)

---

### Post by MacUntu on 2008-05-16
I think the Ubuntu logo should better be build clockwise.

---

### Post by analystscouch on 2008-05-16
Thanks for your input people, I've now added clockwise and orange progress bar variations!

Also, I was wondering if anyone reading this has any experience making *real* usplashes and might like to develop one of these ideas?

---

### Post by smartboyathome on 2008-05-16
By the way, I think the logo should be more "glossy" like the tango-ified ubuntu logo. Just my opinion. :)

---

### Post by geokok1981 on 2008-05-16
Sorry to be off topic but how can I install the newwave engine in hardy?
I already applied the theme and looks great. 
What will the engine offer more and how to activate it (and roll back to normal hardy if I wish to???)

On topic: The usplash looks good...however:

1. Try a bit glossier look as said before (maybe some reflection on the bottom, think elisa interface for example).

2. I personally like the ubuntu logo to be stable and the circular bar 
increasing as an inner circle, but it would feel more normal if it was going clockwise and perhaps better if it had a smooth animation (if possible). 

Other than that, good work mate!

---

### Post by altonbr on 2008-05-16
I find them all too simple and a regression from the current.

All that *really* needs to be worked on is making it bulletproof, so it shows up no matter what monitor or kernel you have.

Start using splashy maybe? I don't know, but the current theme is fine.

---

### Post by analystscouch on 2008-05-16
> I find them all too simple and a regression from the current.

All that *really* needs to be worked on is making it bulletproof, so it shows up no matter what monitor or kernel you have.

Start using splashy maybe? I don't know, but the current theme is fine.

This might seem an odd thing for me to say, since I'm advocating a new usplash, but *even I* actually don't think there's anything terribly wrong with the current usplash! Personally though, I'd prefer something even simpler than the current one, hence my designs. If it turns out that we keep the current one for Intrepid, I think its important that the progress bar changes to whatever is used in the default theme, for consistency. I agree that top priority is to get usplash to be bulletproof, but really thats a separate issue for the usplash dev team, not the the art team.

> Sorry to be off topic but how can I install the newwave engine in hardy?
I already applied the theme and looks great.
What will the engine offer more and how to activate it (and roll back to normal hardy if I wish to???)

I think the engine is at a very early stage and has relatively little benefit for the moment. Personally I'm sticking with testing the theme for the time being. Shortly, the theme/icons/engine etc will be packaged as a .deb for easy install and uninstall.

> 1. Try a bit glossier look as said before (maybe some reflection on the bottom, think elisa interface for example).

2. I personally like the ubuntu logo to be stable and the circular bar
increasing as an inner circle, but it would feel more normal if it was going clockwise and perhaps better if it had a smooth animation (if possible).

Several people have asked for glossiness. I'll produce a new mockup shortly which is glossier! As for animations, and to altonbr's comments about the mockups being too simple, the main reason for that is simply that they are mockups. If anything ever comes of any of this I'd expect the final thing to have a bit more pizazz, gloss and smoother animations. These are just to give you a vague idea of the concept.

---

### Post by exosyst on 2008-05-16
Concept 1, Variation 3.

It looks very good and very clean. Why does it have to be black all the time eh? 

I personally thing it'd be nice if the ubuntu logo faded in complete and then the progress bar started filling left->right in the middle of it.

BIOS->Grub->Mode set correctly for desktop->usplash in white->fade to black->fade to new GDM->fade to desktop, panels reveal from top and bottom or just fade in.

I think something as seamless as that requires a lot more X work to reduce mode switches and GDM would need to be modded as well.

Could be done though and wouldn't that be nice :D

---

### Post by rubicon on 2008-05-17
> **analystscouch said:**
> Thanks for your input people, I've now added clockwise and orange progress bar variations!

Also, I was wondering if anyone reading this has any experience making *real* usplashes and might like to develop one of these ideas?
If under "real usplashes" you mean "usplash themes", then yes, I have experience.

It is not hard to implement one theme for one resolution. However, if you target the theme to wide auditory, you have to add more resolutions (mind widescreens, notebooks, eeepc etc.) with appropriate artwork (it won't be scaled by usplash &#8212; you gotta make all separate variants yourself).

Well, talking about that mockups, good work! It wouldn't be a big problem to implement all that except one thing. Usplash doesn't support transparency now &#8212; you have to draw in **rectangles**. There are some patches and WIP on this (read: not done officially yet), if they make it in Intrepid, that'd be cool! But now 1: it will take time and effort to prepare all artwork in "rectangular" sense and 2: usplash.so for circular boot with some various-res-versions will be about 10 MiB (not so much, but though).

I hope I will find some free time to get on this and render some of your mockups into real usplash theme(s). Feel free to pm me on any questions regarding coding for this.

[COLOR="Silver"]BTW: This is what I've done on leisure time not a long ago (my blog is in Russian but there isn't much to read, just click on pictures and link reads &#1054;&#1088;&#1080;&#1075;&#1080;&#1085;&#1072;&#1083; &#1092;&#1086;&#1085;&#1072; to see original background picture): [http://engored.ya.ru/posts.xml?tag=316614](http://engored.ya.ru/posts.xml?tag=316614)[/COLOR]

---

### Post by nrayever on 2008-05-18
i like the concept 3, it's a real good usplash. sure with some development that could be easily changed. +1

---

### Post by Gina on 2008-05-18
I like Concept 1 Variation 2 - Clockwise with orange progress bar.   I think I prefer the rotating symbol rather than the oscillating bar we have now.

---

### Post by analystscouch on 2008-05-19
Thanks for the comments people. I've had a few offers of help developing them, which is great!

---

### Post by rubicon on 2008-05-20
Did any artist agree to help us with this? Maybe you should cross-post this idea to Art and Design forums?

---

### Post by graymaster on 2008-05-21
Hey, I like concept three, the colour of the orange circle in the middle looks odd, and does not fit with it.

I showed my friends these concepts as well. They both agree that they like variation 4.

I have to say that all of these look really cool, and can not wait until they come with Ubuntu.

---

### Post by smartboyathome on 2008-05-21
I just realised that variation 4 can be done VERY easily with Splashy, you may want to give that a try.

---

### Post by Nirro on 2008-05-22
I like concept 2, variation 1. but the bar should fill-up clockwise.
Concept 1 is just too much IMO.

---

### Post by rubicon on 2008-05-22
> **smartboyathome said:**
> I just realised that variation 4 can be done VERY easily with Splashy, you may want to give that a try.
Definitely! [COLOR="Silver"]Though I'm not talking for myself :P I already promised to try to make theme for usplash.
[/COLOR]
Um. Does anybody know if splashy will be default boot-splash engine in II?

---

### Post by smartboyathome on 2008-05-23
I don't think it will, but it may be for Ibex +1.

---

### Post by rastari on 2008-05-24
concept 1 variation 2

---

### Post by autocrosser on 2008-05-26
I'm all for Concept 3---I like the round orange progress--What if you do the Ubuntu line text below it?

---

### Post by Gina on 2008-05-27
I think the OS name ***should*** appear on the flash screen personally.

---

### Post by rubicon on 2008-05-27
> **Gina said:**
> I think the OS name ***should*** appear on the flash screen personally.
How about not-so-big note > Ubuntu 8.10 «Intrepid Ibex»
Open-source operation system based on Linux kernel
Ubuntu &#8212; Linux for Human Beings!in, like, bottom-right corner?

'cuz I personally don't like huge **UBUNTU** in the center of my screen.

---

