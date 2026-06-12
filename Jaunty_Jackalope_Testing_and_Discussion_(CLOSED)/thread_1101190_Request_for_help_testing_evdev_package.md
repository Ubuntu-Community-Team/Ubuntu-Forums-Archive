---
title: "Request for help testing evdev package"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Jeff250 on 2009-03-20
*Update:  Early instructions forgot to say to restart X or your computer after upgrading the package.  They now are reflected to say this!*

Hi, some of us from launchpad are testing a new evdev package for inclusion into jaunty, and we need some additional testers to see if the patch can be included, so we would appreciate any guinea pigs, err, I mean volunteers that we can find to test it. ;)

Evdev handles things like keyboard input for X, and our current understanding is that the current evdev package in jaunty has a bug involving setting the key press repeat rate.  Your system has a hardware repeat rate, but X also does its own internal 'soft' repeating, and this is what is changed when you change your key repeat rate in, say, the gnome preferences.

It appears that for many people, the hardware repeat rate is conflicting with X's internal soft repeat rate.  Evdev is supposed to ignore hardware repeating, but it does not appear to be doing this for many people, and this makes setting the soft keyboard rate not possible for many of us.

If you could, try out the following:
1. Open gnome keyboard preferences (or similar preferences for your desktop environment)
2. Move the delay slider all the way to the right (longest delay) (we just need it to be longer than the hardware delay so that the hardware repeat kicks in first)
3. Move the rate slider all of the way to the left (slowest rate)
Test the repeat rate by holding a key--once the keys begin repeating, notice how quickly they repeat (note that we are not interested here in the delay it takes before the first key start repeating, just how quickly they repeat once they start repeating).  If you don't experience this bug, they should repeat very, very slowly.  If you do experience this bug, they will repeat at a fairly normal rate.

Then add these repositories:
```
deb http://ppa.launchpad.net/jeff250/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/jeff250/ppa/ubuntu jaunty main
```

To add the apt key for this repository, type:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA6CCFC7
```

Then make sure to upgrade xserver-xorg-input-evdev to version 2.1.1-1ubuntu4~ppa1.1 using apt-get or synaptic.

Next restart X or your computer.

Now repeat the test above.  Also, play around with key repeating and other things in your desktop for a bit involving the keyboard.  If you experienced the bug earlier, is it fixed now?  Regardless of if you experienced the bug earlier, do you have any new problems that weren't there before you upgraded to this package?

If you have questions about these instructions, please post them here in this thread, but please post your results here on the Launchpad page:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/345397](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/345397)

If necessary, downgrade instructions:

Select the xserver-xorg-input-evdev package in synaptic
In menu, go to Package -> Force version...
Then select the version you want to downgrade to.
Apply this change, restart X or your computer, and you should be back to normal.

---

### Post by Jeff250 on 2009-03-20
Hi all, I didn't mean to discriminate against those who don't have Launchpad accounts.  I received some very positive results via PM from someone who didn't have a Launchpad account, and that is perfectly fine.  You can also post them in this thread as well.  I was hoping to get a larger response, but I won't bump the thread beyond this. :) Anyone who can help us test this, please do!  Thanks in advance.

---

### Post by racmar on 2009-03-23
Jeff,

THANK YOU, THANK YOU, THANK YOU.

I have a firefly mini usb remote, and it has been sending double keypress events for a LONG time.  I have a new machine that needs the newer Intel drivers, and thus evdev.  I have been looking for this solution for months!  Again, THANK YOU.

p.m. me, and I'll *definitely* send you a six pack of your favorite beverage!

-Rob

---

