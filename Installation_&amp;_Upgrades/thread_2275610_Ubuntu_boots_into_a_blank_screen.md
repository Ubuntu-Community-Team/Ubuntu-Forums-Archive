---
title: "Ubuntu boots into a blank screen"
date: 2015-04-27
forum: Installation &amp; Upgrades
---

### Post by coacharnold on 2015-04-27
I just upgraded from 14.10 to 15.04 and now when I boot into the system I get a blank screen. ( it looks like a graphically generated black screen) 

I get no feedback from it at all no blinking cursor.  I can ctrl-alt-f1 into a console and everything is working just fine.  I have an NVIDIA graphics card, but my understanding is that if there is a driver issue it should default back to the open source NV drivers.  After some research, here's what I found.

1 - There is a problem from 12.10 to 13.4 that someone spoke about there being an issue like this that had to do with running off of a Solid state drive. ?

2 - I'm wondering if there is an issue with LightDM.  when I was installing I got an installation GUI pop up that warned me to make sure I had grub installed as there would be a boot problem with light DM.   I have grub installed so I clicked continue. 

3- there is always a myriad of people complaining about NVIDIA problems in X11.  but I'm not getting anything but a black graphics screen... as in it appears to be a graphicaly generated black screen with x running .... just nothing showing .

I know someone is going to ask me for my x11 file or logs.   I'm at work posting this hoping someone can just give me some Ideas on this. 

Thanks

Tim

---

### Post by eddie25 on 2015-04-27
I had the same issue after upgrading from Ubuntu 14.10 to 15.04.  After rebooting I was able to type in my password and then a black screen appears and it does nothing, yet I can move my mouse around with no issues.  

I ended up rebooting and went to the advance option for Ubuntu and used Linux 3.16.0.34 and then Ubuntu worked fine but when I used Linux 3.19.0 it would go back to the black screen after typing in my password.

---

### Post by coacharnold on 2015-04-28
I solved my issue ..sort of .... th current NVIDIA drivers only half work.   
- I uninstalled / purged NVIDIA , and reinstalled the current NVidia drivers.
       this got X up and running to a point where I had a background and a handful of windows but no desktp GUI
       I did a full install of the Xubuntu desktop to see if I could get a lower graphics windows manager to work.
        XFCE installed fine and worked.   I was able to use it to get chrome up and running and do some more research. Which told me to COMPLETLY purge NVIDIA and   allow  the NV drivers to take over. 
      I thought UBUNTU was supposed to drop back to the NV drivers if the proprietary drivers didn't work ....  but ok ...  I purged NVIDIA completely and EVERTHING came back up ..... including all of my desktop effects, which I thought wouldn't work on the NV drivers, with all the rendering.

I guess the NV drivers have been worked on since last I had to use them. 

so maybe at this point, I don't have to use the NVIDIA drivers .....  STILL this video issue is something that harkens back to 7.04  not 15.04.  It's the kind of thing that gives Linux a bad name amongst windows users

---

### Post by RobGoss on 2015-04-28
Glad to see you found a fix for this.

---

