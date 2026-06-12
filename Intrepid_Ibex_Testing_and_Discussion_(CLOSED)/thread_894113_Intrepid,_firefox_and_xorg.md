---
title: "Intrepid, firefox and xorg:"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Glowing Fish on 2008-08-19
I actually have a host of issues (as is often the case), which all date back to last week when I went from hardy to intrepid, mostly because I wanted sound in zsnes to work better (but that is a different story)

Most things are working well, although there are a few cosmetic changes that I don't like so much.

But the main problem is that certain websites make Xorg go to 100% of processor capacity. Facebook being the biggest culprit. Desktop Tower Defense, an online flash game, has the same problem. And yet youtube still runs as smoothly as ever.

Does this sound familiar to anyone? I hope I posted this in the right forum, and that this hasn't already been addressed...I couldn't find anything in a search.

---

### Post by Glowing Fish on 2008-08-22
Hmmm...no response to this?

Would it be productive of me to file a bug report on this? Where would I go to do so? This might be something that people working on intrepid would like to know about!

---

### Post by Elfy on 2008-08-22
I'd check out the intrepid forum [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346) to see if it's been seen.

---

### Post by dmizer on 2008-08-22
Moved to Intrepid testing forum.  You'll likely get better responses here.

---

### Post by psyke83 on 2008-08-22
> **Glowing Fish said:**
> I actually have a host of issues (as is often the case), which all date back to last week when I went from hardy to intrepid, mostly because I wanted sound in zsnes to work better (but that is a different story)

It was a mistake to upgrade to Intrepid merely to make zsnes "work better". Anyway, you need to run zsnes with the parameter once: ```
zsnes -ad sdl
```

Sound will then work perfectly (I assume this was your problem), though you may also want to configure PulseAudio correctly (see below).

> Most things are working well, although there are a few cosmetic changes that I don't like so much.


All the original Murrine themes are still available, and if you don't like them, you can get the old Human theme from the package "gtk2-engines-ubuntulooks".

> But the main problem is that certain websites make Xorg go to 100% of processor capacity. Facebook being the biggest culprit. Desktop Tower Defense, an online flash game, has the same problem. And yet youtube still runs as smoothly as ever.

Yes, if you did a cursory search of this forum you would see that Flash 10 beta 2 is *very* CPU-intensive. Luckily the release candidate works much better.

> Does this sound familiar to anyone? I hope I posted this in the right forum, and that this hasn't already been addressed...I couldn't find anything in a search.

I strongly recommend you configure PulseAudio correctly, as it will solve a lot of issues on your system. Follow the steps in this post, making sure to substitute "hardy" for "intrepid" in step 4: [http://ubuntuforums.org/showthread.php?p=5587712#post5587712](http://ubuntuforums.org/showthread.php?p=5587712#post5587712)

Following those steps will give you a properly configured sound system and Flash 10 RC.

For more information on PulseAudio (it's not necessary to follow the steps, only see for the FAQs and information in the appendixes), see: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965) (Intrepid) and [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) (Hardy).

---

### Post by Nullack on 2008-08-22
mate have you had any feedback about when the repos wil have your goodness? Ive seen the dev discuss stuff.

---

