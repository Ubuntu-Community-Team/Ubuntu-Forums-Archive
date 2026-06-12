---
title: "Notifications (again)"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-03-25
I've just upgraded my desktop to Jaunty. My desktop is a dual monitor system configured as twin view - that is it behaves as a single screen and I can drag windows across from one screen to the other. I use my 'A' monitor for most work and my 'B' monitor to keep an eye on ongoing activities, or things that I want to read while working on the 'A' screen. 

The gnome panel occupies the top of the 'A' monitor but does not extend across to the 'B' monitor, thats the default gnome setup. 

Before Jaunty any windows that opened would open on the 'A' monitor and notifications would be sourced from the right hand side of the 'A' monitor. This was fine because the 'A' monitor is my main work area. 

With the new Jaunty setup the top Gnome panel still occupies the top of the 'A' monitor but notifications are appearing on the right hand top of the 'B' monitor, well away from my work screen.

Is this a bug or a feature?

Screenshot - Screen A ends at the end of the top Gnome panel.

---

### Post by loomsen on 2009-03-25
Configuration aint working yet. TopRight is default, and TopRight it will be no matter what you choose. 

Cpl o days and this will be fixed... This is prlly not the most important Bug to fix with a cpl of hrs left to the next milestone.

---

### Post by Peter09 on 2009-03-25
Don't mind if its a bug - as long as its not an annoying feature :)

---

### Post by Bakon Jarser on 2009-03-25
It's an annoying feature and already has two threads dedicated to it.

---

### Post by nwadams on 2009-03-25
will there be a way (when setting the position works) to choose a custom spot on the screen ourselves or is it just the corners? Because i think the only way make it display on the main monitor would be to do that.

---

### Post by TrueTom on 2009-03-25
[QUOTE=Launchpad][...], you're quite correct to point out that the average user is not going to want to recompile software. But that's fine, because they are not going to want to configure the bubble placement either. We could be wrong about that; the beauty of Free Software is that if we are wrong, you can make your own variant and it will be wildly popular.[/QUOTE]

So if want to move the bubble, please write your own notification system instead of complaining here... ;)

---

### Post by nwadams on 2009-03-25
where can I find the source code for it? I'll take a look at it and see what can be done.

---

### Post by TrueTom on 2009-03-25
[https://code.launchpad.net/notify-osd]("https://code.launchpad.net/notify-osd")

With the current hostile attitude I'm not quite sure your work will be merged, though...

---

### Post by nwadams on 2009-03-25
lol. I'm sorry, i'm not intending to be hostile. Although to be honest, i don't expect to be able to achieve anything in the near future. I am still a fairly novice programmer and have university exams coming up so unless i see a simple fix i probably won't accomplish anything.

---

### Post by TrueTom on 2009-03-25
Oh, sorry, you got me wrong. It's not you that is hostile, it's "them"... ;)

---

### Post by Bakon Jarser on 2009-03-25
I think he was referring to them being hostile.

Edit:  ha ha, I was a second too slow.

---

### Post by nwadams on 2009-03-25
with a multiple display setup,does xorg or something else keep track of how big each screen is or does it only keep track of the total size. If it only keeps track of the total size then i'm afraid we can't bind the notifications to one screen at this time without allowing for a custom position of choice. (from my limited programming skill). If it does keep track then we might be able to just simply change from total "screen" size to "screen0" size (main screen) (when calculating position to place the notification)

---

### Post by Peter09 on 2009-03-25
The key here is that the notification does not conform to the rules that the top panel is working to. The top gnome panel restricts its length to the "A" monitor. So gnome conforms to a layout that notifications do not.

---

