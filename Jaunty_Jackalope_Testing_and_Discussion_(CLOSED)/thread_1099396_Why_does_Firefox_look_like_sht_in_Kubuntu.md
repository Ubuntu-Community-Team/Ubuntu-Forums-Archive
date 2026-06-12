---
title: "Why does Firefox look like sh*t in Kubuntu?"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jwork123nl on 2009-03-18
I know this has been discussed in the past.

But why should I have to install extra stuff to get a better-looking firefox?
I thought everything would be themed etc?

---

### Post by lisati on 2009-03-18
pass.

I've noticed a difference between the appearance of 3.07 on Windows (XP & Vista) & Ununtu 8.10 as well.

---

### Post by Vorian on 2009-03-18
> **jwork123nl said:**
> I know this has been discussed in the past.

But why should I have to install extra stuff to get a better-looking firefox?
I thought everything would be themed etc?

sudo apt-get install kde-style-qtcurve

see this blogpost!
[http://jtechinda.blogspot.com/2009/03/gtk-apps-qtcurve-and-kubuntu-904.html](http://jtechinda.blogspot.com/2009/03/gtk-apps-qtcurve-and-kubuntu-904.html)

---

### Post by jwork123nl on 2009-03-18
Hmm, I installed kde-style-qtcurve

Did not help with Firefox, still the win95 theme.
I guess I have to fiddle some more :-(
Perhaps I have to do something to let firefox use this style???

But my point was: why does a user have to fiddle with packages and
settings to let such an important application look integrated?
I thought this was the point of having a good distro, that they
provide sensible defaults, no?

---

### Post by pelle.k on 2009-03-18
> But my point was: why does a user have to fiddle with packages and
settings to let such an important application look integrated?
I thought this was the point of having a good distro, that they
provide sensible defaults, no?
The blog post points out that new installations ( >alpha6 ) have this on by default.
For you, install gtk2-engines-qtcurve, gtk-chtheme and activate qtcurve with gtk-chtheme.

---

### Post by jwork123nl on 2009-03-18
Aha!

that did the trick.
I do not understand why updating (I am beyond alpha 6 now)
did not solve this automatically, I did not manually change config
files.

But ok, it works now, thx!

EDIT: and good to hear that the kubuntu developers DID provide the automatic configuration!

---

### Post by gunksta on 2009-03-18
One reason an upgrade could not affect your existing system is because the files that needed to be changed exist in your ~ directory. Even if they necessary stuff was installed on your system, which could have been accomplished with an apt-get install kubuntu-desktop, you would still have a borked .gtkrc in your ~ directory. Updates do not normally play with files in our ~ directory (fortunately) and this is what needed to change in order to actually see the new theme.

But, I am very glad to see that this is now the default for users of Kubuntu, because GTK apps

---

### Post by martalli on 2009-03-19
This looks great with intrepid, too.  Evolution looks better than ever (including when I was using it in gnome =).

---

### Post by canesalato on 2009-03-19
IMHO qtcurve, with some clever costumizations, can be A LOT better than oxygen style itself

---

### Post by gunksta on 2009-03-19
canaselato:

I have played around with the qtcurve settings (the QT version of QT curve) and I can not make it look exactly like FireFox. My scrollbar slider in FireFox has this nice rounded affect that I can not match via the QT settings.

Suggestions?

---

### Post by Vorian on 2009-03-19
> **canesalato said:**
> IMHO qtcurve, with some clever costumizations, can be A LOT better than oxygen style itself
I agree on the oxygen part, I use skulpture (kde-style-skulpture)

I like it quite a lot

---

### Post by IanW on 2009-03-20
To answer the original question...

"Re: Why does Firefox look like sh*t in Kubuntu?"
Because KDE devs want you to use Konqueror.

---

### Post by canesalato on 2009-03-20
> **gunksta said:**
> canaselato:

I have played around with the qtcurve settings (the QT version of QT curve) and I can not make it look exactly like FireFox. My scrollbar slider in FireFox has this nice rounded affect that I can not match via the QT settings.

Suggestions?

mmm...that's strange: I have the exact same rounded scrollbar slider, both in gtk and in qt (including firefox)...could this be a bug?

---

### Post by gnomefreak on 2009-03-20
The reason for it is with gnome there is Firefox-gnome-support package to help blend in better.
There is no QT support at this time. Mozilla was working on it but as i recalled it stalled due to problems trying to intergrate for QT libs, so don't expect it soon, I'm hoping by middle on the KK devel cycle but we shall see.

---

### Post by canesalato on 2009-03-20
> **Vorian said:**
> I agree on the oxygen part, I use skulpture (kde-style-skulpture)

I like it quite a lot

I like it too...even more I like qtcurve, because, for the first time in years using linux, using qtcurve and kgtk I get the feeling of a true unified kde desktop even using firefox and aMule. And without too much work, since kde settings gets applied automagically to gtk as well.
It would be nice to know the opinion of the other kubuntu/kde users: are we really sure that most of them prefer oxygen as default style?

---

### Post by jjpcexpert on 2009-03-20
> **jwork123nl said:**
> I know this has been discussed in the past.

But why should I have to install extra stuff to get a better-looking firefox?
I thought everything would be themed etc?

Download gtk-chtheme(or use gtk-qt-engine) and then download the attachment.

How to extract:
kdesudo ark
kdesudo dolphin

Drag your ZIP from a non-kdesudo'ed Dolphin into a KDEsudo'ed Ark, and then go to the KDEsudo'ed Dolphin and in the address bar, type /usr/share/themes and then from Ark drag "kde4-oxygen" into /usr/share/themes.

Or just install human-theme to use with GTKchtheme and it will look stupid.

---

