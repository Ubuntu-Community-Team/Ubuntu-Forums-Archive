---
title: "Ubuntu 11.04 freezes on start up."
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by linux_dream on 2011-05-12
I just upgrated from ubuntu 10.14 to ubuntu 11.04.  I have downloaded and installed all files and when it asked ro restart I restarted.  However when it loads Ubuntu 11.4, I can see the background, I can see a different desktop bar compared to the one I had, my mouse pointer can move as I want **but all is frozen**.  I can't click on anything, I can't open the terminal, etc.  
Sometimes when I pass my mouse over some part of the screen I see a "hand" as if there was an invisible window opened.  I once pressed the "enter" key and the computer rebooted...
I'm currently under windows xp but I really need Ubuntu since I have files I'm working with for university.  Any help to recover my stuff and making Ubuntu 11.04 work is greatly appreciated.  

P.S.When I reboot I have the option to use old Ubuntu versions.  Some won't even work, while at least 1 version would load but only as in a terminal.  I don't know if this can help.

---

### Post by ibbill on 2011-05-12
any chance you have nvidia card had the same problem removed my nvidia card and reinstalled maybe you can just boot from the cd then and save your stuff.

---

### Post by NormanFLinux on 2011-05-12
Do you have a Broadcom wireless driver? Then it won't work with 11.04 and you'll have to disable it in your BIOS to get the desktop working.

Ubuntu developers created an Ubuntu version that has no Internet connectivity, by design.

Congratulations, Mark Shuttleworth!

---

### Post by linux_dream on 2011-05-12
> **ibbill said:**
> any chance you have nvidia card had the same problem removed my nvidia card and reinstalled maybe you can just boot from the cd then and save your stuff.
Yes I have a NVIDIA card, namely the Geforce 7300 GS.  Do you mean I should open my computer, physically remove my graphic card and then reinstall it?  I'm not going to do that!  I don't even know where it is inside my cpu.
And reboot from what CD?
> **NormanFLinux said:**
> Do you have a Broadcom wireless driver? Then it won't work with 11.04 and you'll have to disable it in your BIOS to get the desktop working.

Ubuntu developers created an Ubuntu version that has no Internet connectivity, by design.

Congratulations, Mark Shuttleworth!
Hmm I don't know about the wireless driver.  How can I check this out?

---

### Post by NormanFLinux on 2011-05-12
To get in your BIOS, press F2 or F10 on your keyboard at startup and navigate to where your wireless LAN option is and disable it.

That way you can determine if the freeze is related to the driver. If it is, you can revert back to an earlier version of Ubuntu that is compatible with the driver.

If the freeze still persists with the wireless LAN turned off, I suspect it may be the video card.

It doesn't hurt to track down whatever is causing the 11.04 desktop to freeze.

---

### Post by linux_dream on 2011-05-12
> **NormanFLinux said:**
> To get in your BIOS, press F2 or F10 on your keyboard at startup and navigate to where your wireless LAN option is and disable it.

That way you can determine if the freeze is related to the driver. If it is, you can revert back to an earlier version of Ubuntu that is compatible with the driver.

If the freeze still persists with the wireless LAN turned off, I suspect it may be the video card.

It doesn't hurt to track down whatever is causing the 11.04 desktop to freeze.
Ok I might try to do this but before I have a question.  When you say I can get into an earlier version of Ubuntu, I already tried and some work.  But I don't have any desktop interface, it's just a terminal.  I could even find the files I need for university (though I don't know how I can open files with a text editor).  But I have no interface other than a terminal.  So this does not freeze.  
I'll try to do the BIOS trick right now.

---

### Post by linux_dream on 2011-05-12
Disabled the LAN option.  Still freezes.  However after having loaded my background and my icons, it loaded another interface with I'm guessing the Ubuntu default background picture and no more icons.  All was frozen.  
Sometimes when I reboot some icons will appear in my taskbar while other won't.  And the time showed won't change (totally frozen).  
But as I said, I can pass my mouse over some part of the background and I see a hand as if there was an invisible window opened.  So I can click on stuff and see my computer is thinking as if I opened a program (red light of my cpu).  
Very strange that my video card fails... I can play the latest video games without any problem.  
How can I get back to Ubuntu 10.14?  Seems like it's the ONLY solution?!

---

### Post by NormanFLinux on 2011-05-12
I don't have an idea how to get back. I'd recommend you download Oz Unity Lucid 10.04 LTS. It should work on your system. It appears 11.04 is just not ready for our devices. The installer doesn't run and even when there is a successful installation there is a desktop freeze upon login.

Maybe Oneiric Ocelot will improve on the situation.

---

### Post by linux_dream on 2011-05-12
> **NormanFLinux said:**
> I don't have an idea how to get back. I'd recommend you download Oz Unity Lucid 10.04 LTS. It should work on your system. It appears 11.04 is just not ready for our devices. The installer doesn't run and even when there is a successful installation there is a desktop freeze upon login.

Maybe Oneiric Ocelot will improve on the situation.
Hmm ok.  Well then R.I.P. Ubuntu 11.04, for my cpu.

I'll stick to windows xp (damn it, that hurts so bad!) until a next version of ubuntu is avaible.  Hopefully it will work with my cpu.  By the way, how to install the latest Ubuntu from a terminal?  What is the command?
So that in 6 months I'll type it in the terminal I have from earlier versions of Ubuntu.

---

### Post by NormanFLinux on 2011-05-12
Its better to use a USB stick. Just download the iso. and burn it to the USB stick with Unetbootin and boot up into live session in USB mode - if your computer has that setting.

Older computers can be configured to run a USB stick as a virtual hard drive with PLOP Linux.

---

### Post by manco on 2011-05-12
Yeah, I'm having the same problem (at least somewhat)

I'm running 11.04 on my laptop. It works great but after I close my laptop lid and leave it running for a while, when I open it back up to resume it's all frozen except for the mouse.

It's quite odd, but if anyone has an idea that might help I'd really appreciate it :)

---

### Post by linux_dream on 2011-05-13
I've asked help in the French forums of Ubuntu.  Now I can enter in Ubuntu but I have graphics problem.

What I've done is to go in the recovery mod (where I have the terminal).  
Then I modify a file this way:
[B]sudo nano  /etc/X11/xorg.conf

[/B]Then it opens a folder.  In the device section where there is the "nvidia" line, go over it and press the "x" key as to delete the letters to transform nvidia into nv.
Then to save the file and quit, type :wq

Now I can load my Ubuntu desktop.  However all my compiz effects are gone, my lovely theme I used with Emerald doesn't work.  I can't watch youtube videos in full screen (I get an error I never got before).  So basically I'm very limited graphically, but at least Ubuntu doesn't freeze.
Oh and I forgot to say, I don't have the new "nice" menu of Ubuntu 11.04.  It's exactly the same menu I had in the previous versions.

So I don't consider my problem solved.  At least not until I can use my graphic card normally.

If I go into System -> Administration -> NVIDIA X server settings, I get the message "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Any help for that?

---

### Post by linux_dream on 2011-05-13
Here are 2 screenshots of my Ubuntu 11.04.
When I use firefox I should have my Delicious bookmarks, and a Windows 7-like window.  So you can see that my compiz and Emerald graphics are totally disabled.  
See my desktop, I don't have Unity it seems.  The manipulation I did to unfreeze Ubuntu seems to have disabled it.  

I'd like to have normal graphics as I used to have with all my previous versions of Ubuntu.  And I'd like to use Unity if it's possible without freeze.  

Thanks for any help.

---

### Post by NormanFLinux on 2011-05-13
Unity may not work with your graphics card. Install Unity 2D.

---

### Post by linux_dream on 2011-05-13
> **NormanFLinux said:**
> Unity may not work with your graphics card. Install Unity 2D.
Sounds a good idea.
Do I download it from Synaptic?
And what about the "nvidia" that I changed into "nv" into the xorg.conf file?

Edit: And what about Unity 3d that is already installed?  I must first erase it, then download the 2d and then put back the "nv" into "nvidia"?

---

### Post by linux_dream on 2011-05-13
I just found something related to my problem, or better said: MY PROBLEM.
[https://bugs.launchpad.net/unity/+bug/728745](https://bugs.launchpad.net/unity/+bug/728745)
I'm not sure to understand well the problem, but what I understand is that my graphic card has problems with the nvidia drivers.  If I could get the drivers from "nouveau" then I could run Unity 3d just fine.

Now my questions are... where can I find these drivers?  How to install them?  
What do I do with the xorg.conf file I modified?


EDIT:  Probably my problem there too (same forum as this one): [http://ubuntuforums.org/showthread.php?t=1742732](http://ubuntuforums.org/showthread.php?t=1742732).
But that didn't work for me...

---

