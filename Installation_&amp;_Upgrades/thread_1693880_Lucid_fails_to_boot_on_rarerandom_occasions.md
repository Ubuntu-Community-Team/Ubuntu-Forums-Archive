---
title: "Lucid fails to boot on rare/random occasions"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2011-02-23
Why is it that about 98 to 99% of the time my computer will boot to Ubuntu/Lucid just fine but on rare / random occasions after seeing the initial BIOS boot screen and initial cursor just after initial BIOS boot screens, the video will just go BLANK, i.e. does not boot to Ubuntu desktop ?

If I then do ALT,CRL,DEL sequence the SPLASH screen is displayed on the monitor and the system then reboots and then goes thru the complete boot process all the way to the desktop just fine.

Why this occasional failure to boot completely to the desktop ?

Thanks.

---

### Post by Rubi1200 on 2011-02-23
What graphics card do you have installed?

```
lspci | grep VGA
```

---

### Post by wpshooter on 2011-02-23
> **Rubi1200 said:**
> What graphics card do you have installed?

```
lspci | grep VGA
```

I am not home right now, so I can not run the command but it is an ATI Radeon 9600.

Thanks.

---

### Post by Rubi1200 on 2011-02-24
Definitely sounds like a graphics issue.

You could try reconfiguring xorg from either the terminal or the command line in recovery mode:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by wpshooter on 2011-02-24
> **Rubi1200 said:**
> Definitely sounds like a graphics issue.

You could try reconfiguring xorg from either the terminal or the command line in recovery mode:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

What does -phigh accomplish & can you explain why this might possibly solve the booting video problem ?

Thanks.

---

### Post by Rubi1200 on 2011-02-24
From your original post, the description of the situation suggests a video issue. I have had something similar happen though my laptop uses Intel graphics.

```
dpkg-reconfigure -phigh
```

The -phigh is used to select the default values for everything except screen resolution.

From the man page:

> **-p**_value_, **--priority=**_value_
Specify the minimum priority of question that will be displayed.
[http://manpages.ubuntu.com/manpages/maverick/en/man8/dpkg-reconfigure.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/dpkg-reconfigure.8.html)
Rather than having to select yes at every prompt, this takes the defaults except resolution as I mentioned above.

Don't forget, you are backing up the xorg.conf not removing it. If you want to make a copy beforehand and put it somewhere safe; also an option.

---

### Post by wpshooter on 2011-03-06
> **Rubi1200 said:**
> Definitely sounds like a graphics issue.

You could try reconfiguring xorg from either the terminal or the command line in recovery mode:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

When I issued the first command shown above I get a response that No such file or directory found !!!!

Thanks.

---

### Post by Rubi1200 on 2011-03-07
Do you have the same issue when booting older kernels?

Perhaps take a look here for something that can help:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by wpshooter on 2011-03-07
> **Rubi1200 said:**
> Do you have the same issue when booting older kernels?

Perhaps take a look here for something that can help:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Rubi1200:

Thanks for your reply and the info.

If you mean by "older kernels", do I have this boot/video hanging problem when I am using the older versions of Ubuntu, then the answer is NO, that is, if I go all the way back to I think Jaunty, then this hanging problem does not seem to occur.  But if I use any of the newer versions of Ubuntu that have been released since Jaunty, yes I have the problem.

I am sort of getting tired of fooling with this.

Do you think I would be better off just scrapping my ATI video card and just buy an Nvidia based card and see if that will cure these problems.  The reason that I have not already done that is because I am just wondering if there is a remote chance that the problem is not with the video card at all and is perhaps either a problem with some other hardware component, such as either the hard drive, the APG port on the motherboard, the processor or memory (yes, I have run memtest and the memory "seems" to be fine).

I have just been hesitatant to buy a new video card just to later find out that it is some other hardware component or even some trash in the Ubuntu O/S that is the real cause of the problem.  

What are your thoughts ???

Thanks.

---

### Post by Rubi1200 on 2011-03-07
Hi wpshooter,
this is my take on the situation, though other users may offer different perspectives.

I would try first installing the proprietary fglrx driver for your card and see if that makes a difference.

If you still want to go ahead and get an NVIDIA card, be aware that they can also cause problems though possibly less than ATI Radeon.

Just out of curiosity, you said in your original post that this issue occurs only rarely/randomly. Do you also boot into other operating systems/versions of Linux?

If yes, does the problem also happen there?

---

### Post by wpshooter on 2011-03-07
> **Rubi1200 said:**
> Hi wpshooter,
this is my take on the situation, though other users may offer different perspectives.

I would try first installing the proprietary fglrx driver for your card and see if that makes a difference.

If you still want to go ahead and get an NVIDIA card, be aware that they can also cause problems though possibly less than ATI Radeon.

Just out of curiosity, you said in your original post that this issue occurs only rarely/randomly. Do you also boot into other operating systems/versions of Linux?

If yes, does the problem also happen there?

My past experience with trying to download and install these video drivers from the ATI website has given me the impression that doing so is probably just a waste of time.  When I have tried this in the past, what I came out with was worse than what I had with the stock Ubuntu installed driver.

No, I only have 1 O/S installed on the computer at one time.  I do NOT use M/S windows.  I have tried installing Ubuntu versions on this computer (just 1 at a time) all the way back to I believe Jaunty and Jaunty is the only one that seems to not have hanging problem.  All of the newer ones seem to have problems with the boot hanging.  Like I said the machine might boot 25 to 50 times in a row and not have this problem but then again sometimes it might have it 1,2 or 3 boots in a row.  Just rare and random.

I think I am going to go to pricewatch and see if I can find a good Nvidia based AGP card.

Thanks.

---

### Post by Rubi1200 on 2011-03-07
Sounds like a good plan. You should probably do some research first on what cards work best with Ubuntu before buying.

Here is some more information for you:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Good luck :-)

---

### Post by wpshooter on 2011-03-07
> **Rubi1200 said:**
> Sounds like a good plan. You should probably do some research first on what cards work best with Ubuntu before buying.

Here is some more information for you:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Good luck :-)

For $40 bucks, I am not going to waste much more time on this.

I just ordered a PNY GeForce 6200 AGP card from Best Buy.

I am crossing my fingers that that is going to do the deed.

Thanks.

---

