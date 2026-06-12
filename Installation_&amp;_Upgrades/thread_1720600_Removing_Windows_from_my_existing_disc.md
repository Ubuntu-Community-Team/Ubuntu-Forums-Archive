---
title: "Removing Windows from my existing disc"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by bradleysmith on 2011-04-03
Hi,

I've recently applied for University and am happy to say I got an unconditional offer in Software Development :D as this is the case, and that I expect I'll be using mostly Windows software on my course, I decided to buy a hard drive from a friend at work, larger than the one I have now, and plan to install Windows 7 on it for the sake of my course and various other things (games etc.)

I prefer Ubuntu myself, and I've been using it long enough to feel comfortable migrating to Ubuntu altogether and ditching the windows partition I have now (I currently dual boot). Reasons being that I'm not much of a fan of dual booting as I think it can complicate things when its not entirely necessary and that there is also a Linux-based module on my course and between an installation going wrong on my personal hard drive or my university hard drive, I'd clearly go along with losing my music and pictures rather than losing all of my coursework :S

So my question is this: is it completely safe to blow away the windows partitions I have now on this hard drive? I made a LiveCD of my install through remastersys but I really would not like to go through setting up my themes, preferences, additional compiz plugins etc.

Thanks for your help.

---

### Post by Dutch70 on 2011-04-03
All of your settings are stored in your .config folder. I believe that you can save that somewhere safe and just put it back if you reinstall. That will get your settings back, but not your apps, although when you put the app back, your settings will still be there.

Also, check the following link for more important info. Look under #8 where it says 
> [COLOR="Red"]Well, I get your point, but I have installed so many applications on my system that a clean install is basically out of the question.[/COLOR]
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1580857[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")

---

### Post by bradleysmith on 2011-04-03
Just had the decision made for me :S my Ubuntu installation just randomly bricked. For some reason, I lose write permissions for the disc and a few permissions have been put onto folders which means that I can't use the installation anymore. Currently backing up everything I need right now through my LiveCD.

How would one go about restoring the .config folder? Is it a simple matter of dropping it in the home directory and then restarting?

---

### Post by Dutch70 on 2011-04-03
> How would one go about restoring the .config folder? Is it a simple matter of dropping it in the home directory and then restarting?

I believe it is. You may want to change the name of it until you get rid of your other .config folder. Having 2 of them may cause some strange and unusual behavior. :P

Maybe just remove the dot in front of it.

---

