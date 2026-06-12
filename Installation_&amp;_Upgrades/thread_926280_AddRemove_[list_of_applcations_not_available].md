---
title: "Add/Remove [list of applcations not available]"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2008-09-21
I am trying to install Inkscape Vectore Graphics Editor in Add/remove applications, I get the following error:  List of Applications is not available.  (Ubuntu 8.0.4)  I have no clue how to repair this.  I googled it but there is no info on the web.  Can anyone suggest what to do?

---

### Post by Pumalite on 2008-09-21
Make sure 'All Available' is ticked on the left

---

### Post by ineuw on 2008-09-21
Thanks for the reply Pumalite.  'All' is selected on the left and I noticed the following message below:

Inkscape Vector Graphics Editor cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

I am sure Inkscape is available for i386 Ubuntu.  What am I doing wrong?

---

### Post by aysiu on 2008-09-21
Can you close Add/Remove, go to System > Administration > Synaptic Package Manager and then click Reload?

Then see if you can install Inkscape through Synaptic.

---

### Post by Pumalite on 2008-09-21
Maybe this helps (I'm not sure):
[http://www.inkscape.org/wiki/index.php/CompilingUbuntu](http://www.inkscape.org/wiki/index.php/CompilingUbuntu)

---

### Post by ineuw on 2008-09-21
> Can you close Add/Remove, go to System > Administration > Synaptic Package Manager and then click Reload?

There is something seriously wrong with the Synaptic Package Manager as I noticed that there is also something is wrong with the Totem Movie Player. 

I tried to re-install it and now I have several additional software problems, so I placed the installation of Inkscape on the backburner until I fix the SPM.

The below listed message came up with several audio/video related  softwares as I tried to correct it in the Synaptic Package Manager:

totem-gstreamer:
Package totem-gstreamer has no available version, but exists in the database. This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

Please advise what I can do to correct it.
Thanks

---

### Post by unutbu on 2008-09-21
Click on System>Administration>Software Sources.
Under the Ubuntu Software tab, enable the first four boxes (main, universe, restricted and multiverse).

Click close, and then try using Synaptic again.

If that does not work, open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type
```

sudo apt-get update
```
Then try Synaptic yet again. 

If it still does not work,
please post your /etc/apt/sources.list

---

### Post by aysiu on 2008-09-21
Can you close both Synaptic and Add/Remove, and then paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and paste the output back here? ```
cat /etc/lsb-release
cat /etc/apt/sources.list
uname -m
sudo apt-get update
```

---

### Post by ineuw on 2008-09-22
Thanks for everyone's kind advice. I had to check the package options in System>Adminsitration>Software Sources and I reinstalled all the missing software. The Rhythmbox music player is working fine and Inkscape appeared on the list and now is also installed.

My original problem, which I tried to resolve and in the process I messed up everything still exists but I will post a new message.

Thanks again to all.

---

