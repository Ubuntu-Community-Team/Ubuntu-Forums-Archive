---
title: "Boot Ubuntu 8.10 (Intrepid Ibex) on EEE PC 701 from SDHC?"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by Sirkey on 2008-11-16
Hello!

This is my first post here, as I'm sure you can see, so I may have posted in the wrong part of the forum, or I'm asking a really stupid question...or it's just been answered before, in which case, sorry! =P

I currently own a Dell Inspiron 1501 with Windows XP Media Centre Edition installed on it, which I received for Christmas in 2006. I also own an Asus EEE PC 701 (4GB). The EEE is exactly how it was when I got it, except I put a 2GB RAM chip in, stead of the default 512MB it's sold with. Xandros only uses 1GB because there's a cap on it, and I'm told I need to edit the kernel in order to get the full 2GB of the chip working, but I'm too scared to do anything like that! I also own two Kingston 4GB SDHC cards (Class 4...I think...). I use both for music and video on my EEE, as I can just leave them in there. What I want to do is install Ubuntu 8.10 (Intrepid Ibex) onto one of the 4GB SDHC cards, put it in my EEE Pc, and boot Ubuntu from there.

Now you know what system's I'm running on, and what I want to do.

I've done a bit of research. I've found a video showing that Ubuntu 7.10 works fine on the EEE when booted from a 4GB SDHC, which can be found [here]("http://uk.youtube.com/watch?v=rAuFcm2gWzU"). I'm therefore assuming that Intrepid would also work. I've also looked around here, and the EEEUser forums, and found a few threads talking about problems when installing Intrepid on the EEE 701 (these can be found [here]("http://ubuntuforums.org/showthread.php?t=978015&highlight=Asus+EEE+PC+701+Intrepid+Howto"), [here]("http://ubuntuforums.org/showthread.php?t=924426&highlight=Intrepid+on+EEE+Pc+701"), and [here]("http://forum.eeeuser.com/viewtopic.php?id=50732")), however I *think* none of those should effect me, as I'm not installing Ubuntu to the EEE directly. I also found a post that seemed to indicate that what I want to do is possible, and worked fine. This thread can be found [here]("http://forum.eeeuser.com/viewtopic.php?id=51455"), and the post is the 16th one down, which I shall quote below.

[quote="creepingmee"]I use 8.10 on my 701 installed to sdhc no problem whatsoever.  It helps to run the cpu at full speed though.  I run at 1000mhz most of the time, at 900 though it's still quite usable.  I haven't ever installed adamm's kernel, but if you google asus_eee v0.3 I'm sure you can find information on how to set up the kernel module for fsb/fan control.  I have done this with the generic kernel, and rather like it.[/quote]

In theory, my searches say that everything will be fine, and it'll all work like a dream, without any of the problems found when installing Intrepid on the EEE.

Something I think I should mention: I thought the only SDHC card reader I owned was my EEE, as my Dell Inspiron 1501 only had an SD card port, but I have since discovered that my Genius G-Shot DV5131 digital camera also has a SDHC port in it, so I am able to put the SDHC card into the camera, connect the camera to my Dell (Windows) laptop via USB, and see all the files on the SDHC, effectively turning my camera into a card-reader. Will I be able to install Ubuntu 8.10 onto the SDHC using this method? (I'll put that in the questions list.)

Now here's my questions:

[LIST=1]
[*]Are there any minor problems I'd find during installation that I haven't mentioned?
[*]Are there any major problems I may face during installation on the SDHC, or when running Intrepid on the EEE?
[*]Is there a chance of my EEE getting eaten alive, and all my work on my EEE being destroyed?
[*]Would it be worth partitioning my 4GB SDHC, giving 2.5/3GB over to Ubuntu, and using the other 1.5/1GB for general storage (either for Ubuntu or my EEE)?
[*]Will I be able to install Intrepid on my SDHC when using my digital camera as a card-reader?
[*]If I make it all work, will I be able to access what is on the internal drive of my EEE from Ubuntu, and will I be able to save to it without causing a mass meltdown?
[*]Where will all the files I create in Ubuntu be saved? (On the SDHC, or the internal solid-state drive?)
[*]Will Ubuntu use the full 2GB of RAM, or stick to the 1GB like Xandros did?
[*]Will I need to do anything else except install Intrepid on the SDHC and boot it on my EEE?
[*]**How do I install Intrepid on the SDHC?** (I really need that one answering! =D)
[*]Is there anything else you think I need to know? (Assuming I know only what has been mentioned in this post, and what is clearly stated in any replies.)
[/LIST]
I think that's all of my questions, I'll no doubt be back if it isn't.

I am aware that I need to press ESC when the EEE splash screen comes up in order to change which drive the EEE boots from.

I am pretty much a Linux nub (Only ever really used Xandros, and not that technically) so any technical terminology will be wasted on me (i.e. Don't talk techy unless you've explained what it means).

I'd dearly love nothing to happen to the internal disk of the EEE, so that I can remove the SDHC, and run Xandros like I've never been near it with Ubuntu. I greatly value my EEE, so I don't want it being destroyed! =P

Any help, in any shape or form will do, even if it's a link to a thread asking the very same thing hidden away in the depths of the interwho.
Again, if this has already been covered, or if it's in the wrong place, sorry!! :KS

~ Sirk

---

### Post by Sirkey on 2008-11-16
Don't tell me my post was too long to read? :P

Or has this been answered somewhere else? I still can't really find what I want...

---

### Post by Steve1961 on 2008-11-16
Why don't you just create a bootable intrepid usb stick (unebootin or the intrepid cd), boot from that and see how it works for you.  It works fine on my 1000H but can't comment on how well it would work on a 701. 

As for installation, well the easiest way with a 701 is from the usb stick.  If your installing to an sdhc the only real danger is selecting your internal drive by mistake.  That said, it can be reverted to the original xandros system in about 5 minutes with the recovery cd so not a huge issue.  But always back up your files before hand just in case.

In general though, the eeeuser forums are where you will get most advice about the questions you've asked.

---

### Post by Sirkey on 2008-11-16
Alright mate, Thank you! =P

I'll head over to the EEEUser forums, and make myself an account.

Are you saying I should install Intrepid to a 2GB USB stick (using PenDriveLinux?) then run the EEE off that, and somehow install Ubuntu (for the second time) onto my SDHC? How would I go about installing Ubuntu again...if it's already installed on my USB stick?

Thanks again.

~ Sirk

---

### Post by Steve1961 on 2008-11-16
> **Sirkey said:**
> Alright mate, Thank you! =P

I'll head over to the EEEUser forums, and make myself an account.

Are you saying I should install Intrepid to a 2GB USB stick (using PenDriveLinux?) then run the EEE off that, and somehow install Ubuntu (for the second time) onto my SDHC? How would I go about installing Ubuntu again...if it's already installed on my USB stick?

Thanks again.

~ Sirk

The Intrepid live cd has an option in the menu to create a usb stick.  just plug in a usb stick and follow along.  This basically creates a live cd on your usb stick.  You then boot your eeepc with that and then double click the install icon once it launches.  An installed system is not the same as a bootable live image - one is generic and the other is specific to your system, so installing to an sdhc is just like installing to a hard drive, and retains all the settings and packages that you alter/install.

---

### Post by Sirkey on 2008-11-16
Right, so I can put the LiveCD onto a USB stick, as it were...

Excellent, I'll try that as soon as possible!! I'm assuming I'll need a 2GB USB stick for that? Will I be able to do that from within Virtual Box?

Again, thank you, you've been a great help!!

~ Sirk

---

### Post by Steve1961 on 2008-11-16
> **Sirkey said:**
> Right, so I can put the LiveCD onto a USB stick, as it were...

Excellent, I'll try that as soon as possible!! I'm assuming I'll need a 2GB USB stick for that? Will I be able to do that from within Virtual Box?

Again, thank you, you've been a great help!!

~ Sirk

1gb should be more than enough.  Not sure why you need virtualbox, just boot your main pc with a live cd and create the usb stick from there.  That said, if your booting a live cd iso from virtualbox you should be able to do it as long as you have usb support

---

### Post by Sirkey on 2008-11-16
I'm only using virtual box so I don't have to use up a CD! =P

I'll try to do it via Virtual Box.

Again, thank you! I'll click the `Thanks` button as you've been so useful! xD

~ Sirk

---

### Post by Steve1961 on 2008-11-16
Cheers, and good luck :)

---

