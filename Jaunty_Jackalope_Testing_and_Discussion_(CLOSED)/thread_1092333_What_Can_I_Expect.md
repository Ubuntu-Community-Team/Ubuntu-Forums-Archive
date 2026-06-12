---
title: "What Can I Expect?"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by CarlosinFL on 2009-03-10
Besides support for Ext4 file system in JJ / 9.04, what else can I expect to be upgraded in the spring? I heard they are moving away from the ugly brown color scheme to something more appealing.

---

### Post by philinux on 2009-03-10
[http://www.ubuntu.com/testing/jaunty/alpha5](http://www.ubuntu.com/testing/jaunty/alpha5)

One goal was faster boot times. And it does. Also from login to desktop is much faster than intrepid. For me on nvidia compiz is now really smooth and no messed up graphics when apps load.

---

### Post by CarlosinFL on 2009-03-10
Any improvements to battery life?

---

### Post by Jordanwb on 2009-03-10
> **philinux said:**
> [http://www.ubuntu.com/testing/jaunty/alpha5](http://www.ubuntu.com/testing/jaunty/alpha5)

One goal was faster boot times. And it does. Also from login to desktop is much faster than intrepid. For me on nvidia compiz is now really smooth and no messed up graphics when apps load.

I just installed 9.04 Alpha 5 on my machine sitting beside Gentoo on LVM. When it started up, the first thing I said was "Damn that was fast". I swear I got from grub to Gnome on like 10 seconds.

The terminal looks nicer too.

Damn that was fast.

---

### Post by crjackson on 2009-03-10
I'm praying for decent performance (compared to Intrepid) with the Intel x3100 video chip. I had to take Intrepid off my laptops due to poor video performance. I'm running Hardy on lappys and Intrepid on Desktops.

Dose anyone have any info on the Intel Video Performance?

---

### Post by Simian Man on 2009-03-10
You can expect the things that have been in Fedora for 6 months.

---

### Post by Nullack on 2009-03-10
Kernel 2.6.28, X server 1.6, gnome 2.26 plus allot of what red hat is doing

---

### Post by Jay_Bee on 2009-03-10
@crjackson:
Intel video in Jaunty is quite a mess unfortunately.
By default UXA is disabled and performance is poor, but you can enable UXA yourself in xorg.conf which then gives good performance and DRI2 (meaning compiz and 3d play nice together).
Unfortunately again... UXA has some bugs, there is an annoying transparency bug that caused me to disable all fading animations in compiz, and for me resume for suspend is broken (returns me to the login screen)..
Some users are also complaining that X crashes when UXA is enabled...
There is still time left for the things to improve, but right now it's not looking very good.

---

### Post by philinux on 2009-03-10
> **Carlwill said:**
> Any improvements to battery life?

To be honest, on my girlfriends lappy, Vista would say you got 2 hours on battery whereas ubuntu would say 1. Guess what, ubuntu reported it right. Vista was way wrong.

---

### Post by crjackson on 2009-03-10
> **Jay_Bee said:**
> @crjackson:
Intel video in Jaunty is quite a mess unfortunately.
By default UXA is disabled and performance is poor, but you can enable UXA yourself in xorg.conf which then gives good performance and DRI2 (meaning compiz and 3d play nice together).
Unfortunately again... UXA has some bugs, there is an annoying transparency bug that caused me to disable all fading animations in compiz, and for me resume for suspend is broken (returns me to the login screen)..
Some users are also complaining that X crashes when UXA is enabled...
There is still time left for the things to improve, but right now it's not looking very good.

Thanks - That's very disappointing. I guess I’ll be running Hardy at least until 9.10 comes out. I can’t tell you how sad this makes me. I’m getting more discouraged with 9.04 with every piece of new information received. Intrepid really let me down big time, and things aren’t sounding any better for me with Jaunty. I know things are moving forward, but it sure feels like Ubuntu is in reverse for me.

---

### Post by ghindo on 2009-03-10
> **Jordanwb said:**
> The terminal looks nicer too.What do you mean?

---

### Post by anibalojeda on 2009-03-10
> **Carlwill said:**
> Besides support for Ext4 file system in JJ / 9.04, what else can I expect to be upgraded in the spring? I heard they are moving away from the ugly brown color scheme to something more appealing.

Running 9.04 alpha 5 feel already like final on my laptop. Fast boot, compiz is smother than ever & for the first time everything feels fine! i first installed 32bit but i just moved to 64bit & it works perfect! i cant wait for the final version to replace my desktop with this new version.

---

### Post by Jordanwb on 2009-03-10
> **ghindo said:**
> What do you mean?

Well in 8.10 the letters were kinda thick. In 9.04 they're thin and smooth. Just an aesthetics thing.

---

### Post by anibalojeda on 2009-03-11
> **Jordanwb said:**
> Well in 8.10 the letters were kinda thick. In 9.04 they're thin and smooth. Just an aesthetics thing.

I know what you mean.. i think is the new GNOME.

---

### Post by gnomeuser on 2009-03-11
> **Jordanwb said:**
> Well in 8.10 the letters were kinda thick. In 9.04 they're thin and smooth. Just an aesthetics thing.

The default dpi setting is now more closely matched to the screen you have. If you might also want to try enabling subpixel hinting (System->Preferences->Look and Feel in the fonts tab).

---

