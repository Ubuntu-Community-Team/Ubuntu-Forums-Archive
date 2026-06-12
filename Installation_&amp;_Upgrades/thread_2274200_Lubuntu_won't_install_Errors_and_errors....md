---
title: "Lubuntu won't install: Errors and errors..."
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by maik4 on 2015-04-18
Hi! I'm new at the forum! I'm here because I've got frustated by Lubuntu. It won't install!

I tried makin a bootable USB with UNetbootin, Rufus and other things. But I only get the same error when I press Enter for installing or trying it:

"No irq handler for vector" error and "Assuming drive cache: write through" error.

When those errors appear, It appears a little red rectangle on the top left corner. And nothing more happens.

It's a old PC I try to take again to life. I tried to install Slitaz but Firefox, flash and audio are conssuming me...

The PC specifications are:

1GB RAM, Intel Celeron D, with a 165GB HDD.

Please help me I will cry... :(

---

### Post by egeezer on 2015-04-18
The iso for current versions of Lubuntu is a hybrid, so it can be written directly by dd'ing to the USB drive.  There is also a relatively new utility called mkusb that promises a safer version of the same technique.   [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by mörgæs on 2015-04-19
Have you tried installing using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by maik4 on 2015-04-20
I can't use mkusb because I don't have Linux installed...

I will try the alternate ISO! I didn't...

Now I installed 12.04 but had problems with IRQ handler after installing a controller, so I will try the alternate ISO right now!

---

### Post by maik4 on 2015-04-20
I tried Alternate ISO but I can see only some lines like scratches in the screen... I don't know why...

I'm thinking about leaving it and stay at 12.04, because is there where the only problem I got is when watching videos in youtube, I have no sound...

---

### Post by mörgæs on 2015-04-21
Lubuntu 12.04 is a problem in itself, because it's unsupported. 

Let's take a closer look at the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by mattharris4 on 2015-04-23
> **maik4 said:**
> I tried Alternate ISO but I can see only some lines like scratches in the screen... I don't know why...

I'm thinking about leaving it and stay at 12.04, because is there where the only problem I got is when watching videos in youtube, I have no sound...

You will likely run into the no sound problem with the current version as well.  It is a bug involving Alsamixer installing muted.  Here is how to fix that:  [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/) , page down to section two "Check Alsa Mixer"  I will attempt to reiterate the instructions below.  Of course check the volume control accessible from the GUI (lower right corner where a speaker and three curved lines is shown, click the icon once) but this is likely not the issue unless you have messed with it before reading this post (unmute if needed).

1.  Get into a terminal by clicking the blue box in the lower left corner, select System Tools, then select UXTerm.

2.  Enter "alsamixer" (without quotes) and press Enter.

3.  If the letters "MM" is under the bars for Master, Headphon and Speaker (or any of these three), use the left and right arrow keys to place the cursor over the "MM" and increase volume to about 90 with the up arrow (the down arrow decreases volume).  The "MM" will change to "OO".  Do the same for other "MM" entries under either Master, Headphon and Speaker.  Exit Alsa Mixer by pressing Esc.  Test your sound by playing a YouTube video or CD.  If you don't have sound after this, click on the link in this post and read the article, it has other glitches that sometimes show up in a Lubuntu install (the article discusses Ubuntu but it applies to any Canonical OS).

---

### Post by maik4 on 2015-04-26
I just can't do that morgaes (sorry, can't type it like you have...) It tells me only what this command can do.

I tried Elementary 0.2, because every ubuntu related to 14.04 just tell me that error I mentioned in the first post.

---

### Post by mörgæs on 2015-04-26
Did you copy and paste the command or try to type it?

---

