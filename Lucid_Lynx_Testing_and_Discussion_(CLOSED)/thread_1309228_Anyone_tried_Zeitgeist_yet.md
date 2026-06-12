---
title: "Anyone tried Zeitgeist yet?"
date: 2009-11-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by godhika on 2009-11-01
Has anyone already tried Gnome activity Journal? I tried to compile it from source but failed somehow miserably. I must admit that I am not that experienced with compiling software from source, so if someone could give me a quick guide, I would be very grateful.

---

### Post by Framli on 2009-11-01
(Excuse my terrible english)
I tried downloading various branches from the zeitgeist-gui and the zeitgeist-core launchpad, then ./configure + make + make install , then merging almost all the downloaded branches/folders in a random order.
A few exotic (for me at least) python libraries were needed, but I was finally able to run the gui. It's pretty cool even if the file association features are still under heavy developement. I surely can't make a how-to out of this, as I'm fairly new at not-trying to bork my system, but I hope that someone will do one.

---

### Post by Mr.Kappa on 2010-04-11
I know it's a bit late to respond but you can try installing zeitgeist and gnome activity log from the zeitgeist ppa. 
Use this command to add the repo ```
sudo add-apt-repository ppa:zeitgeist/ppa
``` and then to install use ```
sudo apt-get update && sudo apt-get install zeitgeist gnome-activity-journal
```
And voilà! :guitar:

---

