---
title: "Yet another &quot;Gutsy won't shut down&quot; thread"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Mountaingod on 2007-10-24
I clean-installed Gutsy yesterday, and there were a couple of problems. I've ironed them out (thanks to the IRC channel), except for this one which everybody seems reluctant to tackle.

When I click the shutdown button next to the clock and select _S_hut down, the screen goes blank and my laptop freezes. I've left it for ages and it never gets any further. I have to cut the power to turn it off at this point.

Gutsy 'restarts' fine, and will successfully power down when I do "sudo halt". It just won't shut down normally.

Searching on the forums, problems with shutting down are widespread but there have been very few attempts to address the issue. It seems like a particularly fundamental problem to have in an operating system, especially as the alternatives (cutting the power, halt) aren't the healthiest things to do repeatedly to a computer.

Shutting down on Feisty, which I had previously, worked fine. Has anybody found a solution to this problem?

Thanks.

---

### Post by Mountaingod on 2007-10-24
Oh wow, I also discovered that Ubuntu crashes if I attempt to log out. It's comforting to know so much effort was put into making the windows whoosh around the desktop semi-transparent, so long as you don't actually intend to stop using the computer at some point.

---

### Post by Mountaingod on 2007-10-24
Bump before I go and play Halo. Yeah, that's right, you've driven me to M$ ;)

I'm sure such a major and widespread problem will receive a fix soon enough. Or at least some acknowledgment. Until then, *sudo halt* for me. That's the price I pay for flashy graphics and up-to-date repositories.

---

### Post by monkeymoo on 2007-10-24
Have you tried disabling the splash screen? It worked for me (and others) who had this problem.

---

### Post by Mountaingod on 2007-10-25
How would I go about doing so? I only just managed to get the splash screen *working* on startup! The not-shutting-down issue was present while the splash screen was absent, although it wasn't actually *disabled*, just had the wrong resolution in usplash.conf

Last time I tried a restart, that froze too. GNOME closed, the splash screen started, and it got about 3/4 empty before the screen flashed on and off a few times, then blank/frozen again.

Bizarre.

---

### Post by monkeymoo on 2007-10-25
You need to edit the file "/boot/grub/menu.lst", eg. do "sudo gedit /boot/grub/menu.lst" in terminal. 
Down at the bottom of the file you'll see a list of kernels eg. Ubuntu 7.10, kernel 2.6.22-14-generic (or similar). For the one you are using (which will probably be the first one if you haven't changed anything, but you could do it for all of them if you aren't sure) you need to change "splash" to "nosplash". It'll be on the end of the line that begins "kernel". 

It won't work until the next time you boot, but when you shut down after that you will probably just get a message in red text saying you are shutting down and then it will shut down properly. 

Hope this works for you.

---

### Post by Mountaingod on 2007-10-26
Thanks a lot for your help monkeymoo, somehow though the thing has started working normally :? It seems more inconsistent than I thought.

I've got a feeling it's to do with whether or not I shut down with my external hard drive still mounted. When I started unmounting/turning it off to protect it when I attempted a shutdown, it did it fine. I'm tempted to try and recreate the error but that would be looking a gift horse in the mouth.

---

