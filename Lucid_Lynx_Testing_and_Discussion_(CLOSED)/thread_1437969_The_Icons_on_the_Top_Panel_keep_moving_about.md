---
title: "The Icons on the Top Panel keep moving about"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by StuM on 2010-03-24
As the title suggests, some of the icons (unsure what the correct terminology for these are) on the top panel keep reordering themselves of their own accord.  In particular the date/time, wifi and shutdown ones.  Seemingly positioning themselves in a totally random order.  Example attached.

Worse still sometimes the shutdown one disappears completely.  Fortunately I have Gnome Do installed so I shut down via that.  Has anyone else encountered this?

---

### Post by Rob2687 on 2010-03-24
Yeah...what's the deal with that? It's always behaved like that (not just in Lucid). 

Even when the applets are locked the order may stay the same but the position of the applets will move seemingly randomly.

Pretty annoying.

---

### Post by StuM on 2010-03-24
Ah Applets! I was wondering what they were called. :D

---

### Post by linux4me on 2010-03-24
That's really bizarre! Mine don't move, but at one point I had two sound icons instead of a network icon and a sound icon in the indicator applet.

@Stum: Do the applets move regardless of the theme you use or the video driver you are using?

---

### Post by kaldor on 2010-03-24
In Hardy and Intrepid, they used to move about just like that every time I logged in. It drove me MAD, especially when other people needed my computer for something. They'd be like "what the f*** is this crappy layout" etc. I'd have to explain "oh, linux sometimes does that" only to get "well linux sucks then" as a return. 

Little things like this can put many people off.

---

### Post by linux4me on 2010-03-24
I've been using Ubuntu since Dapper, and that's never happened to me. Do you guys have "lock to panel" selected for the icons in the applet?

---

### Post by StuM on 2010-03-24
> **linux4me said:**
> @Stum: Do the applets move regardless of the theme you use or the video driver you are using?

I haven't tried other themes, or altering the video driver as of yet.  But I've just changed my theme and will try that out for a while.  The problem is that it doesn't happen that often... just out of the blue they'll have a little move around.

> **kaldor said:**
> In Hardy and Intrepid, they used to move about just like that every time I logged in. It drove me MAD...

That's interesting.  Along with Rob2687, it appears this isn't exclusive to Lucid. 

> **kaldor said:**
> ...Little things like this can put many people off.

Very true.

> **linux4me said:**
> I've been using Ubuntu since Dapper, and that's never happened to me. Do you guys have "lock to panel" selected for the icons in the applet?

Yep all the icons have 'lock to panel' ticked... The only one I don't know how to check is the wireless one, when I (right) click on that it doesn't display the lock to panel option.

---

### Post by linux4me on 2010-03-24
Well, keep us posted, this is interesting. I have always used Nvidia graphics with the exception of my laptop which has integrated Intel graphics, if that helps any. I don't know if the graphics could explain it or not...

---

### Post by kaldor on 2010-03-24
Yes, it was locked. 

It happened on Ubuntu, Mint, Fedora on 3 different computers.

---

### Post by Mr. Picklesworth on 2010-03-24
This is a known bug that occurs with right-aligned applets when you change screen resolution mid-session. Especially popular when running in VMs. (It's also why I am so very thrilled about the idea of forgetting gnome-shell completely in Gnome 3).

There's a bug report somewhere, and come to think of it a fix was meant to be comitted upstream just recently. I'll see if I can find it for you...


Edit:
[https://bugs.launchpad.net/bugs/44082](https://bugs.launchpad.net/bugs/44082) :)

---

### Post by kaldor on 2010-03-24
> **Mr. Picklesworth said:**
> This is a known bug that occurs with right-aligned applets when you change screen resolution mid-session. Especially popular when running in VMs. (It's also why I am so very thrilled about the idea of forgetting gnome-shell completely in Gnome 3).

There's a bug report somewhere, and come to think of it a fix was meant to be comitted upstream just recently. I'll see if I can find it for you...

I never changed resolution, and it happened to left aligned too. Never used VMs either.

---

### Post by Rob2687 on 2010-03-24
> **kaldor said:**
> I never changed resolution, and it happened to left aligned too. Never used VMs either.

+1


I haven't used gnome-panel since shortly after installing Lucid but in previous releases I did. The GDM resolution was different than my desktop resolution so I'm guessing the problem occurred if gnome-panel loaded before it set the desktop resolution.

---

