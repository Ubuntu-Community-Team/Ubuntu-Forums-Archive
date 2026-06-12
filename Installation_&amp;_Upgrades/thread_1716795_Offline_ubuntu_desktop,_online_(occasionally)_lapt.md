---
title: "Offline ubuntu desktop, online (occasionally) laptop"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by Woodogg18 on 2011-03-29
So I am going to dual boot install my desktop at home with windows and ubuntu 10.10. This desktop does not have an Internet connection. However, I have a laptop (hp g61) that I plan on doing the same type of boot config to. So my question is... If I have driver problems or want programs for my desktop, can I get these with my laptop and then transfer to my desktop?. I know I can get some programs from a .dev file I've already got with a lot of various programs that will (I guess) automatically install. My real concern is drivers as I have heard that ati video cards tend to have some problems.  :confused:

---

### Post by Rasa1111 on 2011-03-29
well..

You can download .deb packages for programs, save them to USB drive,
then transfer them to the desktop and install them using software center or gdebi.

However...

Once you have Ubuntu installed on the desktop..
You are going to want to run the updates required for a new install.

 Otherwise..
I don't think you'll have much luck installing programs/apps. 

Is there anyway the desktop can be hooked up to ethernet at least for the install/updates? 

 I know that, whenever Ive done a fresh install..
and ive forgotten to do the updates before installing programs,
I get an error that it cannot install said program.
But once I do the updates, installing things is no problem.

Drivers are possible to get offline.. (download then transfer to other PC))
But without the desktop being online..
you won't know which drivers you need for what. 

Not without a lot of searching, that is. 

 Say, your desktop needed certain drivers...
If it was connected.. it would just search for the drivers needed, and you would click and install&activate them.

But, without it being connected...
Im not sure how you're going to find out what drivers you need
(or how to install/activate them)

Sorry Im not more help.
 
Good luck :)

---

### Post by Woodogg18 on 2011-03-29
So, my only option I can do is to maybe take my desktop to a friends house to get the updates. Can I install ubuntu first and then take it over there? Or do I have to install it while connected to get said updates? Also, will the updates include the drivers I will need or will I have to do something to get them (like in the device manager in windows) sorry if I kind of sound clueless, but with Linux I pretty much am. I am actually doing this for the first time with the intent on actually using it. Lol. I am, however, fairly proficient with windows and basic hardware. I am a computer nerd for sure, I just never got into Linux due to the differences.

---

### Post by Rasa1111 on 2011-03-29
hey,
 no problem, no apologies. :)
i was a total linux 'noob' 1 year ago.
learned a lot in that year..
but still a 'noob'. lol

Thats what I would do ~(and have done once before.)
perhaps there are other ways, but I dont know of any, 
and they are probably more complicated if so :lol:

I took my tower (and lcd monitor) because his computer was up and he didnt want to disconnect it.(understandable). lol

 I had dial up at the time, and this was easier than getting the dial up thing situated. (i tried).
He is a neighbor, so it was close by. ;)

Yeah you can install Ubuntu first. 
thats how I did it. 

 Install ubuntu..
take the desktop to where you can plug it into an ethernet cable,
once connected, open update manager.
System>Administration> Update Manager

 Let it find all the updates it needs, 
download them and wait for them to finish, and install. 

By now,
 you may have been alerted that there were other drivers available for your system.. but if not..

You can check by going back to System>Admin> Additional drivers.

Let that check for any drivers, and if there's any you need, you can activate/deactivate them. 

 I would first make sure everything is working ok before i installed/activated any drivers though. 

Next thing you should do..
 if you want to play media on the desktop, music/video/flash/DVD etc..
you should install "ubuntu restricted extras" .
That will install virtually any codec you could possibly need. lol

 Install it through software center, synaptic package manager, or by the terminal, if you're comfy with that. 

 In software center, or synaptic package manager,
just type 'restricted extras' into the searchbox provided.
(both in the upper right hand corner).

if using the terminal, 
 type 
```
sudo apt-get install ubuntu-restricted-extras
```

 If using Ubuntu 10.10,
 I also think it's good to install "Gdebi" (find it in software center, or synaptic also)
Then you can install deb packages thru that instead of using software center. (quicker)

 Hope something ive said helps. lol

edit: You could also, since you're there..
Go ahead and download any programs you'll be wanting/needing. 
Im sure your friend wont mind?

That will save you the trouble of going from the laptop to the desktop right away, and give you some room to play before having to find and install deb packages. 

 good luck, have fun. :)

---

### Post by Woodogg18 on 2011-03-29
Thanks a lot. I am really anxious and exited to be running ubuntu, I'll post an update when I'm done. One more question if your still there. Lol. I want to get compiz fusion up and going when I'm done. Is that included with ubuntu? Or will I have to be connected to get/download it? I have been assuming it's included, but with Linux I really can't assume anything at this point.

---

### Post by Dutch70 on 2011-03-29
Compiz should be pre-installed. You can check in software center to make sure. 

You may want to add the compiz-fusion-plugins-extra. You can find them here, just a little ways down the page, under...
"I can't find some of the plugins mentioned in this FAQ. Where are they?"
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=809695[/COLOR]]("http://ubuntuforums.org/showthread.php?t=809695")

A few things you may want to do after installing...
[[COLOR="Blue"]http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu-10-04-lucid/[/COLOR]]("http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu-10-04-lucid/")

---

### Post by Rasa1111 on 2011-03-29
No problem. :)
I was very excited to start running ubuntu a year ago also..
and Im still excited with it! lol

For compiz,
it is already installed. 

Though you may want to download/install CCSM 
(compiz config settings manager)
That gives you a lot of (easy) options to play around with.
(you can also find this in software center or synaptic)

You might also want to install emerald theme manager, and the emerald theme engine. (this, and compiz pretty much go together).

This link [http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html](http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html)
will tell you about emerald (and show you to install it).

To switch to compiz (special/visual efects)
Go to System>Preferences> Appearance >, and go to the "visual effects" tab.

 The top choice is no effects (no compiz)
The ones below it are for effects/enhanced effects/custom effects. 

usually by default, if the computer can handle compiz, the 2nd choice will be checked. (visual effects on).

looking forward to seeing your progress. :)

Peace love n Ubuntu! lol

---

### Post by Woodogg18 on 2011-03-31
Success! So I've got everything installed, then ran the update manager, got my drivers (only needed my graphics driver) and I'm all up and running. I configured my compiz effects (beam me up Scottie), by the way, I love the customization. I only had trouble during the install when I was trying to set up a shared data partition for my two OSs. I suppose I'm still a little to noobish to pull that off just yet. Also I was kinda in a hurry so I just split my drive in two. Thanks for all your help, I believe this will be my main OS for now for everything but gaming.

---

### Post by Rasa1111 on 2011-03-31
Niice!
Congrats woodogg!

Good job! :)
(can you believe some people say it's "soo hard"?) lol ;)

 I love all the customization options also..
and I'm still finding more all the time! 

 Glad it all worked out for you man.
:)
See you around.

---

