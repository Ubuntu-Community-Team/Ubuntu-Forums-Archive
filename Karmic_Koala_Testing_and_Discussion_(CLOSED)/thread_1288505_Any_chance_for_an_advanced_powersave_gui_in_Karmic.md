---
title: "Any chance for an advanced powersave gui in Karmic?"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cptrohn on 2009-10-11
For the laptops users out there?  I know they a great one in KDE and most other distros out there... (one that lets you choose from a performance option all the way down to an extreme powersave option)   I mean it IS commonplace on just about every OS from windows to OSX to Kubuntu..... they should really have one in Gnome as well since laptops are so commonplace now-a-days....


Just my 2 cents... for what it's worth ;)

---

### Post by crjackson on 2009-10-11
Right click on panel>Add to Panel>CPU Frequency Scaling Monitor

Once it's on the panel, left click and select your desired performance level.

---

### Post by fela on 2009-10-11
> **crjackson said:**
> Right click on panel>Add to Panel>CPU Frequency Scaling Monitor

Once it's on the panel, left click and select your desired performance level.

The CPU isn't the only thing that uses power in a laptop. You also want all the other stuff such as display brightness; display turn-off delay; HDD spin-down time; etc etc etc.

---

### Post by ranch hand on 2009-10-11
I am on 9.04 right now and I only have a desktop box.  I have had that on here before and it really doesn't do anything and there are no settings.

Is this something just for laptop use or is it different in 9.10?  Never thought to look at it there.

---

### Post by slakkie on 2009-10-11
It is called powerdevil. If you have the battery widget, you can click on it and do the thing you want to do.. 

See 
[http://opperschaap.net/~wesleys/ubuntu/karmic/powerdevil_widget.png](http://opperschaap.net/~wesleys/ubuntu/karmic/powerdevil_widget.png)
[http://opperschaap.net/~wesleys/ubuntu/karmic/powerdevil_change_more_stuff.png](http://opperschaap.net/~wesleys/ubuntu/karmic/powerdevil_change_more_stuff.png)

Owwww. you ment for gnome.. I dunno, I use KDE..

---

### Post by ranch hand on 2009-10-11
Wow, this is all neat.

My wife would like a laptop and I am trying to learn a little about them before we get one.

---

### Post by Amaranth on 2009-10-11
These options are basically a "break my system" setting. The ondemand governor is the best choice for both power saving and performance.

---

### Post by mcduck on 2009-10-11
Such options are only really useful in very special situations. Most of the time the default "ondemand" governor will give both the best performance *and* battery life.

For any modern CPU the most effective (and least power consuming) way is to do things as fast as possible to get back to idle state (and lowest CPU frequency) as quickly as possible.

This means that on any normal situation using "powersave" or "conservative" governors will actually decrease your battery life. And the "performance" governor doesn't really have any noticeable performance increase over the "ondemand", since switching between frequencies happens very quickly.

"Conservative" and "powersave" governors are only useful in situations where you run some CPU-intensive task that takes the same time regardless of the computing power used to handle the task, for example when playing a game (which will of course continue as long as you play the game, so no matter how much computing power you throw at it the CPU won't get back to idle any sooner).

---

