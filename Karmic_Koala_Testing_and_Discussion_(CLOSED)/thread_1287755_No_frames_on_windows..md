---
title: "No frames on windows."
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dadedo123 on 2009-10-10
I'm not getting any frames in windows since I installed alpha6 UNR. It is really annoying. 

[IMG]http://img444.imageshack.us/img444/6757/screenshoth.png[/IMG]
How can I fix it?

---

### Post by ranch hand on 2009-10-10
OK, I'll bite, what on earth are you asking about?

Looks pretty similar to what I have under Jaunty, as do all my Karmic installs.

I have never seen Update Manager on my bar.  The background color on my bars have been set to please me.  I rarely use "icon view".

Other than that it looks like a window to me.

I always thought that the frame of the monitor was enough.

You could add panels on the sides if you want.

---

### Post by perlluver on 2009-10-10
I believe he is asking: where are the exit, minimize, maximize buttons.

---

### Post by VMC on 2009-10-10
You know what. That looks very similar to what I had just before I changed my Intel driver to the latest 2.9.0 and kernel-12. I had no way to control any opened windows.

What video graphic chip do you have?

---

### Post by gradinaruvasile on 2009-10-10
> **dadedo123 said:**
> I'm not getting any frames in windows since I installed alpha6 UNR. It is really annoying. 

[IMG]http://img444.imageshack.us/img444/6757/screenshoth.png[/IMG]
How can I fix it?

It seems metacity crashed. Metacity is the window decoration manager, that is responsible for drawing the window frames. Try pressing alt+f2 then type 
```
metacity --replace
```

---

### Post by ranch hand on 2009-10-10
Well.  I sure am observant aren't I.

Sorry, just a moron.

---

### Post by dadedo123 on 2009-10-11
metacity --replace has worked for only one windows. All other windows remain the same, without the frame. :(

---

### Post by Lorag on 2009-10-11
In UNR a programm called maximus maximizes your windows and removes the titlebar. But the close button should normally be in the top panel then. I don't know why it isn't in your case. Maybe you can check what applets you have in your panels or what your maximus settings are. 
If none of this helps you could use namebar: [http://www.gnome-look.org/content/show.php/NameBar?content=101643](http://www.gnome-look.org/content/show.php/NameBar?content=101643) 

Good luck!

---

### Post by dadedo123 on 2009-10-11
> **Lorag said:**
> In UNR a programm called maximus maximizes your windows and removes the titlebar. But the close button should normally be in the top panel then. I don't know why it isn't in your case. Maybe you can check what applets you have in your panels or what your maximus settings are. 
If none of this helps you could use namebar: [http://www.gnome-look.org/content/show.php/NameBar?content=101643](http://www.gnome-look.org/content/show.php/NameBar?content=101643) 

Good luck!

If I minimize the window, or move the window, I do get the titlebar.
and how do I check my maximus settings?

---

### Post by Lorag on 2009-10-11
You can edit the settings with gconf-editor. Go to apps > maximus and uncheck the option "undecorate". 

But you should really try to add the defauls maximus applet to your panel which gives you title bar functionality. I'm not sure as i don't run UNR but i thinks it's called something like window picker.

---

### Post by dadedo123 on 2009-10-11
> **Lorag said:**
> You can edit the settings with gconf-editor. Go to apps > maximus and uncheck the option "undecorate". 

But you should really try to add the defauls maximus applet to your panel which gives you title bar functionality. I'm not sure as i don't run UNR but i thinks it's called something like window picker.

The option undecorate is already unchecked!

---

### Post by dadedo123 on 2009-10-11
wohoo, thanks! I was able to fix it! From the same directory that you gave me, there was a tab that was called "Do not maximise" and for some reason it was checked by default. I unchecked it, and it all worked. wohoo!

---

### Post by go7Ul1ai on 2009-10-11
> **dadedo123 said:**
> wohoo, thanks! I was able to fix it! From the same directory that you gave me, there was a tab that was called "Do not maximise" and for some reason it was checked by default. I unchecked it, and it all worked. wohoo!

Celebrate good times now come on! :)

---

### Post by dadedo123 on 2009-10-11
> **lee.jarratt said:**
> Celebrate good times now come on! :)

Celebrate good time, c'mon, let's celebrate, it alright.

---

