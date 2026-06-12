---
title: "Live CD X Server Prob?"
date: 2006-04-18
forum: Installation &amp; Upgrades
---

### Post by denny2k2 on 2006-04-18
Hi there,

I'm new to Linux and Ubuntu although i have always been intruiged, so my mate told me about the LIVE CD, which basically allows you to try it out without installing etc.

So anyway, apparently it should have been a pretty straight forward proceedure hehe. 

Somehow i must've mucked up.

I have read the other X Server problem threads, but i'm not sure if these apply to the Live CD?

I basically get the:

 "Failed to start X Server (your graphical interface). It is likely it is not set up correctly. Would you like to view the x server output to diagnose the problem?"

I choose YES and it shows mainly jargon, symbols and version numbers of X Windows Server and such like.

I click ok and it comes up with

"X Server disabled. Restart GDM when configured."

I read in the others that i should type:

"sudo dpkg-reconfigure xserver-xorg"

and choose VESA on the video driver section?

then type:

"sudo /etc/init.d/gdm restart"

I am just wondering if this is the same for the LIVE CD?

Also, where abouts would i type the "sudo dpkg..." line? Just at the "boot" screen?

Thank you for your time.

- Denny

---

### Post by Sutekh on 2006-04-18
I've never had to try this on a LiveCD.  What happens after you are shown the error screens, do you end up at a command prompt?

If you do then use those commands from there.

---

### Post by denny2k2 on 2006-04-18
Hi there, thanks for your reply.

I have finally sorted it.

to answer your question however. No, it would just go do a black screen with some of list which was had just previously loaded (sorry, i don't know all the terminology, i'll try and explain, when ubuntu finally starts to load (with the graphic and loader bar) checking all the diffrent things and either saying "OK" or "failed" beside it, well it had a few of the those). I couldn't type or anything.

I tried these commands at the boot screen. It wouldn't recognise the "sudo" command and said something about not finding that "kernel".

Anyway, i found the solution within the "live-expert" settings.

As i read through this forum, i noticed it seemed to be that people with ATI video cards, had the same problems. Also that i should change the video card setting to "vesa" which is the "general" card driver, i think.

The problem was i didn't actually know how to change it from ATI to vesa.

So i finally tried booting up in "live expert" mode.

instead of pressing "enter" and entering the default boot up, i typed "live-expert" and pressed enter.

This allowed me to check the settings. When it came to the video hardware settings, i chose NOT to auto detect them, and then chose "vesa" from the big list.

It went all very smoothly from there!

So i think it was purely down to ATI problems.

I quite liked the feel of Linux. I wouldn't mind learning it in more depth!

Might partition my HD and give it a shot...i dunno though, as i have never done anything as adventerous like this before hehe.

thank you anyway for your reply.

Cheers,

- Denny :mrgreen:

---

### Post by Sutekh on 2006-04-18
Hey good stuff!

Yeah the vesa driver is the general driver, and people do seem to have a lot of problems with ATI cards.  NVIDIA ones seem to be better supported straight from an installation.

A LiveCD is a good way to introduce yourself to Linux/Ubuntu, so I'd keep messing around in there until you are comfortable.

If you do decide to go ahead with an installation, I would recommend you have a read of this link, you might find it helpful.

Great guide for Dual-Booting (Check the Ubuntu + NTFS/Ubuntu + FAT32 guides)

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone/)

---

### Post by Sutekh on 2006-04-19
This is another very useful guide I only just re-discovered.

[Ubuntu 5.10 & MS WinXP DualBoot How To - Mehdi Hassanpour](http://www.hezardastan.org/breezy_xp_dualboot/en/)

I particularly like this guide because it has a couple of different methods and of course the obligatory screenshots.

---

