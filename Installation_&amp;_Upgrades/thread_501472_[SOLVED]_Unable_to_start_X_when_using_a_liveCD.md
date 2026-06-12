---
title: "[SOLVED] Unable to start X when using a liveCD"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by Auax on 2007-07-15
I'm completely new to Linux, so I ordered a LiveCD to try it out and see if I like it. However, whenever I try to boot from the CD, it ends up telling me it can't start "X" graphical something and then covers the screen in text and gives me a command prompt that looks kind of like DOS. How do I make it work?

Thought maybe I should include some specifics, heh.

I'm trying to use Ubuntu 6.06 on an Acer Aspire 5100. Graphics card is a Radeon Xpress 1100, proccessor is an AMD Turion 64. Current OS on the system is Windows Vista Home Premium.

Thank you very much! I'm using Ubuntu now thanks to you.

Could you help me with another problem?

I'm trying to install off of the liveCD now, and I need to know what kind of filesystem I should make my new partition for Linux?

Woot! Thanks again.

Hmm... I have a widescreen monitor... but the only display options I have are 4:3, how can I change this?

I tried to edit it to include another resolution... and now I can't get it to load again. Help please?

---

### Post by merlinus on 2007-07-15
Try this --

At the command prompt:

```

sudo dpkg-reconfigure xserver-xorg

```

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

```

startx

```

-merlin

---

### Post by merlinus on 2007-07-15
Glad it worked.  Welcome!

-merlin

---

### Post by eapache on 2007-07-15
If you have vista installed, there should be a guided option to 'resize partition and use freed space'.

---

### Post by merlinus on 2007-07-15
> **Auax said:**
> 

I'm trying to install off of the liveCD now, and I need to know what kind of filesystem I should make my new partition for Linux?

ext3

-merlin

---

### Post by confused57 on 2007-07-15
You probably need to install the driver for your video card:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by merlinus on 2007-07-15
Did you try following the replies to your first post?

-merlin

---

