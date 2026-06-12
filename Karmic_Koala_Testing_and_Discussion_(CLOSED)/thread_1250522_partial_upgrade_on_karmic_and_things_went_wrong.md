---
title: "partial upgrade on karmic and things went wrong"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mephist0pheles on 2009-08-26
After doing a partial upgrade on my karmic, it said something about my filesystem being corrupted. Then I did an fsck. Restarted with Ctrl+D. File system still corrupted. It started doing something...not sure what. Restarted again in frustration, interrupting whatever it was that linux was doing before. Suddenly, it works again, except now my desktop is blank and ubuntu won't let me change it. There are also no icons on my desktop. :(

Help??:confused:

---

### Post by mephist0pheles on 2009-08-26
bump

---

### Post by mephist0pheles on 2009-08-30
anybody?

---

### Post by VMC on 2009-08-30
Since your talking karmic you need to post in that forum.

It sounds like you don't have all the updates properly installed.

Maybe try cleaning :

```
sudo apt-get clean && sudo apt-get autoremove && sudo apt-get install -f

```

also you might try adding a test user and see if that user has a desktop.

---

### Post by autocrosser on 2009-08-30
In the first place--you should never do a partial upgrade UNLESS you know exactly what you are doing---please search for posts in this forum about it.

Secondly--unless you are fairly well versed in how to recover your system after it has been b0rked--you should be using Jaunty instead of Karmic--we have just got to feature freeze & there are still lots of bugs to be killed.

Thirdly--I reinstall about every 6 months due to accumulated cruft due to development software--I would advise you to either install Jaunty or if after what I've said reinstall Karmic & take things a bit more carefully...Karmic is still more for advanced users until it is released.

And PLEASE read the forums/search for answers/ASK QUESTIONS before doing things if you don't know how to fix it yourself.

---

### Post by VMC on 2009-08-31
> **autocrosser said:**
> --I reinstall about every 6 months due to accumulated cruft due to development software--Words to live by. I'm amazed how some never reinstall but just keep upgrading.

I've entered in at alpha3 and have been updating constantly. I do this mainly to see the progress on my hardware and software. I file bug reports in hopes that it will help the overall scheme of things. In the end I will reinstall the final product when it reaches production status.

---

### Post by inportb on 2009-08-31
Well... if you stick with the stable versions (or better yet, the LTS's), it is indeed possible to keep on upgrading. On my laptop, though, I always get the development version so I reinstall instead of upgrade.

---

### Post by psyke83 on 2009-08-31
I agree with the warnings about partial upgrades, but in this case I don't think that a partial upgrade is the cause of the issue.

See: [http://ubuntuforums.org/showthread.php?t=1252690](http://ubuntuforums.org/showthread.php?t=1252690)

---

