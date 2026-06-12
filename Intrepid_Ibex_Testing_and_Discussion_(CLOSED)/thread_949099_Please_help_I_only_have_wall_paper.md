---
title: "Please help I only have wall paper"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by thrasher6900 on 2008-10-15
I just install Intrepid last night and I don't have a desktop anymore.

I just have walpaper and my keyring to connect to my wireless pops up and works.

Right clicking doesn't do a think either.

All there is is the wallpaper and a mouse arrow.

I've tried everything I could think of with reinstalling the desktop and using aptitude install -f.

I'm fairly a noob at this, so is there a way to fix this?  Can I revert back to 8.04?

I have an intel computer. It's a compaq presario c552 notebook is that helps any.

Thank you all ahead of time.

Cheers

---

### Post by Merovius on 2008-10-15
I had the same results after installing an ATI card and trying to use the newest ATI driver. The way I got around it so I could work on the problem was to restart in recocery mode and select the option to try and repair x... Then the system would boot into the desktop but without the restricted ATI driver. (no 3d) 

After a few runs of the update tool and selecting the ATI driver in the hardware drivers applet it started working normally.

---

### Post by Merovius on 2008-10-16
After rebooting I'm back to just wallpaper again..:confused:

---

### Post by tkiesel on 2008-10-16
I faced that same issue on upgrading to 8.10 the other day.

At the login screen (GDM) click the "Sessions" button and choose Gnome.

Then login.  If it asks about making this your default, say yes.

That fixed my wallpaper and mouse cursor problem.

---

### Post by jerrylamos on 2008-10-16
Two suggestions.  I get similar problems on my IBM Thinkpad R31 where booting either Ubuntu CD Live or install ends up in wallpaper or black screen.

1.  Try Xubuntu CD Live without installing it. It doesn't use Gnome desktop or compiz.  Compiz is code for eye candy special effects which it does (my words) by fancy tricks with the graphics hardware and software.

If Xubuntu works, then your problem with Ubuntu could be Gnome desktop or compiz.

2.  If you have Ubuntu from install or upgrade, then boot in recovery mode and select command prompt.  Do:
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot.

If that works then the problem was compiz.  All you'll lose is fancy fade effects, splashes, ... but no function.

Jerry

---

### Post by Merovius on 2008-10-16
I just told the hardware drivers app to enable the ATI driver. I rebooted. It works fine. I wish it would make up it's mind... I'm going to reboot and see what happens.

Then I will try some of the suggestions.

---

### Post by Merovius on 2008-10-16
It rebooted and the driver is working. I also noticed the catalyst control center in applications. Don't remember seeing that there before.

Maybe it finally stuck. Time will tell.  Thanks to all

---

### Post by Merovius on 2008-10-17
Uh, no. Next morning I boot into just the wallpaper again. Drivers work why won't they stay that way?

---

### Post by jerrylamos on 2008-10-17
Ubuntu Gnome uses compiz to get eye candy and fancy effects by playing tricks with the graphics drivers & hardware.  That's a tall order since there are so many different drivers & hardware out there so the compiz code is famously buggy and constantly under revision.  They fix it for one driver/hardware and it fails for a different driver/hardware.  For me, Alpha 3 ran.  Alpha 4 compiz failed.  Alpha 5 ran.  Then they updated compiz, failed again.  Alpha 6 fails.  Beta fails.  Unless I remove compiz.

Your easiest test is to try Xubuntu CD Live which is an Ubuntu that doesn't use the Gnome desktop with the fancy appearance code compiz.   

If that test works, then likely compiz is the culprit.  I can get Ubuntu to run (like right now on latest daily build 20081016) only by removing compiz as in my post earlier.

Jerry

---

### Post by Merovius on 2008-10-17
I'm starting to think thats the way I will have to go. At least until everything is out of Beta.

I had a lot of updates this morning. Three of them had to do with fglrx and ATI maybe that will change things.

---

### Post by klange on 2008-10-17
I can confirm this on my desktop. Manually starting my WM, followed by gnome-panel and Nautilus yielded a working desktop, but Nautilus doesn't seem to be handling my desktop.

---

### Post by Merovius on 2008-10-17
Removed Compiz and got the driver to install. Desktop comes up (twice anyway..) 

Now TVTime doesn't work.

I'm thinking about installing Compiz after the driver to see if that makes a difference.

---

### Post by Merovius on 2008-10-17
Installed Compiz after the new ATI driver and was able to reboot to a functional desktop twice.

TVTime still refuses to show video. The first couple times the driver was installed (after Compiz) and wouldn't stick TVTime worked but was a little jerky. Now the driver seems to be working OK but TVTime won't.

:confused:

---

### Post by thrasher6900 on 2008-10-17
Well what I did was log in and then hit ctrl alt F1 to get a console and installed **scrollkeeper** and** nautilus**.

It seems that the beta version doesn't install those as of yet automatically.

So here's what you do.

```
sudo apt-get install scrollkeeper
```Let it run it's course and answer yest to all questions

Then you need to install nautilus

```
sudo apt-get install nautilus
```I hope this helps ya'll:)

---

### Post by Merovius on 2008-10-18
Well after the scrollkeeper nautilus idea failed to have an effect, I have decided that ATI is still not ready for prime time.

 I reinstalled my Nvidia 6800XE and enabled the proprietary driver. Turned on desktop effects and all works fine the first time around.

TVTime is fine now too. Guess I'll have to wait for the next ATI driver or two and try again then. 

Thanks again for all the help and ideas.

---

