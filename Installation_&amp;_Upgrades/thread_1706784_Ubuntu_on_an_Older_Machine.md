---
title: "Ubuntu on an Older Machine?"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by jage on 2011-03-14
I'm trying puppy on an older machine: P3/1G/256MB
[http://www.puppylinux.org/main/index...%20Release.htm]("http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm")

While it's downloading, I previously tried Ubuntu (minimum of 512MB ram for min install/ 1G for full) before checking the requirements.  I've been waiting to resurrect this machine with Ubuntu, and I was pretty dismayed when I got around to looking at the requirements.

When there isn't enough RAM (if I'm even getting to that point) it just hangs.  I've done memory tests and after playing with Ubuntu have had some issues even booting the computer which has lead to motherboard testing- haven't found anything wrong.

Then I tried lubuntu, and I could get to a desktop of sorts, whether or not I used the GUI it just winds up hanging.  I don't get to any install point really.

So I'm on to puppy.  I'm hesitant to buy RAM until I can determine the system is actually working, but in the end I'd like to have full Ubuntu... it has hardware issues on my main system and I do a lot of graphic work that isn't supported, so this machine would be my ubuntu machine.

Anyway, two things:
1. I can run XP on the old box.  I don't want to, but it just works with the hardware in the current state.  Ubuntu is supposed to be the one that "just works" but...
2. it only hangs- is there no idiot message for someone like me who things "old computer + ubuntu == great things" where when putting the disc in the first thing it says would be: Hey, we checked your RAM and this isn't going to work. (Or Hey, with only 512 you're going to be in for a rough ride, proceed?)

Maybe my impressions are wrong, but I gave up on even dual booting because of all the laptop problems and now this is just seeming like a hot mess.  I keep thinking, I could just get XP and my computer wouldn't be in pieces all over my desk, or even go back to ME from the OEM disc and it would *function* for what I need it for.

Any advice?  Will I be OK for ubuntu if I just up the RAM to 1G?

---

### Post by mikewhatever on 2011-03-14
You could try Xubuntu or Lubuntu, the mid and light weight derivatives of Ubuntu. Personally, I think 512Mb of RAM would be enough to run Ubuntu on an old computer. You won't be able to open a hundred web pages or run VirtualBox, but it should work well for browsing, email, chat, photos, etc.
XP does indeed run with 256MB, but whether it's usable or not is highly debatable.

---

### Post by mörgæs on 2011-03-14
It surprises me that Lubuntu does not work. Can you install straight from the CD without running a live session?

Installing only the needed packages in *buntu will also help:
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

Here are some other options, if it still does not work:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by jage on 2011-03-14
> **mörgæs said:**
> It surprises me that Lubuntu does not work. Can you install straight from the CD without running a live session?


Boot from CD
Install Lubuntu from menu
Desktop Loads
When I double click the "Install Lubuntu" icon in the upper left, the menu bar goes away and the mouse still moves but everything else seems dead- can't move the icon, deselect it or anything.

Also tried to just click and drag the install icon, and things froze except the menu bar didn't disappear.

I've scanned the HD for errors and run memory tests.

Puppy runs fine for the record.

Is there another way to install?  If the GUI installer won't run, that's a bad sign right?

---

### Post by mörgæs on 2011-03-15
> **jage said:**
> 
Is there another way to install? 

yes, you could try post 176 in this thread:
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

Which screen card do you have?

---

### Post by jage on 2011-03-15
Interesting because with the ubuntu or lubuntu I get something like this on boot: **getpwuid_r(): failed due to unknown user id (0)**

Which is in your #176 thread.  I'll try that minimal install with apt-get for lubuntu when I have time.

Video card is e-Gforce FX 5500, 256MB haven't searched on it yet since there didn't seem to be obvious problems along those lines.  Hey, just realized my v/card has the same RAM as the computer... :confused: derp!

I believe my next computer will be built around ubuntu friendly hardware!

---

### Post by XsheepX on 2011-03-15
I have an old machine with 256mb that ran XP. It was a nightmare, A NIGHTMARE. 
Installed Crunchbang on it, and it works like a pro. Also tried Ubuntu on it, and it works pretty decently.

---

### Post by mörgæs on 2011-03-15
I have an Nvidia Geforce FX 5200, and it is very Ubuntu-friendly. It is to early to scrap the old one.

---

### Post by jage on 2011-03-19
Here is what I've done so far, at least what has worked so far:

From post #176 as referenced earlier, I downloaded the minimal CD.
Installed twice to get a prompt.
Installed lubuntu with apt-get and clean.

Still locks up every time I boot... stops while the GUI is loading on a white screen with cursor.

Lubuntu run from the CD stops the GUI whenever anything is clicked.

Puppy locked up whenever I tried to install a browser.

The one thing that has worked is going into the Lubuntu CD menu and using **F6 Password** to change boot settings turning everything off:
x acpi=off
x noapic
x nolapic
x edd=on
x nomraid
x nomodeset
  Password

and then "Try Lubuntu wihtout installing"

So I am going to see if I can turn these off and "Boot from First Hard Disk" and/or narrow down which one of them is actually causing the problem.

In the mean time, I have no idea what they are.  What are they (in layman's terms) and more importantly how do I set them if I'm not using the CD to boot?  I am hoping that I can determine which of them is causing the problem, and then set it so I can boot from HD without whatever that is.

---

### Post by jage on 2011-03-19
It does seem to be "nomodeset", with only that item checked I can boot and operate fine from CD in the GUI.

I gather it has something to do with the VGA mode, but I'm out of my depth at this point.  I don't know how to alter the GRUB for a hard drive boot or where I should do that from... or if I can then load an NVIDIA driver (have a .run file ???)

So yeah, I'm confused at this point but there is hope finally.

NEW THREAD ABOUT THIS:
[http://ubuntuforums.org/showthread.php?p=10586686#post10586686](http://ubuntuforums.org/showthread.php?p=10586686#post10586686)

Marking this solved at this point.

---

