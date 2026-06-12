---
title: "Mint 13, 14 and 15 constantly crashing"
date: 2013-11-04
forum: MINT
---

### Post by MrAutumn on 2013-11-04
Hello! 
I initially installed Mint 13 Mate 64bit on a my netbook. I was told that Mint was a reliable lightweight OS that would run better on low end PCs than other distros. After installation things run smoothly for about an hour when it suddenly froze. I was not even running anything weird. I went for a walk and when I came back my pc was just stuck. Couldn't move the mouse and the keyboard wouldn't respond. After the battery died 4h later I plugged it in and rebooted the system. This time it froze before I could even log in.  

After some fruitless googling (is than even a word?) I found a post on the mint forums from one of the devs that said that this was caused by a "bug" in the MATE interface. "Ok, no problem" I thought "Ill just go with the Cinnamon shell". After reinstalling Mint 13, this time with Cinnamon, the exact same thing happened. 2h after the second installation Mint freezes. Some more internet searching and apparently the bug was not restricted to MATE. The error is somewhere deep in Mint 13's graphic interface something code that means Im totally screwed.

 "Fine, Ill just run Mint 14. Such a huge bug, it must by fixed in following versions". Well, guess what? Its not. I tried Mint 14/15 with Mate and Cinnamon, both 32 and 64 bit versions. That's 8 distros, meaning 8 separate installations. Every version froze or crashed after installation. The gold goes to Mint 14 Cinnamon 64bit, that run for almost a day before crashing and burning.

Am I the only one having these issues? Not according to the mint forums. 
What's the deal Mint? Why are you so unstable! Freaking Windows Me was more reliable!!!

Now Im running Ubuntu 13.10 64bit with Gnome shell. It works fine... Thanks for asking.

---

### Post by BBQdave on 2013-11-04
> **MrAutumn said:**
> ...initially installed Mint 13 Mate 64bit on a my netbook. I was told that Mint was a reliable lightweight OS that would run better on low end PCs than other distros.

Depending on the age (capabilities) of your hardware, Linux Mint Maya 13LTS ([COLOR=#ff0000]**32-bit**[/COLOR]) would probably be a good fit on a **netbook** :)

And I would stick with MATE on older hardware.

---

### Post by MrAutumn on 2013-11-04
> **BBQdave said:**
> Depending on the age (capabilities) of your hardware, Linux Mint Maya 13LTS ([COLOR=#ff0000]**32-bit**[/COLOR]) would probably be a good fit on a **netbook** :)

And I would stick with MATE on older hardware.

I have an ACER Apire ONE 722 model. It has 1.3Ghz AMD Dual-Core processor, 4GBB Ram and 500 GB HDD. It should run Mint Olivia without problems...

---

### Post by Stinger on 2013-11-04
Could be an issue related to mint not dealing correct with your graphics chip, do you know the make and model ?

Else try 'lspci' in a terminal and look for VGA, here is mine:
> 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV730 XT [Radeon HD 4670]

Try this in a terminal to see if the driver is loaded correctly 'glxinfo | grep OpenGL' here is mine:
> OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV730
OpenGL version string: 2.1 Mesa 8.0.4
OpenGL shading language version string: 1.20
OpenGL extensions:

---

### Post by r-senior on 2013-11-04
Have you tried running a memory test to confirm that is not the issue?

---

### Post by buzzingrobot on 2013-11-04
First, Mint is *not* a light-weight distribution. Mint is based on Ubuntu.  Light-weight distributions don't solve  the kind of problems you are seeing,  They just run faster and use less memory.

Second, if the same problem has occured on each of the several installations you have attempted, then, logically, that problem must stem from something that's common to all of those installations.

Did you install the available updates as soon as you rebooted after the first install.  Even Mint 15 is several months old and has hundreds of updates and bug fixes awaiting you.

Many people, including myself, found that the default kernel in Mint 15, and in Ubuntu 13,04 on which it is based, caused trouble.  After installing Mint 15, open a terminal, enter and run this command: "uname -a".  If the kernel version is listed as 3.8.19, then enter and run this command to upgrade the kernel: "sudo apt-get install dist-upgrade".  Be sure to reboot to ensure the new kernel is used.

Your troubles also might be video related.  Please use lspci mentioned earlier to determine the video card in the machine.

Mint, as well as Ubuntu, does not install proprietary video drivers by default.  It is possible the the open source video driver that is installed is not working correctly on your machine.  Mint offers ways to install proprietary video drivers.  In older releases it might be labeled "Additional Drivers".  In newer releases, it might be labeled "Driver Manager".

---

### Post by neu5eeCh on 2013-11-04
This problem can be caused by a wide variety of issues that have nothing to do with Mint.

For instance, my older Ubuntu installs were regularly freezing because of _major_ Firefox memory leaks. _**Major**_**.** For many weeks I thought the problem was Ubuntu. It was only after installing Memory Restart that the real culprit was revealed. Google chrome also feasts on memory. Another time, the same symptoms were caused by hard drive failure. That was in Windows XP. It took me several weeks before I stopped blaming Windows.

Based on your description, I'm inclined to think the issue isn't software related, but hardware. I'm willing to bet your hardware is failing and that Mint, more so than other distros, is sensitive to that failure. Obviously, it may be time to start diagnosing. Install a different distro. Check your hard drive. Do memory checks. Etc...

---

### Post by orb9220 on 2013-11-04
Yep your general system specs are no guarantees of smooth running. 
Everything from video chipset,wifi to trackpad to sound chip in a laptop can create these kind of situations.

Might get more help listing out your video chipset used as a majority of the time that seems to be the issue.
[linux ACER Aspire ONE 722 on google.]("https://www.google.com/search?q=linux+ACER+Aspire+ONE+722&biw=1107&bih=874&noj=1&tbas=0")
.

---

### Post by Stinger on 2013-11-05
@orb9220
google is your friend ;)
**A conflict between the ethernet and the wireless adapter causes some system freeze from time to time. **

[UBUNTU 12.04 - INSTALLATION ON ACER ASPIRE ONE 722 (AO722)]("http://bernaerts.dyndns.org/linux/74-ubuntu/251-ubuntu-precise-acer-ao722")
> 1. AVOID WIFI ADAPTER FREEZE
Under Ubuntu Precise 12.04, the Aspire One 722 wifi adapter is fully supported.

It doesn't have the very annoying bug where the system freezes instantly when activating the wireless adapter, but you can still encounter some system freeze from time to time. To get rid of these freezes, you have to follow the same procedure as for the previous wifi activation freeze.

This bug comes from a conflict between the ethernet and the wireless adapter and can be corrected by seting-up a specific boot order, where the network boot is used first. With this setup, the ethernet adapter will be configured in a way that there won't be any conflict with the wifi adpater at the time of wireless network connexion.

And again here:
[Linux on Acer Aspire One 722-0369]("http://cortman.wordpress.com/2012/04/13/linux-on-acer-aspire-one-722-0369/")
> Fixes and things to know about the 2012 Acer Aspire One 722

Netbook will freeze right after boot-up. This is due to the wireless driver, in ways that I myself don&#8217;t understand, but it can be fixed by changing the boot order in the BIOS. Set Network boot first. This will always return a boot-up error about cables being disconnected, but that&#8217;s the price to pay.
HDMI output needs to be manually configured. It works perfectly with Ubuntu 11.0 and Fedora 16, but still needs to be configured with xrandr.
Graphics resolution will be fixed by 3.x+ kernel. Any kernel version < 3.0 will need ATI proprietary graphics drivers, which have decidedly inferior performance to the open source version in my experience.

---

### Post by MrAutumn on 2013-11-05
I have Ubuntu 13.10 64bit installed right now and its running quiet smoothly. (Better than with 12.04 64bit)... I know that&#8217;s no guarantee but I really doubt its a specs issue. As for updates, I installed them as soon as I got the system running (in some cases the pc froze before they could even finish downloading). I also tried reinstalling and updating the graphics drivers (again, if the os could hold that long). 

> **Stinger said:**
> @orb9220
google is your friend [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]
**A conflict between the ethernet and the wireless adapter causes some system freeze from time to time. **

[UBUNTU 12.04 - INSTALLATION ON ACER ASPIRE ONE 722 (AO722)]("http://bernaerts.dyndns.org/linux/74-ubuntu/251-ubuntu-precise-acer-ao722")


And again here:
[Linux on Acer Aspire One 722-0369]("http://cortman.wordpress.com/2012/04/13/linux-on-acer-aspire-one-722-0369/")


Could be. In Mint 14 I eventually found out that the pc would crash "prematurely" if I unplug (or disable) the LAN connection or the power input. But, at this point I was so frustrated I didn&#8217;t even bother looking it up on Google. I just went back to Ubuntu 12..04, beaten and humiliated (and kinda hungry).

---

### Post by Stinger on 2013-11-06
I'm confused of what OS you're running ?
The OP says "Now I'm running Ubuntu 13.10 64bit with Gnome shell" but your latest post says "I have Ubuntu 13.10 64bit installed right now" at the beginning, but at the end it says "I just went back to Ubuntu 12.04" ??

Anyway, if you still wanna try on Mint ( or any other Ubuntu version ) , I would recommend "setting-up a specific boot order, where the network boot is used first" as it says [here in "1. Avoid Wifi adapter Freeze"]("http://bernaerts.dyndns.org/linux/74-ubuntu/251-ubuntu-precise-acer-ao722") to avoid your random freezes.

---

### Post by BBQdave on 2013-11-07
> **MrAutumn said:**
> I have an ACER Apire ONE 722 model. It has 1.3Ghz AMD Dual-Core processor, 4GBB Ram and 500 GB HDD.

OK, yeah that hardware should handle most modern 64-bit Linux distros.

For what it's worth, I have Ubuntu Unity 12.04LTS 64-bit running smoothly on a Lenovo Thinkpad T400.
Intel® Core™2 Duo CPU T9400 @ 2.53GHz × 2 with 2 gigs of RAM and a 7200 RPM HD.

If you get the drivers sorted, your hardware should perform well with Linux 64-bit distros.

---

### Post by wsc1028 on 2013-11-22
I used 32-bit versions of Linux Mint 15 and 13, lightweight XFCE desktop, as well as Puppee Linux on old and small Acer Aspire One netbook, all of them worked well without proprietary drivers. 64-bit versions are much more convenient in use, though.

---

