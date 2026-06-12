---
title: "My feedback on the Ambiance/Radiance themes"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kaldor on 2010-03-08
I just installed the Ambiance and Radiance themes on 9.10. I love it! I am mainly talking about Ambiance (dark) right now.

1) Buttons on left are great. The button icons themselves are wonderful, too.

2) The panels look very smooth and clean. Professional and appealing.

3) The scrollbars look absolutely horrible. They are clunky and huge. I think it'd look much better if it were made narrower and turned black. Kinda like the Dust theme's. It also has a weird looking "grip" on it. I dislike it entirely. 

4) Colours blend well. 

5) Humanity icons look at home. 

6) Despite my hate for the wallpaper, the black/orange theme goes well with purple.

Great artwork, loving it. I just hate the default wallpaper's blurriness and the scrollbar's size. 

I know there were other topics on this, but I wanted to have a sort of "feedback" thread in case it would get out to anyone who's putting this together.

Edit: ...where's the dock/tasklist in Lucid? Just noticed that lol

---

### Post by psyke83 on 2010-03-08
There's still a lot of work going on with the themes.

There is an update due soon, based on Kenneth Wimer's [branch]("https://code.launchpad.net/~kwwii/+junk/light-themes-refresh") which includes lots of bugfixes submitted from the community (mostly dashua).

---

### Post by 67GTA on 2010-03-08
The buttons on the left drive me insane, but that is just personal taste. I hacked them back to the right. The only glitch I've seen, aside from the ghastly scrollbar, is that the panel backgrounds are not scalable. If you resize the panel past 24, you are left with a white strip. The panel backgrounds need to be scalable. I can always resize the panel backgrounds, but most won't know how.

---

### Post by psyke83 on 2010-03-08
> **67GTA said:**
> The buttons on the left drive me insane, but that is just personal taste. I hacked them back to the right. The only glitch I've seen, aside from the ghastly scrollbar, is that the panel backgrounds are not scalable. If you resize the panel past 24, you are left with a white strip. The panel backgrounds need to be scalable. I can always resize the panel backgrounds, but most won't know how.

That's fixed in Kenneth's branch, so you'll see the fix in the next official update.

---

### Post by VMC on 2010-03-08
> **psyke83 said:**
> That's fixed in Kenneth's branch, so you'll see the fix in the next official update.

What's fixed in the next update? The left-right buttons **or** the scalability.

---

### Post by psyke83 on 2010-03-08
> **VMC said:**
> What's fixed in the next update? The left-right buttons **or** the scalability.

The panel scalability. As far as I'm aware, the button placement was a design decision.

---

### Post by kaldor on 2010-03-08
I found a problem with the new theme; Skype integration is bad. The fonts on the notification area for Skype are nearly invisible. Hovering over some buttons on Skype make blank white boxes appear, instead of text.

---

### Post by psyke83 on 2010-03-08
> **kaldor said:**
> I found a problem with the new theme; Skype integration is bad. The fonts on the notification area for Skype are nearly invisible. Hovering over some buttons on Skype make blank white boxes appear, instead of text.

Unfortunately, Skype is uses a QT3 interface which means that it cannot use any GTK themes. Only QT4 applications can use native GTK themes via [QGTKStyle]("http://labs.trolltech.com/page/Projects/Styles/GtkStyle") - for example, VLC.

---

### Post by kaldor on 2010-03-09
That's going to cause annoyance for some people, namely the less computer-savvy people.

---

### Post by Keyper7 on 2010-03-09
> **psyke83 said:**
> Unfortunately, Skype is uses a QT3 interface which means that it cannot use any GTK themes. Only QT4 applications can use native GTK themes via [QGTKStyle]("http://labs.trolltech.com/page/Projects/Styles/GtkStyle") - for example, VLC.

What in the world are you talking about? Skype has been Qt4-based and capable of using Gtk themes for a long time. *Years*, perhaps.

---

### Post by psyke83 on 2010-03-09
> **Keyper7 said:**
> What in the world are you talking about? Skype has been Qt4-based and capable of using Gtk themes for a long time. *Years*, perhaps.

Wow, it just goes to show how long it's been since I used Skype...

Anyway, there's not much we can do to fix this - the packages on skype.com would need to use the GTK style by default (or at least be smart enough to fallback to GTK in a non-KDE environment). Perhaps if Skype ends up in the Canonical partner repository, we can make this change.

---

### Post by kaldor on 2010-03-09
> **Keyper7 said:**
> What in the world are you talking about? Skype has been Qt4-based and capable of using Gtk themes for a long time. *Years*, perhaps.

How the hell did I miss that?! Nice, thank you! :)

---

### Post by Keyper7 on 2010-03-09
> **psyke83 said:**
> Wow, it just goes to show how long it's been since I used Skype...

Anyway, there's not much we can do to fix this - the packages on skype.com would need to use the GTK style by default (or at least be smart enough to fallback to GTK in a non-KDE environment). Perhaps if Skype ends up in the Canonical partner repository, we can make this change.

It will also be easy to solve once Skype releases the already-promised open source GUI. 

Which will probably happen in a billion or a trillion years.

---

### Post by kaldor on 2010-03-09
[http://www.debianadmin.com/wp-content/gallery/1004/1.png](http://www.debianadmin.com/wp-content/gallery/1004/1.png)

Anybody else think that the new GDM theme is horrible? 

Personally, I miss the older themes such as Hardy, intrepid etc.

---

