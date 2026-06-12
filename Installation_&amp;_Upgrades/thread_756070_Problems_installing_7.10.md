---
title: "Problems installing 7.10"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by Eric Weir on 2008-04-15
I have been using Ubuntu almost exclusively -- actually, Kubuntu -- for about eight months now. A techie friend installed it on a 10 GB hard drive on an old machine that I wasn't using. Needless to say, with only 10 GB the system eventually got excruciatingly slow.

This past weekend I cannibalized two 40 GB hard drives from my Windows desktop and tried to do a fresh install of Kubuntu by myself. Initially, the install hung up very early in the process with a black screen with a couple lines at the top with something about "Busy-Box" in them. Underneath were some characters that looked like a command in parentheses -- "(initramfs)". I couldn't tell that anything was happening, except that the lights on my modem and router were flashing like crazy, so I assumed it was downloading updates to the system.

However, after four hours of waiting for the "downloading" to stop I took my techie friend's suggestion and did a Ctrl-Alt-Del, after which the installation process started up again and seemed to go through to completion. But when I tried booting without the CD the system wanted to boot from the CD; it wouldn't move on to the HD. I restarted the system and checked the BIOS settings, which showed the two CDs as first and second boot drives, and the two hard drives as "not installed." 

My techie friend suggested that I change the jumper settings on the second hard drive and then try installing again. Again, the process hung up at the black screen with "Busy-Box" and "(initramfs)" showing. I tried Ctrl-Alt-Del again several times, hoping that the installation process would eventually start and go through to completion, but it never did.

Any ideas what's going on and what I need to do to get the installation to go through to completion?

Thanks much,

---

### Post by gn2 on 2008-04-15
Try the F6 additional boot parameter only-ubiquity with the Live CD if you have 384mb RAM or more, otherwise use the Alternate CD would be my suggestion.

---

### Post by Eric Weir on 2008-04-16
> **gn2 said:**
> Try the F6 additional boot parameter only-ubiquity with the Live CD if you have 384mb RAM or more, otherwise use the Alternate CD would be my suggestion.
Thanks. Just put the CD in the machine, and will give it a try.

Regards,

---

### Post by Eric Weir on 2008-04-16
> **gn2 said:**
> Try the F6 additional boot parameter only-ubiquity with the Live CD if you have 384mb RAM or more, otherwise use the Alternate CD would be my suggestion.
Well, when the live CD booted I didn't find that parameter. While I was at it, I went ahead and tried all the others, except OEM install, and got the same result with all of them. 

What is the Alternative CD? How do I get it?

Thanks,

---

### Post by gn2 on 2008-04-16
When you boot with the Live CD and a menu is presented, with Start or Install Ubuntu at the top, press F6 then type: only-ubiquity
Then hit Enter and the installer should run without a Live session.

If you look along thebottom of the splash screen there are different F# options listed.
F6 is to enter additional boot parameters, of which there are a few.

---

### Post by Eric Weir on 2008-04-16
[quote=gn2;4728162]When you boot with the Live CD and a menu is presented, with Start or Install Ubuntu at the top, press F6 then type: only-ubiquity
Then hit Enter and the installer should run without a Live session.

I realized that was what you meant after I posted my response. However, I didn't enter the command correctly as you fave it. The memory test is running right now. [Previously ran the CD test. It's OK.] When it's done I'll try this.

Thanks again,

---

### Post by gn2 on 2008-04-16
You can get the Alternate CD here: [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

Instructions: [https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6](https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6)

---

### Post by Eric Weir on 2008-04-16
[quote=gn2;4728162]When you boot with the Live CD and a menu is presented, with Start or Install Ubuntu at the top, press F6 then type: only-ubiquity
Then hit Enter and the installer should run without a Live session.

This bypasses GUI assisted install altogether?

In any case, it hung up at this line: "[64.522185] Kernel panic - not synching: VFS: unable to mount root fs on unknown block(104,1)"

---

### Post by gn2 on 2008-04-16
> **Eric Weir said:**
> [quote=gn2;4728162]When you boot with the Live CD and a menu is presented, with Start or Install Ubuntu at the top, press F6 then type: only-ubiquity
Then hit Enter and the installer should run without a Live session.

This bypasses GUI assisted install altogether?

It runs the same installer as would have run if you clicked the desktop "Install" icon.

> **Eric Weir said:**
> 
In any case, it hung up at this line: "[64.522185] Kernel panic - not synching: VFS: unable to mount root fs on unknown block(104,1)"

Time to have a try with the Alternate CD.

---

### Post by Eric Weir on 2008-04-16
> **gn2 said:**
> It runs the same installer as would have run if you clicked the desktop "Install" icon.
Never got to it. It just bombed out into Busy-Box.
> Time to have a try with the Alternate CD.
I'll have to see if I can get somebody to get one for me. My only computer at this point is a laptop without a CD running XP. 

Probably just get me into another kettle of fish, but could the Alternate CD installation be run from the Alternate CD loaded onto a flash drive? If so, what size flash drive would be required? 2GB? 4GB?

Strange that I did get the process to go through the first time -- though I did end up with the hard drives showing up as "not installed."

---

