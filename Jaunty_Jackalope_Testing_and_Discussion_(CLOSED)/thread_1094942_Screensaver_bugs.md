---
title: "Screensaver bugs?"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MadsRH on 2009-03-13
[SIZE="5"]Hi[/SIZE]
Here's the story:

Today I did I ran an update (*alpha 5 -> alpha 6*) and left the computer for 15 minutes. When I came back, the *AntInspect* screensaver was activated. To return to the desktop I tried moving the mouse, clicking the mouse buttons and hitting almost every keyboard key, with no luck - the screensaver keept running uninterrupted.
After a cold boot, I went into **system -> preferences -> screensaver**, but before I could try anything the window froze.

[COLOR="DarkRed"]Has anyone had similar experiences?[/COLOR] :confused:

I guess there's actually two bugs here.

1. The actual freeze...
2. Why is the default Ubuntu screensaver AntInspect and not something like Floating Ubuntu? Seems kind of stupid

---

### Post by MadsRH on 2009-03-13
I guess since I'm using nVidia driver (180.35) this could be related to this bug: [https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/335903]("https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/335903")

---

### Post by rburkartjo on 2009-03-13
mads yes i have also had problems with the screensaver i can get only floating ubuntus to work properly and other screen saver just locks up. here is a link that might help. just set back to floating ubuntu
If you have the gnome configuration editor isntalled (package name gconf-editor) you can run it to change the screen saver setting without actually invoking the screensaver applet that is locking your system up.

If you have the gnome configuration editor isntalled (package name gconf-editor) you can run it to change the screen saver setting without actually invoking the screensaver applet that is locking your system up.

The location of the setting you need to change is in apps / gnome-screensaver. In the right-hand pane of gconf-editor just change the "themes" setting from whatever it currently is to empty square brackets, like this:

[]

That sets you up with the blank screensaver. Then you should be able to open the screensaver applet and choose another screensaver -- if you feel like messing around with it any more.



I think the lockups caused by certain screensavers are indicative of video driver issues. Several of the screensavers will lock one of my laptops when its using the standard drivers. It has an nVidia Quadro Go 1400 card. If I install the restricted drivers, then then screensavers work without locking the system up.

---

### Post by Nyoro on 2009-03-13
Yes, I am having the same problem for about 2 weeks now.

What I do to get out of the problem, is to push CTRL-ALT-F3 to get a console. Then I log in and kill both the gnome-screensaver process, and the specific process that runs the actual screensaver, for instance glslideshow.

I guess if you want to disable the screensaver you can do so with gconf-editor. Run a terminal and run gconf-editor, then browse to apps/gnome-screensaver and uncheck idle_activation_enabled. I haven't tested this, but I'm guessing that this will at least disable the screensaver.

As to what is making the screensaver lock up, I have no clue, but it seems to be connected to running opengl applications, as gnome-screensaver also becomes unresponsive when previewing the screensavers. However, it does not seem like it actually crashes (the window doesn't go dark)..

---

### Post by Nyoro on 2009-03-13
I'm using the nvidia 180 driver for my 8800GTS, and I'm seeing the problem.

---

### Post by MadsRH on 2009-03-13
Thanks for all the help - I'm still on Intrepid (just testing Jaunty, so I won't be messing around with gconf-editor ;-))

Has anyone reported this bug?

---

### Post by Nullack on 2009-03-13
Try 180.37

---

### Post by Nyoro on 2009-03-13
How do I install 188.37 without breaking stuff? 

@Mads
If you have the time, you could check if theres any existing bugs and post one, let us know if you do, I'll add what I have to add.

(Sorry, lazy & in a hurry)

Regards

---

### Post by Nullack on 2009-03-13
Uninstall all repo nvidia drivers including VDPAU
Exit to GDM
In a tty, do sudo /etc/init.d/gdm stop
Then change dir to where you downloaded 180.37
sudo sh NVI (tab) to autocomplete the install shell script
Accept licence, compile your own, dont let nvidia change your conf
sudo nano -w /etc/X11/xorg.con and change the driver to nvidia
sudo /etc/init.d/gdm start

Now your boiling with gas :)

Remember any kernel changes and youll need to rebuild the nvidia kernel module.

When it comes into the repos use the --uninstall flag on the nvidia shell script to turf it out.

---

### Post by Nyoro on 2009-03-13
I think I managed to install 180.37, as per Nullacks instructions. Thanks.

However, now my xorg.conf seems borked. 

When I restarted gdm, it had a problems as GDM had not relinquished the display for some reason. So i allowed it to start on another display, but it couldnt load X, and offered to reconfigure / roll back etc. I tried each, but the results are:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Also tried a dpkg-reconfigure x-server.xorg.

The backup is empty too.:(

Arg, I really hate editing xorg.conf, not clear to me what to put in there and what should be autodetected.

I guess the restricted driver config application cannot see "handrolled" nvidia drivers either.


***EDIT****
I rolled back the original driver from the repos, screensaver is not important atm.

---

### Post by MadsRH on 2009-03-14
> **Nyoro said:**
> ...@Mads
If you have the time, you could check if theres any existing bugs and post one, let us know if you do, I'll add what I have to add...Regards

Sorry, just got back. Haven't had any time to report anything :-({|=

---

### Post by rburkartjo on 2009-03-20
since last updates sceensaver seems to be working correctly

---

