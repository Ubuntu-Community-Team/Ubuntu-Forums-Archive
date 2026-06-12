---
title: "Songbird - symbol lookup error - HELP"
date: 2009-07-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by techdude3177 on 2009-07-22
Anyone else have this issue or know how to fix it?

When i try to run songbird i get this error:
/Songbird_build-1183/./songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by techdude3177 on 2009-07-23
seriously... nobody!?

---

### Post by xc3RnbFO8P on 2009-07-23
Try:
> sudo apt-get remove libvisual-0.4-plugins 

---

### Post by techdude3177 on 2009-07-23
tried that, same error happens

---

### Post by xc3RnbFO8P on 2009-07-23
In Synaptic Package Manager search **gstreamer python** what version do you have?

---

### Post by techdude3177 on 2009-07-23
you mean my python-gst package? thats 0.10.15.3-1

---

### Post by xc3RnbFO8P on 2009-07-23
Karmic Koala? , did just change it now?
Or is it me :)
Maybe that is the answer to your problem.

---

### Post by techdude3177 on 2009-07-23
yea i just changed it i realized it was still on jaunty, lol

i was going to post in there but wanted to try here first.

---

### Post by xc3RnbFO8P on 2009-07-23
> yea i just changed it i realized it was still on jaunty, lol

i was going to post in there but wanted to try here first.
You got me worried :) 
Should be moved.

---

### Post by techdude3177 on 2009-07-23
Anyone else have this issue or know how to fix it?

When i try to run songbird i get this error:
/Songbird_build-1183/./songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by overdrank on 2009-07-23
moved to Karmic Koala Testing and Discussion

---

### Post by techdude3177 on 2009-07-23
awesome thanks

---

### Post by techdude3177 on 2009-07-24
So i updated to the 1.3 beat 1 of songbird to see if that would fix the error and i am still getting the same error read out. 

/home/username/Songbird/./songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by techdude3177 on 2009-07-25
I was able to get my hands on a PPA developer version for Karmic which is Songbird 1.4 so i cannot install the ipod addon yet which puts me back to square one of why i updated songbird 1.0 but if anyone else needs this just to get songbird running here it is...

here are the repros
deb [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu) karmic main

to install the key
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5719E347

and isntall songbird
sudo apt-get update & & sudo apt-get install songbird

---

### Post by durand on 2009-07-25
Shouldn't that be:
sudo apt-get install **s**ongbird

Sorry, in a picky mood :P

---

### Post by techdude3177 on 2009-07-25
LOL, well that is a good point... i edited it just for you!:)

---

### Post by durand on 2009-07-25
Hehe :D

---

