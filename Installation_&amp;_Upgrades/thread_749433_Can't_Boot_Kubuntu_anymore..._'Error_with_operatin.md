---
title: "Can't Boot Kubuntu anymore... 'Error with operating system'"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by jmusso on 2008-04-08
Hi,

I know there are a lot of threads about this but so far nothing really specifically addresses my issue. So I tried to install a Windows XP partition after I had already installed Kubuntu on my entire internal HD. I loaded up Gparted live, shrunk my ext3 partition by about 20 gigs or so, and formatted the blank space as NTFS. Then I stuck my windows xp cd in, installed it, but couldn't activate it because the activation codes i had were bust. I also could not boot into Kubuntu from here. So my stupid means of getting Kubuntu back, I just put gparted back in and deleted the windows partition, thinking it would automatically boot Kubuntu. I then edited 'Flags' under the ext3 partition and checked off 'boot.' Now I get the message saying 'error loading operating system,' and I don't know what to do. I'm currently running off a Kubuntu 7.04 live disc... any ideas? Thanks, this is really preventing me from getting a lot of stuff done this finals week...

PS - I initially tried to install a Vista partition, but the Vista CD kept saying "windows couldn't find a partition that meets its requirements" or something, even though I had a 20+ gb partition formatted with NTFS... any ideas as for this???

---

### Post by Peter09 on 2008-04-08
Tty downloading the SuperGrub disk from here:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

its is supposed to be very good at repairing broken boot setups.

PC

---

### Post by jmusso on 2008-04-08
right, but i can't burn cd's because i have to run my computer off the live cd. is there anyway i can do it from the kubuntu live cd?

---

### Post by Peter09 on 2008-04-08
Ouch .... 

try running up the CD burner, once its in memory can you remove the live cd?

Most probably not :(

Perhaps someone else can chip in here.

PC

---

### Post by jmusso on 2008-04-09
sorry, what does 'running up the cd burner' mean?

---

### Post by Peter09 on 2008-04-09
Start the program which will do the CD burn.

PC

:)

---

### Post by Peter09 on 2008-04-09
Is there another system on which you can burn this CD?

PC

---

### Post by Partyboi2 on 2008-04-09
> **jmusso said:**
> right, but i can't burn cd's because i have to run my computer off the live cd. is there anyway i can do it from the kubuntu live cd?
super grub can be copied onto floppy or usb as well.
[This]("http://whocares.de/2004/12/28/error-loading-operating-system/") might help with the error message you are getting.

---

### Post by jmusso on 2008-04-10
Hey guys, I solved my own problem. Threw in an old Ubuntu alternate CD (not sure if the Live CD has this option, just had the other one lying around at the time) and chose 'repair system,' then proceeded to install Grub again on /dev/hda. Worked fine, now Grub loads Kubuntu just great. My only question is.... I still have that other 20+ gb partition that I want to put Windows Vista on.. When I try to do this, it says 'windows cannot find a partition that meets its requirements,' or something to that extent. My language isn't precise there, i haven't tried installing it in a few days (just trying to get kubuntu back up). Any ideas would be great... i'm trying to get internet connection sharing from my wireless to my ethernet, and i can't seem to figure it out with kubuntu so my solution is just to reinstall windows and use it for that... lemme know what you guys think. thanks again.

---

### Post by Partyboi2 on 2008-04-10
[Here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") is some info on recovery grub after installing windows. You will probably need to restore grub since you are installing windows as the 2nd operating system.

---

