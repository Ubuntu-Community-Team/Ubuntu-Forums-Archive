---
title: "Another try, Remove the PalmOS-program from settings"
date: 2009-06-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-06-14
Back in Jaunty development a made a thread about removing the PalmOS-program from settings. I also filed a bugreport and a brainstormidea. 

There was an overwhelming majority that wanted this (1056 for, 134 against).

I even attached a debdiff to the original report to make this simple but needed change happen.

So..here we go again ;)

[http://ubuntuforums.org/showthread.php?t=1080350&page=3](http://ubuntuforums.org/showthread.php?t=1080350&page=3)
[https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/334446](https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/334446)'
[http://brainstorm.ubuntu.com/idea/3844/](http://brainstorm.ubuntu.com/idea/3844/)

---

### Post by durand on 2009-06-14
I hope it does get removed. Someone might find a use for it but then to be fair, we would have to support other mobiles as well by default and that's just stupid :|

---

### Post by andrewabc on 2009-06-14
Don't remove it. I have an iPAQ and use it everyday.

oh wait...

---

### Post by ktp on 2009-06-14
> **olskar said:**
> back in jaunty development a made a thread about removing the palmos-program from settings. I also filed a bugreport and a brainstormidea. 

There was an overwhelming majority that wanted this (1056 for, 134 against).

I even attached a debdiff to the original report to make this simple but needed change happen.

So..here we go again ;)

[http://ubuntuforums.org/showthread.php?t=1080350&page=3](http://ubuntuforums.org/showthread.php?t=1080350&page=3)
[https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/334446](https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/334446)'
[http://brainstorm.ubuntu.com/idea/3844/](http://brainstorm.ubuntu.com/idea/3844/)

+1

If someone needs it then they can easily install it.

---

### Post by Foaming Draught on 2009-06-14
Agreed.  I'm a Palm fan, but I have to install JPilot anyway because useless Evolution doesn't sync, so it's an easy thing to grab pilot-link at the same time.

---

### Post by olskar on 2009-06-15
And..it's fixed! :D

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/334446](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/334446)

---

### Post by mcdavey on 2009-06-15
Has this "fix" been tested?  What does it do?  That is, what is the effect on a new default install?

---

### Post by yelo3 on 2009-06-15
gnome-pilot is still there, not fixed

---

### Post by olskar on 2009-06-15
The fix removes gnome-pilot from a default installation. The update will not make gnome-pilot disappear, you have to reinstall latest daily (or next alpha) to notice the fix.

---

### Post by mcdavey on 2009-06-15
How do you remove gnome-pilot from a default install?
The Evolution package depends on it.
Try "dpkg-query -W -f '${Depends}' evolution"

---

### Post by olskar on 2009-06-15
> **mcdavey said:**
> How do you remove gnome-pilot from a default install?
The Evolution package depends on it.
Try "dpkg-query -W -f '${Depends}' evolution"

Hm, I'm on Jaunty at the moment but here 'sudo apt-get remove gnome-pilot' does not remove evolution..

---

### Post by mcdavey on 2009-06-15
Sorry for the granular responses, but what happens for you now if you go to Evolution and select "Edit -> Synchronization Options" ?

(gnome-pilot is broken into libgnome-pilot2 and gnome-pilot packages.  On 8.10, "sudo apt-get remove gnome-pilot" offers to remove the gnome-desktop, so I guess it's cleaned up in Jaunty, allowing you to remove the gnome-pilot package and leave Evolution asking for a system service (gpilotd) that is not present).

---

### Post by rudenko_ruslan on 2009-06-15
> **mcdavey said:**
> Sorry for the granular responses, but what happens for you now if you go to Evolution and select "Edit -> Synchronization Options" ?
I see a pop-up with text on it - "Welcome to gnome-pilot!", blah-blah-blah. Some kind of wizard? :-k

---

### Post by mcdavey on 2009-06-15
Right, that wizard is gnome-pilot popping up to help you configure (PalmOS) PDA synchronization.  What I was getting at is that, presumably, with the "fix" implemented it will either mean nothing happens, or Evolution complains in some way.  Either way, a new user will have little clue what to do next, but hopefully will be able to find out after hitting google.

---

### Post by ktp on 2009-06-15
> **mcdavey said:**
> Right, that wizard is gnome-pilot popping up to help you configure (PalmOS) PDA synchronization.  What I was getting at is that, presumably, with the "fix" implemented it will either mean nothing happens, or Evolution complains in some way.  Either way, a new user will have little clue what to do next, but hopefully will be able to find out after hitting google.

I don't use anyone of these so don't know, but if Evolution does not depend on gnome-pilot, and only depends on libgnome-pilot2, things should just work.  If it does not then Evolution does not depend on the right things, which should be a bug.  Can you try it?

---

