---
title: "Ubuntu 7.1 Installation Help Please"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by ejohnson442 on 2007-11-09
I tried to upgrade to Ubuntu 7.1 from Ubuntu 6.4.  I thought things went well but a few days later Ubuntu wouldn't load.  I've downloaded and burned a CD for installation of Ubuntu 7.1.  However, I am dual booting with WindowsXP which I don't want to inadvertently destroy.

So what steps should I take to get up and going?  I'm really excited about this installation but unfortunately I'm also a newbie to Linux but not computers.  Any help would be well appreciated.


Thanks...

---

### Post by MikeMLP on 2007-11-09
First make sure you've backed up all your data on the old install.  Then, boot up using the live cd.

When you get to this screen:
[http://content.zdnet.com/2346-12554_22-171001-7.html]("http://content.zdnet.com/2346-12554_22-171001-7.html")

click "manual"

set mount points for your windows partition and any other partition you wish to mount.  Format your ext3 partition (that's your broken install), and mount it as '/' (set up a /home partition if you wish).  Then just click to the next screen.

Hope this helps.

edit for clarity:
I've done this many times as I dual boot.  I've used both the alternate and live cd.  The alternate cd tells you that it has detected "other os insalls" and prompts you to install grub.  The livecd makes grub just a part of the installation process, and doesn't ask you anything.  I have never had a problem with either process.  If you get stuck with a grub error, usually a fresh install of the linux os, or only grub (using the alternate cd) will fix it.  As long as you make sure you don't format your ntfs (windows) partition, you will not lose your windows install and data.  If grub messes up (and the likelyhood of that is very slight) your install will still be there, you just will have temporary issues accessing it (booting into it).  There are several work arounds if this happens, but, again, I've never had any trouble.

The easiest way to lose your windows install is through user error.  So if you aren't sure about something, just come back and ask.  You don't want to end up formating the wrong partition.  Once you've done it a few times though, it becomes a simple process.  As long as you pay attention, everything should go just fine.

---

### Post by ejohnson442 on 2007-11-14
MikeMLP:

Thanks for your help.  I have a ton-o-stuff going on and have not had time to try out your suggestion as of yet but I will before the weekend is out.  I just wanted to take the time to thank you for you prompt response and to let you know that I hadn't rudely ignored you.

Your help is very much appreciated and I'll let you know how it goes!

---

