---
title: "Installation freezes with a black screen after logo displays for a couple minutes."
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by pah2Ji5j on 2009-12-02
Originally I though the problem was with the .iso file I download and ran via Daemon Tools, or Daemon Tools itself causing a problem.

So I had a CD sent to me from the website, only to find out, I'm still getting the same problem.

I turn on the computer, boot from the CD, and get that menu to either boot Unbuntu live, or install, and the other options I can't remember at the moment.

I choose to install and then the screen goes black with a white Unbuntu logo that sort of fades in and out. (I'm sure you all know what I'm referring to if you installed it, just trying to be specific so you know at what stage this happens.)

Then after a few minutes, the logo disappears and the screen remains black for a countless amount of time.

Also, the lights on my keyboard (number/capslock/etc) go off at this point.

My computer is by no means slow, so "just wait" isn't or shouldn't be a response I'm expecting.

If you need any information about my computer I'm willing to provide so just ask.

It's a standard HP Pavilion. Model d5000t, if you want to look up the specs.

Thanks in advance.

---

### Post by u.b.u.n.t.u on 2009-12-03
Hi and welcome to the Ubuntu community!

Try running the CD live and see what happens.

---

### Post by pah2Ji5j on 2009-12-03
> **u.b.u.n.t.u said:**
> Hi and welcome to the Ubuntu community!

Try running the CD live and see what happens.

I get the same problem.
Only difference is this time I get a wall of text after the logo disappears.

Then after that just goes black. (Lit up, but black.)

Here's the "wall of text" I get when starting up live.
I would assume this is normal though when running it live, I've used other live CD's in the past.

[IMG]http://img101.imageshack.us/img101/4808/pc021779.jpg[/IMG]


I should also add that my CD drive becomes unresponsive when I press the open tray button.
Only after I press the power button (I have to hold it for it to shut down otherwise) then press the open tray will it open.

I'm not sure if any of this is useful but the help is appreciated.


Also, I noticed the time on my computer had been reset or actually moved forward 5 hours from it's actual time each time I reset the computer after it failed to load.

And the lights on the keyboard go off after I select from the menu, the same time the logo appears.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **pah2Ji5j said:**
> I'm not sure if any of this is useful but the help is appreciated.

The image is most useful!

I cannot see any error messages.

I have installed Ubuntu 9.10 via an ISO mounted by Daemon Tools.

I think there may be an option to adjust the screen resolution and graphics bit depth at the start of the Ubuntu installation. Have you tried setting those to a lower level?

What size is the HDD, how many MB does the GPU have, and how much RAM is installed?

At first glance it appears to be a hardware related issue.

If you see any text about something failing then that would be relevant.

---

### Post by pah2Ji5j on 2009-12-03
My hard drive is 500GB and I have about 50 partition to unallocated space for the install.
I figured that would be enough because I'm only just testing it out at the moment.


4096MB RAM
512MB GPU
the computers 64bit.

I think I should also mention that I have 2 monitors connected.
They are both on and work fine, but since you mentioned resolution, you think it might because an issue?

The picture I took was of my smaller monitor which the graphics card defaults to when starting up.

The bigger one is connected via HDMI to the same graphics card.

I'm gonna disconnect the HDMI cable and try it again and then update this.


*Edit*

I turned off the HDMI screen and everything was smooth.

I just now have a problem with the display so I'll make a post in the proper forum.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **pah2Ji5j said:**
> I turned off the HDMI screen and everything was smooth.

I just now have a problem with the display so I'll make a post in the proper forum.

Your GPU sounds more than adequate. Sounds like you isolated the issue, HDMI screen. With a default install one need look no further the VESA drivers and a question of compatibility.

---

### Post by pah2Ji5j on 2009-12-03
> **u.b.u.n.t.u said:**
> With a default install one need look no further the VESA drivers and a question of compatibility.

If you could elaborate a little it would be helpful.

---

### Post by u.b.u.n.t.u on 2009-12-03
With a default install one need look no further than the VESA drivers because they simply work and when considering proprietary drivers it becomes a question of their compatibility with the installed hardware, eg the GPU and monitor.

For example, ATI 9.11 drivers do not work with my ATI HD4850 GPU.

VESA are 2d drivers installed by Ubuntu 9.10 by default and they provide a range of screen resolutions based on the monitor.

Proprietary drivers provide 3d but may raise the question of compatibility, that is, will they actually work, as contrasted to VESA which will almost certainly work.

---

