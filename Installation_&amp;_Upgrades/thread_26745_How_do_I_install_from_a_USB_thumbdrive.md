---
title: "How do I install from a USB thumbdrive?"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by dubside on 2005-04-13
Since I didn't get any answers to [http://ubuntuforums.org/showthread.php?t=26315](http://ubuntuforums.org/showthread.php?t=26315) , I'm thinking about borrowing a USB thumbdrive to install Hoary.

Sorry if this seems like a completely basic question, but what is involved in doing this? Will the installer boot if I just drop the 5.04 i386 .iso onto the USB drive? Or do I need to create partitions or anything like that? Again, I'm a complete beginner at this, so any help would be appreciated...

---

### Post by heimo on 2005-04-14
I appreciate your creatity. I'm not sure if the method you're suggesting would work, I think it is designed just to run Knoppix distributions, but not to actually install Knoppix or any other distribution. (I don't say it couldn't work, I just can't figure how.)

What I'd try to do... is figure out why the CD drive on your computer doesn't want to cooperate, or I'd borrow or buy external CD or DVD (rw) drive. But you get more geek points for getting around the problem with your knowledge (Knoppix boot / fixing the problem with your current setup). :)

---

### Post by Dr Gonzo on 2005-04-14
Absolutely it will work.

On my computer, I see this file (on the Ubuntu install cd): ```
file:///media/cdrom1/doc/install/manual/en/ch02s02.html#id2526441
```  There is also an index.html file in that directory.  I didn't think to check the install media for docs.  There's an entire install guide right there, including for thumb drives.

What is up with this distro?  The developers are fixing things that have long bothered me about Linux.  And Debian in particular.  I had used Libranet for a while, but it was pretty obvious that it was just being done by 2 guys.  Ubuntu is different.  Their development process is great.  The documentation and community is no different.

---

### Post by dubside on 2005-04-14
Aha - The install guide looks very helpful. Thanks for the tip :)

But. When I get to section 4.3, "Preparing Files for USB Memory Stick Booting," they start by saying: "For preparing the USB stick you will need a system where GNU/Linux is already running..."

If all I've got right now is XP, am I out of luck?

---

### Post by Dr Gonzo on 2005-04-14
Well, it's looking like it'd be a lot easier for you to use a cd to install it.  Unless the memory stick already had it on there.

You've got to be able to install syslinux -- a boot loader -- onto the thumb drive.  To do this, it appears that you need Linux.

---

