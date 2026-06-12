---
title: "Ubuntu 11.04 HP DM3 no trackpad scrolling"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by wv25m on 2011-05-01
Just did a fresh install of 11.04 on an HP DM3 laptop, everything works except the trackpad scrolling feature and the button to lock out the trackpad functionality.  Any fixes on this?  Otherwise this is a brilliant OS.

---

### Post by wv25m on 2011-05-02
Also experiencing jumpy/out of control pointer after resuming from sleep mode.  Any help appreciated.

---

### Post by kevjames3 on 2011-05-03
Same issue here (HP Pavilion dm3).  This is the third time I have had to reinstall the OS :(  Just want the mouse to work and I would be all set.  If any specs are needed, please ask

---

### Post by mr.norrime on 2011-05-03
Hello- I'm having same issues on an HP DM3.  Scroll does not work on trackpad.  Pointer is out of control when coming out of sleep- however this problem goes away after about a minute.

Otherwise it looks good and I'm looking forward to exploring the changes.

---

### Post by kevjames3 on 2011-05-04
Workaround: [http://mitchtowner.net/?p=840](http://mitchtowner.net/?p=840)

Apparently, this was updated in the linux kernel headers which will probably released soon

---

### Post by jnkramer on 2011-05-09
Hey everyone,

This worked for me on my HP Dm3-1039wm.  With a fresh install of Natty Narwhal.

sudo echo “options psmouse proto=imps” > /etc/modprobe.d/options

After that you’ll will need to either reboot or manually reload the psmouse kernal module.

The above change also fixed my trackpad craziness after waking the laptop from sleep.

Found it on this website. [http://thf.org.uk/ubuntu](http://thf.org.uk/ubuntu)

---

### Post by kevjames3 on 2011-05-10
I am unsure of what the "options" program is.  In addition, in modprobe.d there is no file called "options".  Help me out?

---

### Post by jnkramer on 2011-05-10
What this command does is actually create a file in /etc/modprobe.d called "options" with the text "options psmouse proto=imps" (no quotes)

If you are having trouble with the command it can also be inputted like this, in Terminal type:

sudo -s

It should ask you for your password, then type:

echo "options psmouse proto=imps" > /etc/modprobe.d/options

Then, if your ready, and ok to reboot, type:

reboot

Hope that helps.

---

### Post by 74kumi on 2011-12-12
I am having the same error with a hp DM3z-2000 ubuntu 11.10 updated daily. I tried the > sudo echo &#8220;options psmouse proto=imps&#8221; > /etc/modprobe.d/options but it did nothing. Does anyone have any new information on this topic?

---

