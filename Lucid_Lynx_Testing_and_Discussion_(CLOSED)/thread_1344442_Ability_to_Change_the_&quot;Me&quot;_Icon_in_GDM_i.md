---
title: "Ability to Change the &quot;Me&quot; Icon in GDM is Hidden"
date: 2009-12-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ellipsis on 2009-12-02
I have been a full time Ubuntu user since Feisty and yesterday I discovered something absolutely amazing: you can change the "Me" Icon in GDM through "About Me." I was shocked, amazed and utterly stupefied by my own ignorance. You see ever since the mock up/beta themes for karmic I always thought: "If only Ubuntu would allow you to have cool customizable icons there instead of just that human silhouette it would look so much better." Yet, no one in any review, screen shot etc. ever bothered to change it from the default. Perhaps it was just laziness or comfort in going with the default but maybe, these reviewers were also ignorant of this ability. 

This can be understood because as was my case one of the first things I do (normally) when installing Ubuntu is set it up to login automatically. Moreover, I rarely/never use "About Me" since it is a fairly useless application for me at the moment. 

I thus came up with a brainstorm idea to make this functionality more visible:

[http://brainstorm.ubuntu.com/idea/22764/](http://brainstorm.ubuntu.com/idea/22764/)

Any other ideas? Is it good as it is? Should "About Me" be cleaned up to showcase this ability more clearly?

---

### Post by wojox on 2009-12-02
Cool I didn't know that either. I agree, it should be mentioned in the Help and Support application.

---

### Post by Merk42 on 2009-12-02
Yea the only reason I even thought to look was the GDM for Karmic.

Definitely needs to be more discoverable.

---

### Post by hugmenot on 2009-12-03
The file is called ».face« in your home directory (note the dot).

---

### Post by ubername on 2009-12-04
During one of the Karmic beta updates my GDM image changed to this

this is called .face.icon in ~/

I have a separate picture which is just called .face which appears in 'about me'. Testing this on other users it appears that the GDM logon screen looks first for a .face.icon, and them uses .face if it can't find one. I have no idea why this might be useful however.

---

### Post by Ellipsis on 2009-12-06
The idea on Brainstorm has (finally) been approved. Please vote and add more solutions.

---

### Post by Hiram on 2009-12-06
I think that the about me app should be more present.. It is a great way to fill in all of the users details in one place. especially now with empathy. Why is there this app and the details dialog from empathy? that dialog also misses a webcam picture feature and if I change my picture there why shouldnt my account picture change? I would prefer if the empathy dialog actualy started about me and that about me becomes more usable..

---

### Post by mathfeel on 2010-04-27
Didn't work for me.
I wanted to test what gnome-about-me do. So I removed ~/.face and ~/.face.icon, ran gnome-about-me, set the face.

It created a new ~/.face, but when I logout, the face browser of the login screen shows a generic grey man icon.

---

