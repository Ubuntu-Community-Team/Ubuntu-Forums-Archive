---
title: "Request advice:  compiz (or similar) compatible with 16.04?"
date: 2016-05-27
forum: Installation &amp; Upgrades
---

### Post by m9ke2 on 2016-05-27
I have been nursing an old Pentium 4 box with Xubuntu for quite some time.

Just completed building a more powerful box, with a fresh install of Xubuntu 16.04

[COLOR=#000000]New box is an AMD-8320 8-core processor, ASUS GEForce GTX-960 graphics card.  I am running the NVidia proprietary driver v 361.42 

[/COLOR]Back in the days of Feisty Fawn and [COLOR=#000000]Gnome 2  i used to enjoy the Compiz stuff like wobbly windows.

I'd be willing to change drivers, but want to stay with Xubuntu.  I don't mind installing stuff like Compiz plugins as long as the new software is compatible with 16.04.

[/COLOR][COLOR=#000000]So here is my question:  Given the above hardware is it feasible[/COLOR][COLOR=#000000] to make my new system support special effects like wobbly windows, etc?

[/COLOR]

---

### Post by DuckHook on 2016-05-28
Feasible, yes. I've never tried it, because for me, the whole point in using Xubuntu is to keep a light system, but there is no conceptual reason why it wouldn't work. You would have to pull in compiz from the repos, but it sounds like you already know that.

Be aware that compiz deals with probably the most delicate and yet critical subsystem in your computer: the video subsystem. It has garnered a well-deserved reputation as a finicky, thin-skinned, easily upset little spoiled brat. Installing it may be a one-way street, as it may change so many system settings that uninstalling it may leave your system unstable. This is just a semi-educated caution but I have no real experience with either installing or uninstalling it since I use Ubuntu on which it is installed by default.

---

### Post by m9ke2 on 2016-05-28
Thanks for your reply DuckHook.  I agree with you on both points.  Although I am no longer nursing an old, under-powered computer, i decided to continue running Xubuntu for my 16.04 upgrade after installing Ubuntu and running that for a while.  It ran fine and performed well on my new box.  But so many settings are hidden and other GUI elements not quite to my liking  that I went back to Xubuntu.  

Compiz finicky?  Oh ya it is.  After much tweakinjg, I got i working reliably in older distros, but didn't pursue when I was babying that old computer.

I did not know Compiz is comes with Ubuntu by default now.  It might make more sense for me to figure out how to make the Ubuntu GUI and settings more to my liking than to try to kludge Compiz into working on Xubuntu.  I don't mind re-installing.

I am sure I am not the only one who would like to see more settings exposed in the GUI of Ubuntu.   Anyone have any suggestions?

---

### Post by DuckHook on 2016-05-28
If you were not happy with Unity the first time around, it is unlikely that you will be happy with it this time either. Xubuntu is an excellent flavour and I would encourage you to stick with what you like.

Consider spinning up a VM, installing Xubuntu on it and then compiz. You can try it out in a non critical environment before doing so permanently. Your new box certainly has the horsepower to run a VM properly.

---

### Post by grahammechanical on 2016-05-28
With the right utilities installed the user can have special effects on Ubuntu because Compiz is a compositing window manager. But Compiz does use more memory then window managers that are not also window compositors. This is why Xubuntu & Lubuntu work better on low specified hardware than Ubuntu does.

Compiz has been the window manger for Ubuntu for years now. Certainly since before I first installed Ubuntu in 2007. What we do not have installed by default.are utilities like Compiz Configuration Settings Manager (CCSM) which we can use to activate certain special effects and Unity Tweak which also is useful.

On the other hand, Ubuntu Mate seems to give the user endless possibilities for modifying the user experience. It gives the option of running with Compiz or some other non-compositing window manager.

Regards.

---

### Post by m9ke2 on 2016-05-29
Thank you DuckHook and grahammechanical for your posts.  And DuckHook I think you are right about Unity.   Think I will take grahammechanical's advice and check out Ubuntu Mate.   I will use the old computer I just upgraded from .   

I will keep this thread open for now and post back what i find out with Mate before marking this thread Solved.

---

