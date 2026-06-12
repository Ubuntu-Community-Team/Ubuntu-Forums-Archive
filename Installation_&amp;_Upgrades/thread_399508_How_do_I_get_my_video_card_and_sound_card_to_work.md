---
title: "How do I get my video card and sound card to work?"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by Aro on 2007-04-02
Hi!

I'd like to switch from windows to linux (ubuntu or xubuntu), but there are a few obstacles that I need to elminate before I can afford the switch.

I have two hardware issues: Video card, Sound Card.

My sound card doesn't work because I have an integrated card (busted), and a PCI sound card that does work. I messed around with mixer settings and I figured out how to use the package installer to install XMMS (since xgime wouldn't load), and I had sound for a while.

I rebooted and now XMMS won't even load, and I can't get any sound at all.

I should probably mention that I'm running a live version of linux off a flash USB drive. If this is the reason I'm having problems loading XMMS, then don't worry about the above problem.  I don't understand why XGime won't load most of the time (it came prepackaged in this live distro, so I'm sure they did it right) 

I would like to know the proper way to switch from one sound card to another (when the primary is a busted integrated that you can't remove) What are ALL the things that I need to check/do?

Secondly, and just as important to me, are getting working video drivers. The last time I really tried to get into linux was years ago and I was running slackware 9 or 10. It was great except no matter what I read I couldn't find anything or anyone suggesting there were working radeon drivers for my card. 

Now, that card is long gone, and I have a new one, so I'm hoping there are drivers for this card.

I have a Nvidia Geforce 6600N (it's an agp not pci, can be SLI, but I only have one).

The sound card I can probably figure out on my own, but the video card I can't. I don't understand all the different video thingies...i mean...that X11 Xorg stuff...(or whatever it evolved into now) I also know that nvidia/ati generally don't release any linux help/drivers, so do I have to look for a third party driver? 

Where would I look to find all that information (how to install video drivers, where to find video drivers specific to my card/distro, and anything else I need to get openGL and other 3d acceleration to work)?

I'm sorry about the long mail, but it does reflect how confused and lost I am. 

Thanks for reading, and thanks for any help

---

### Post by sammyd253 on 2007-04-02
I don't think your card can be run in SLI.  I'm pretty sure SLI is only supported with PCI-e, not AGP.  As for drivers, I would try going to Nvidia's website and downloading the newest drivers off of there.  Supported graphics cards are supported in their documentation.  They also have legacy drivers for older cards.  I would imagine that these drivers would support your card.

---

### Post by Aro on 2007-04-02
I took your advice and checked the Nvidia site. I didn't think they offered support for Linux, but I guess they do! Thanks :)

I found my way to here
[http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

---

### Post by Aro on 2007-04-02
I have a problem =p

It wants me to shut down X windows and just run a command prompt which is where I'm supposed to run the nvidia package.

But...I don't know how to shut down to a command prompt...I only know how to open a command prompt while in X windows.

In windows I would reboot and hit f8, then choose dos prompt.

How would I do that in Ubuntu?

---

### Post by Aro on 2007-04-02
Note: Sound problem is no problem. 
I gave up trying to run linux off a flash drive and installed it. I'm not having sound problems now (especially since I know how to switch from my default card to my other sound card in the mixer...it was really simple actually)

So, I'm down to the video card now ;-)

I also plugged in my laser printer...
How do I get it to work? Does someone have a ubuntu/linux printer install howto I could read? :-)

I tried logging out of ubuntu and then changing my session to the failsafe terminal window...but when I ran the nvidia installer it told me I still had X-Windows running =/

---

### Post by sammyd253 on 2007-04-03
You said earlier that you have an Nvidia 6600N AGP card.  Can you double check this?

Here is a list of all supported graphics cards by Nvidia:
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html)

Once you know your card is supported by these drivers, do the following to install your Nvidia drivers:  (I am assuming you are using 6.06 LTS or higher)

1)  System --> Administration --> Synaptic Package Manager
2)  Settings --> Repositories
3)  In Software Preferences, click on Add
4)  In Edit Repository, check the Restricted copyright box
5)  Click ok, then say yes to reloading the package database
6)  Search for "linux-restricted-modules"
7)  Download the proper restricted modules based off of your kernel
8)  Search "nvidia"
9)  I would assume that you will want to install nvidia-glx, I don't think your card is considered "legacy", but double check the supported card list I gave you a link to
10)  Make sure you have installed these packages, then once you're done, exit Synaptic Package Manager
11)  Hit Alt+F2, then type sudo nvidia-xconfig
12)  Restart Ubuntu


Hope this helps, please use this advice with caution.  Misconfiguring your graphics cards could render your Ubuntu setup unusable.

---

### Post by Aro on 2007-04-08
Hey, I solved my problem a while ago. I thought I made a final post but I guess I was wrong.

What I did was this:
I edited the repositories so I could find universe/multiverse stuff...which includes nvidia's drivers.

I installed the drivers after making sure my 6600 is included in the main driver package and not hte legacy package. 

I installed the drivers then rebooted.

I had to do one final thing, however...

I had to go to the video configuration file...i forget where it is though....the xorg file under /etc? 

Anyway, in that file search for "driver"
you'll find something like driver = "nv" which needs to be changed to driver = "nvidia"

and then i rebooted one final time, and everything worked! 
thanks all :)

---

### Post by Aro on 2007-04-09
*deleted double post*

---

### Post by sammyd253 on 2007-04-13
Glad you sorted your issue.  I'm sure many more users will encounter the same thing, this will be a good reference point for them.

---

