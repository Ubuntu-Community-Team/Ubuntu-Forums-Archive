---
title: "Ubuntu 10.04 works from USB, dies on HD, **kills normal boot from USB**"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by pling on 2010-09-15
The hardware is a brand new HP/Compaq Mini Note Netbookj (Atom CPU, Ion LE, 1GB RAM, 160GB HD, XP installed, no CD - hardware that I know worked Ubuntu 9.) I've given Ubuntu a 2GB-ish swap (whatever the default setting was) and 118GB of Ext2 under /

1. I tried 10.4 Netbook first. Downloaded, checked MD5, ran live - was fine except for needing drivers for wireless and Ion, found plug-in wireless that I was going to use to download drivers. So I rebooted - still fine. Switched off, did stuff, came back later - and Ubuntu never succeeded in rebooting again, not even in Recovery mode.

2. So I googled, concluded I had a freak bad install, and installed Netbook over itself again by opting for manual partition during install. I reformed the prior Netbook partition as Ext2 and mounted as / and left Swap alone. The result was exactly the same as 1, except - and this is really evil - ****now the machine would no longer boot from USB pen unless I went into the grub shell during boot, then inserted the pen, ls-ed the pen, then exit-ed**. **I'm obviously concerned that this might stop working too, given the tendency of stuff to work once or twice and then fail.

3. So I tried this method to install desktop 10.4.1. Again I checked the checksum. I updated before closing. I got one reboot out of the machine, but it was a very awkward one - I went through a recovery menu and had to log in on the cmd line and use xstart

At this point I can only say WTF??? I'd like to be able to get Ubuntu running - even an older version - but I'll settle for just giving the hard drive space back to XP and wiping Ubuntu off my system. In fact, I suspect that getting rid of all traces of my previous installs is the first thing to do before trying another version of Ubuntu - or even Fedora or whatever.

So, questions -

- Can anyone see where I went wrong?

- Does anyone have any idea what is happening, so that a machine can run ok Live, boot once, and then hangs eternally during future boots?

- Does anyone have any idea why I could no longer boot from USB except via grub (I could no longer get at the boot menu to select USB - if I pressed ESC to bring that menu up the machine would just hang.)

- Is this [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927) the best way to remove Ubuntu and is that what I should do next? 

- Is there anything else I should try to install Ubuntu 10.4 or should I give up?

---

### Post by pling on 2010-09-16
From the absence of replies after a whole day, I'm guessing that other people are as puzzled as I am.

What bothers me is that the whole machine was closed to being bricked - if this had happened and I hadn't chosen to keep some drive space for XP, then it might have taken a hard drive change to make the machine usable. Ok - I can get the machine to work via messing around with grub at the moment, but that's not something most potential users would try, and given previous history there's nothing to say that this will continue to work. Scary.

Otoh, I'm damn will not going back to Windows!

---

### Post by pling on 2010-09-24
Bump - anyone?

---

### Post by pling on 2011-06-30
Ok - so Ubuntu can brick a machine during install and nobody has any ideas at all what to do??? I'm a little alarmed here.

---

