---
title: "choppy performance after Ubuntu 12.04 reinstallation"
date: 2015-03-23
forum: Installation &amp; Upgrades
---

### Post by grashdur on 2015-03-23
Dear All,

I recently reinstalled my Ubuntu 12.04. (I'd love to use 14.04 instead, but on those later versions my touchpad moves the pointer too fast across the screen [not fixable with the Mouse and Touchpad settings, nor with the Pointing Devices app from the Software Center, nor with xinput].) But since reinstalling, I'm having these problems:

1. When I start moving the pointer with my touchpad, it usually sticks several times when it starts moving. So it's jumpy. Then as I continue moving the pointer, it works fine. Then after I haven't used the touchpad for a few minutes and use it again, it's sticky again at first. [later edit: no, actually this can happen even if it hasn't been a few minutes] (I use a Lenovo ThinkPad touchpad-keyboard.) This happens almost constantly.

2. When I type text, there's often a delay of a second or so before the text appears on screen (in Chrome, LibreOffice, WPS Office, etc.). This unsynchronized situation leads to typos. This tends to happen more after I've been using the computer for a few hours.

3. If I use the arrows on my keyboard to scroll down or up (for example, a webpage on Chrome), the scrolling jumps along, rather than flowing smoothly. This happens all the time.

4. Occasionally, music cuts out intermittently while playing in Clementine or Rhythmbox. Sometimes it just happens once and then not again. Sometimes when music has been playing for a while, the sound starts cutting out so frequently that I give up listening. Rebooting seems to fix this, but obviously that means stopping what I'm doing and restarting the all programs I'm using.

5. Occasionally video can get choppy too, like on YouTube videos. 

So, this is a fresh installation, but everything gets choppy, stopping and starting as it goes. These problems occur regardless of how many things are open at the time. I have a dual-core AMD Athlon processor (II X2 250), and 8 GB of RAM. It's a 64-bit computer, a ZaReason system built for Linux. I recently doubled my RAM, so before reinstallation, performance was wonderful. As far as I know, the only difference between my current system and what was running before is that all the updates ran at once this time (right after installing) instead of little by little over time. 

Normally I expect a reinstallation to improve performance, not make it worse. How can I recover the perfomance I had before with Ubuntu 12.04?

---

### Post by ajgreeny on 2015-03-23
Could this be your graphic card?  Is it just the integrated chip or do you have a dedicated card for graphics?

---

### Post by grashdur on 2015-03-23
The list of specifications on the invoice does not say anything about graphics. So I'm not sure. Should I check this out on my computer, or will I need to get additional specifications from the company that sold it to me? 

By the way, I just tested out a few other things: 

When I log into the Guest account, the problem remains. When I boot into the Live CD for 12.04, the problem is still there but less severe. When I boot into 14.04 (I left it installed in a separate root partition), the problem is there too -- though I still have the problem that the pointer is out of control in that version. 

This is so strange -- if I'm having this problem everywhere now, then why wasn't it happening in my previous installations of 12.04?

---

### Post by grashdur on 2015-03-23
Okay, I just tried something else: I unplugged my touchpad-keyboard from the keyboard switcher (for switching between two computers), and plugged it directly into the computer's own USB port. No difference. 

and now I just unplugged my usual Lenovo Thinkpad touchpad-keyboard, and plugged in a GearHead touchpad-keyboard. The jumpy pointer movements, and the delayed text entry are still happening. Actually they're even worse. I tried booting into Ubuntu 14.04 with this other keyboard, and I have the same jumpy movements, although not quite as severe. 

This seems to be happening regardless of the keyboard, and regardless of the Ubuntu version. It's an Ubuntu problem. Why is this not affecting anyone else? And why was it not happening to me on my previous installation on this computer?

---

### Post by grashdur on 2015-03-23
I installed the package fglrx-amdccle, the Catalyst AMD control center. When I try opening it, I get this error message: 

[B]Initialization error

There was a problem initializing Catalyst Control Center Linux edition. I could be caused by the following:

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for your AMD hardware, or configure using aticonfig.[/B]

I tried reinstalling my graphics driver, the package called fglrx, but no change in performance nor in the error message. I could not find any aticonfig, though I have all the software sources enabled. 

I don't know whether my problems are being caused by the graphics driver, but I did get this error message.

---

### Post by grashdur on 2015-03-24
I solved the problem, but by creating a bigger one:

As mentioned above, I installed the package fglrx-amdccle, the Catalyst AMD control center. For my previous installation of 12.04 back in 2013, this package allowed me to fix my monitors to work perfectly. Now after rebooting, I have my two monitors stuck in mirror mode, with the larger one in low resolution and the image stretched out horizontally. I got an error message about the display size. (The pointer and text entry work perfectly now, with no lags or choppiness.) When I tried to go into monitor settings and change them to normal settings, I got a similar error message. I can't repeat it here, because when I tried it again just now, my monitors went black until I rebooted. 

So it seems that the cause of my problems was the monitor drivers. (Right?) New preferred drivers are now installed automatically, but they cause choppy performance. When I tried installing the old display setup that worked for me in the past, it didn't work and it messed up my "preferred" monitor driver. 

How can I fix this? I hope I don't have to reinstall the system. But if I do, how do I get the right drivers to install?

---

### Post by Vladlenin5000 on 2015-03-24
The 'right' drivers to install are often those offered by Ubuntu (tested). System settings > Software & Updates. In the rightmost tab you'll find the recommended drivers, both open source and proprietary.

---

### Post by grashdur on 2015-03-24
I've been thinking that's probably the case: My original reason for reinstalling was that my Unity desktop kept disappearing, several times a day. That may have had something to do with the older monitor driver that I was using. 

But in System Settings, I don't see anything called Software & Updates. (Ubuntu 12.04 with the default Unity desktop) Is there supposed to be something there that can reinstall the "right" driver? I do see the icon for Additional Drivers, but that doesn't do anything for me.

Scott

---

### Post by Vladlenin5000 on 2015-03-24
Sorry, the information I provided before applies to newer versions. In 12.04 you can search for "additional drivers" (exactly what you just mentioned), the rest is the same. It should offer additional proprietary drivers whenever available. Those should be preferred. Of course, if you already try to install from other sources, with other methods, then probably you have a broken system already. Just keep that in mind next time you do a fresh installation.

---

### Post by grashdur on 2015-03-24
I wonder if there's any chance of reinstalling the "right" driver now. The Additional Drivers thing comes up empty. 

Or do I need to just reinstall now?  And if I do reinstall, is there any chance that a different distribution would help? I haven't ever tried Kubuntu. Or will the drivers all just be exactly the same there?

---

### Post by Vladlenin5000 on 2015-03-24
Unfortunately I'm not an expert on AMD graphics. Except for a 2014 low-cost HP notebook with AMD APU (equivalent to R2 graphics) where I installed the recommended drivers and everything works fine, my last experience with AMD graphics was in the time they were still called ATI (circa 2005).

Nevertheless, I have a question: Is there some reason why you kept the 12.04? The machine is new enough to perhaps work better with newer releases. 14.04 is also LTS.

---

### Post by grashdur on 2015-03-24
I love 14.04, but there is one critical problem: It causes my touchpad to send the pointer around too quickly. It was not fixable with the Mouse and Touchpad settings, nor with the Pointing Devices app from the Software Center, nor with xinput. Right now I'm logged into 14.04 again (I left both installed with separate root partitions) to see if there might be a different driver for my touchpad-keyboard. Apparently there are no other drivers available for me. 

Right now I'm downloading Kubuntu, to try out its installation disk. I could also try Gnome and Mint. If nothing works, I'll just reinstall 12.04 again and try to live with the jumpiness.

---

### Post by grashdur on 2015-03-25
In summary: It seems to have been a problem with the driver for my 25" HP LP2475w monitor: The newer, "preferred" driver causes jumpiness and delayed text entry, instead of making the Unity interface go invisible at random moments.

I did end up having to reinstall, because by installing amdccle, I apparently was deleting the newer driver, and amdccle won't run on my system any more anyway.

---

