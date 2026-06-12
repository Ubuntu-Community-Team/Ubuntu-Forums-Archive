---
title: "Ubuntu Emulator not working"
date: 2014-03-08
forum: Installation &amp; Upgrades
---

### Post by zacharyi123 on 2014-03-08
I recently installed the latest daily build (PC (Intel x86) desktop image) of Trusty from here: [URL="http://cdimage.ubuntu.com/daily-live/current/"]http://cdimage.ubuntu.com/daily-live/current/

[/URL]

  Ubuntu works perfectly! I decided to try out ubuntu touch using the ubuntu-emulator to see if I  like it. Eventually I will use this to make and test ubuntu apps.


  I ran these commands to install, create and run ubuntu-emulator:


  sudo apt-get install ubuntu-emulator
  sudo ubuntu-emulator create myinstance
  ubuntu-emulator run myinstance


  The first two worked fine and when I ran the third, a virtual phone  appeared however the virtual screen was blank. I waited and waited, but  nothing happened, the screen remained blank/black (on the virtual  phone). Then I notice I have to log in terminal. I entered phablet then  phablet and logged in fine.


  Now I have the terminal logged in and a virtual kernel of the phone but the screen is blank. How can I start the graphics?


  Also, once I've got the screen working, can I reduce the window size (it doesn't all fit on one desktop)?
  Thanks! -Zach

---

### Post by kostkon on 2014-03-08
> **zacharyi123 said:**
>  The first two worked fine and when I ran the third, a virtual phone  appeared however the virtual screen was blank. I waited and waited, but  nothing happened, the screen remained blank/black (on the virtual  phone). Then I notice I have to log in terminal. I entered phablet then  phablet and logged in fine.


  Now I have the terminal logged in and a virtual kernel of the phone but the screen is blank. How can I start the graphics?
Same here, ran it a couple of times, got a blank screen. I logged in and ran unity8 again, it restarted and then I got graphics but unity was messy and buggy; that didn't work the second time though. So, I can't give you a definite solution for that.
> **zacharyi123 said:**
>  Also, once I've got the screen working, can I reduce the window size (it doesn't all fit on one desktop)?
  Thanks! -Zach
Yes, to scale it down for example to 80% of its size you would do:
```
ubuntu-emulator run --scale 0.8 myinstance
```

Anyways, even if you manage to make it work, it will be slow. The good news is that the x86 version of the emulator is coming out soon and it's obviously, much faster than this.

---

### Post by kostkon on 2014-03-09
Actually, a public preview of the x86 emulator is already available (just read the post on webupd8). Instructions are [here]("https://plus.google.com/+RicardoSalveti/posts/1u7HSYjF2He") (and also on webupd8).

---

