---
title: "[SOLVED] Ubuntu Minimal CD installation fails"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by fredbird67 on 2013-06-10
I've got an idea for a Ubuntu-based Linux distribution I'm really wanting to put together during my week off from work.  I'm starting with a Ubuntu mini base (available at [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")), version 12.04, which seems to install just fine.  But after I've removed my installation USB and my plop CD and reboot the thing after installation, I get...nothing.  All there is on the screen is a white blinking cursor in the top left-hand corner and I can't type anything into it.  I did ask for it to install GRUB onto the MBR, and the installation itself seemed to go just fine.  What could I possibly be doing wrong?

Thanx in advance,
Fred in St. Louis

---

### Post by papibe on 2013-06-10
Hi fredbird67.

Did you do use the command line installation option? If so, my first guess would be that an old bug is still around. Once you get to the black screen, wait a few seconds and press Ctrl+Alt+F1. That should take you to a text mode console.

Let us know how it goes.
Regards.

---

### Post by Bashing-om on 2013-06-10
[COLOR=#000000]fredbird67; Hi !

Not much to go on huh ? ...Is bios even finding grub ?
what results from:
cold boot, as soon as bios screen clears, depress and hold the shift key ->
do you get the grub boot menu ?
[/COLOR][INDENT][COLOR=#000000]
gotta start somewhere, basic is good

[/COLOR][/INDENT]

---

### Post by fredbird67 on 2013-06-17
Sorry for the delay, y'all.  Been out of town the last several days due to an unforeseen family emergency.

Anyways, no joy on either of y'all's suggestions. ](*,)  I'm tempted to start with a Lubuntu installation, even though I plan to swap out LXDE for Xfce (LXDE just doesn't feel as complete as Xfce, IMHO).

---

### Post by Bashing-om on 2013-06-17
[COLOR=#000000]fredbird67;

Food for thought: As you like xfce4 ... and have a bit of knowledge of ubuntu;
How bout starting with the minimal install and adding exactly what you want ?

I am running a rather outdated high end box ...started with 13.04 minimal, installed xorg, xfce4 and google-chrome as my base system.
All I can say is : "I like it !"
It is fast, lean and mean - no frills - just what is necessary and only what I want on my operating system.

This route does take being totally aware of what you want your operating system to be.

On the other hand // old Sempron AMD system ubuntu // -> My wife had expressed that only death would separate her from her beloved 10.04 ...flash, facebook and youtube -> dualbooted her into 13.04 lubuntu ...installed google-chrome (pepper for flash) ... introduced her to it ..
much faster as lubuntu 13.04 than ubuntu 10.04 ... she is now a happy camper with lubuntu 13.04 !
[/COLOR][INDENT=3][COLOR=#000000]
There are many many options, depends on hardware and what you want[/COLOR][/INDENT]

---

### Post by fredbird67 on 2013-06-18
Well, I learned something about this whole ordeal -- Ubuntu minimal installations cannot be done from a USB stick -- they HAVE to be burned to a CD.  And that's exactly what did the trick.  Just to make sure it would work consistently, I booted it a total of 3 times just to make sure, logged in, issued a "sudo reboot" command twice, and then, on the last time (since it's so late right now and I need to go to bed), I issued the command "sudo shutdown -h now" -- and it worked like a charm each and every time.

How I found out about this was, on [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD"), they have a line on that page that I had been repeatedly missing:  "Unlike other iso images available on this site, this image mini.iso does not work with the USB stick installation method."  Boy do I feel like such an idiot for not catching that previously...but it's working perfectly now. :)

---

### Post by Bashing-om on 2013-06-18
[COLOR=#000000]fredbird67; 

Pleased you got it worked out ! .. I have also learned to "read" for comprehension ... each detail can be important.

Please mark this thread as solved = aids others seeking solutions and helps keep the forum tidy:
 [/COLOR]Interim method:> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT=2]
Will see ya next time -> enjoy

[/INDENT]

---

### Post by fredbird67 on 2013-06-18
I thought I already did -- and, I thought it already showed up as such in this thread...and looking up there, yes, it does show as solved.

---

