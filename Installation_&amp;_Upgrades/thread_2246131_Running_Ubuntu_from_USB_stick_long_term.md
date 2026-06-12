---
title: "Running Ubuntu from USB stick long term"
date: 2014-09-28
forum: Installation &amp; Upgrades
---

### Post by rafiqcombrinck on 2014-09-28
Hi All

I have installed Ubuntu 14.04 on one of my memory sticks (8Gb) which I intend on using on my work sponsored laptop. I was just wondering though, what would the cons be to running Ubuntu like this long term? 

I have a data partition on the laptop with all my "stuff" on it, so it will really only be the OS, apps and updates on the stick.

What say you?

Thanks,
R

---

### Post by Dennis N on 2014-09-28
My experience is that Ubuntu installed on a USB stick runs quite slowly compared to a HD install. usb 3 might alleviate some of that. There is a potential compatibility problem when moving from one computer to another. You can't be sure how well it will work as it is configured to work with the machine it was made on.

---

### Post by ajgreeny on 2014-09-28
I hope you made sure that grub was put onto the root of the USB and not to the intyernal hard disk or you will have problems if you want to boot Windows when the USB is not attached.

I agree with Dennis N that a USB installed system runs quite slowly, but as long as you have not installed any proprietary drivers for graphics etc etc, I don't think you should have problems moving to another computer, unless, of course, that second computer does need some particular driver that is not in your vanilla install.

---

### Post by nerdtron on 2014-09-28
I say no good on this. I have tried installing the full blown Ubuntu Sever on an 8GB USB Flash drive (SanDisk Cruzer Fit)  and all data is on a larger dedicated Hard drive. I performed tune-ups to reduced read/write on the flash drive to prolong its life. 

Changed the /var/log/ directory to tmpfs (to reduce writes)
Set no atime and nodiratime on the filesystem (to reduce writes)
I even removed the swap partition(to also reduce writes)

I have 5 machines with this experiment and the longest one survived a little over 3 months. Given that flash drives have limited read/writes and also some of my applications on the system are using other directories than just /var/log, the longevity is not really very long. Although you mileage may vary of course.

---

### Post by ubfan1 on 2014-09-28
C.S.Cameron has written up some tradeoff guides on USB installations.  Putting heavily written directories (like /tmp, /var/log, package download archive, browser cache, ...) into a ram disk does offer some benefits in speed and longevity.

---

### Post by sudodus on 2014-09-30
If you follow the tips by *nerdtron* and find the tips by *C.S.Cameron* and do not use the computer that intensively, the system might last for a long time. Some of the new USB 3 pendrives have both better speed and lifetime compared to standard USB pendrives. But be prepared that it might stop working, and in that case it would be handy to have a cloned copy.

See these links for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[URL="http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085"]
Link to USB 2 and USB 3 speed tests for installers[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it[/URL]

---

### Post by Maverick Meerkat on 2014-09-30
Hi there,
I actually did this... ran Ubuntu at work from a thumb drive.
I tried to make it as close to a full install as possible.
Yes, it ran slower, but it was still fun.
Where I ran into a problem was if it locked up on me, and I wasn't able to do a proper shut-down, it wouldn't work right afterwards.
I agree with those that mention wearing out a thumb drive, I think that's what I was doing to some of mine.

I noticed after some lock-ups, the screen would mention "casper" or something was not right.
So, after I set up a new thumb drive, I would save a copy of Casper ( it was visible when viewing contents of drive )
Then, if it got hosed, I would re-write Casper onto the thumb drive.
This bought me time, but it was best to redo the whole thing later.

I ran like this for over a year!
I would do it again if I had to.

Ultimately, I ended up popping in a 20 Gig hard drive as a second drive and doing a full install.
Not recommended in most work places, but I was okay to do so.
It was great for showing people who would ask about Ubuntu what a full install worked like.

Peace,

Rick

---

### Post by nerdtron on 2014-09-30
> I noticed after some lock-ups, the screen would mention "casper" or something was not right.
So, after I set up a new thumb drive, I would save a copy of Casper ( it was visible when viewing contents of drive )
Then, if it got hosed, I would re-write Casper onto the thumb drive.
This bought me time, but it was best to redo the whole thing later.

Casper file? I think that is used on a Live environment and not on a full install. If your are OK with a live environment, the lifespan of the thumb drive might increase since a live environment is optimized to run on temporary memory.

---

