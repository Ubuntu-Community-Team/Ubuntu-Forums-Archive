---
title: "Installed Audio Repositories for Ubuntu Studio, Now Grub is weird"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by employeeno5 on 2008-02-24
So I've been running Ubuntu 7.10 since October as a dual boot with Windows. This has made me a happy happy boy.
For a long time I've wanted to get my hands on Ubuntu Studio but only the audio recording software. I was happy to learn that you could do this by simply installing the packages ubuntustudio-audio and ubuntustudio-audioplugins. So I did this and everything appeared to go well. After installing them and restarting the computer I found that I now I had two new linux boot options:

Ubuntu 7.10, kernel 2.6.22-14-rt
Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)

Below it was my normal selection of options typified by:
Ubuntu 7.10, kernel 2.6.22-14-generic

Now, if I start the computer in "rt" mode it appears to have retained my user settings but it does not correctly recognize my video card and my wireless internet does not work either. In fact general rendering of windows seems to be slow and a difficult. I did not explore for further issues.
When I start in "generic" mode everything runs as it normally has and I would expect it to. All of the software I wanted from the audio repositories is installed and appears to work correctly.

I went to my /boot/grub/menu.lst and commented out the new boot options so that they're not showing up and booting automatically if I'm not quick on my feet.

So, I'm wondering; is it strange that this happened? Is it a problem? Should I leave well enough alone having successfully "removed" these from my Grub menu or is there a way for me to reverse whatever had caused them to show up in the first place?
Any insight into what happened here would be great as I love learning about Linux in general.

Thanks!

---

### Post by dstew on 2008-02-24
Ubuntu Studio installs the [Real Time Kernel]("https://wiki.ubuntu.com/RealTime/Gutsy"), I suppose to support editing and playback more perfectly. To use it, you probably have to install the drivers that work with that kernel. Boot into it, and look in the Restricted Drivers Management tool. I think there are drivers for your video and maybe for your wireless card there.

---

### Post by employeeno5 on 2008-02-25
Thanks for the info on the real time kernel.
I'm guessing that it is essential for allot of this software to run correctly, as after further experimentation I'm having a very hard time getting any of the recording programs to interact correctly with my inputs. There's allot of crashing going on and error messages regarding "timers".
I might look another time to see about getting this stuff working correctly on my laptop, (or I may just  do a full install of Ubuntu Studio on different computer) but for now I guess I'm hoping there's a sane way to undo what I did.
Uninstalling those packages did not remove the applications or the real time kernel. Most of those applications won't uninstall through clean normal means (package manager) either as they seem to all be relying on each other and various plug ins but won't group each other together for complete removal.

Is there a reasonably safe way to remove the real time kernel that anyone knows of? 
I may just back up some personal info and do a clean install of Ubuntu anyways, or maybe wait it out until Hardy's release and do it then. 
I know the real time kernel may be harmless sitting in there out of the way, but I don't like leaving extra fat and loose ends on my computer if I can help it. Also, again, I'm always up for a new lesson in Linux.

---

### Post by dstew on 2008-02-25
> Is there a reasonably safe way to remove the real time kernel that anyone knows of? Remove it using Synaptic. That will remove the kernel images and delete the grub menu items also.

---

### Post by employeeno5 on 2008-02-25
> Remove it using Synaptic. That will remove the kernel images and delete the grub menu items also.

Well, that's easy enough isn't? I feel a bit foolish for having not even looked for it in there. 
Thanks again for all the help and info!

---

### Post by MetalMusicAddict on 2008-02-26
It appears you did not install the restricted modules for the -rt kernel. **sudo apt-get install linux-rt**

---

